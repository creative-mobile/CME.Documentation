# Making Validation Requests

При установке нашего пакета в вашем Unity проекте появится файл `Assets/CME/Sample/CloudPurchaseSample.cs` в котором есть примеры использования `CloudPurchaseClient`.

## <a id="client"></a> Using CloudPurchaseClient
Пример использования `CloudPurchaseClient` для валидации платежей:

```
public async Task Validate()
{
    // Create client for validation
    using (var cloudPurchaseClient = new CloudPurchaseClient())
    {
        // Create validation request directly
        var request = new ValidationRequest
        {
            Store = Store.GooglePlay,
            PackageId = "com.my.package.name",
            ProductId = "my.product1",
            ReceiptData = "Receipt data from store",
            // Set UserId to investigate logs and solve possible user problems
            UserId = "Optional User ID in game",
            // Set PriceUsdCents for analytics and revenue diagrams in dashboard
            Price = 9.99,
            Currency = "USD",
            PriceUsdCents = 999
        };

        var response = await cloudPurchaseClient.Validate(request);

        if (response.Valid)
        {
            // All Good

            if (response.PurchaseType != PurchaseType.Paid)
            {
                // This is not real pay, Tester etc
            }
        }
        else
        {
            // See details in response.ErrorCode and response.ErrorMessage
        }
    }
}
```

## <a id="unity-iap"></a> Within the Unity IAP IStoreListener

Для того, чтобы использовать `CloudPurchaseClient` вместе с `Unity IAP IStoreListener` сначала нужно найти файл `Assets/CME/Sample/Extensions.cs` в Unity проекте и раскомментировать его. Это нужно для того, чтобы использовать соответствующие extension методы.

Пример использования `CloudPurchaseClient` c `Unity IAP IStoreListener` для валидации платежей:

```
public class PurchaseProcessor : MonoBehaviour, IStoreListener
{
    private IStoreController? _storeController;
    
    public void OnInitialized(IStoreController controller, IExtensionProvider extensions)
    {
        _storeController = controller;
    }
    
    public void OnInitializeFailed(InitializationFailureReason error)
    {
        // Process error
    }

    public PurchaseProcessingResult ProcessPurchase(PurchaseEventArgs purchaseEvent)
    {
        // Validate purchase without awaiting method
        ValidatePurchase(purchaseEvent.purchasedProduct);
        
        // We are still waiting for purchase validation
        return PurchaseProcessingResult.Pending;
    }

    public void OnPurchaseFailed(Product product, PurchaseFailureReason failureReason)
    {
        // Process error
    }

    private async Task ValidatePurchase(Product purchasedProduct)
    {
        try
        {
            using (var iapValidator = new CloudPurchaseClient())
            {
                var request = CreateValidationRequest(purchasedProduct);
                var response = await iapValidator.Validate(request);

                if (response.Valid)
                {
                    // All good
                    
                    if (response.PurchaseType != PurchaseType.Paid)
                    {
                        // This is not real pay, Tester etc
                    }
                }
                else
                {
                    // See details in response.ErrorCode and response.ErrorMessage
                }
            }
        }
        finally
        {
            // Confirm
            _storeController?.ConfirmPendingPurchase(purchasedProduct);
        }
    }

    private ValidationRequest CreateValidationRequest(Product purchasedProduct)
    {
#if UNITY_ANDROID
        // Create validator
        var validator = new CrossPlatformValidator(
            GooglePlayTangle.Data(),
            AppleTangle.Data(),
            UnityEngine.Application.identifier);

        var result = validator.Validate(purchasedProduct.receipt);
        
        foreach (var purchaseReceipt in result)
        {
            if (purchaseReceipt is GooglePlayReceipt googlePlayReceipt)
            {
                // Use extension method to create ValidationRequest from GooglePlayReceipt
                return googlePlayReceipt.AsValidationRequest(); 
            }
        }
#elif UNITY_IOS
        // Create validator
        var validator = new CrossPlatformValidator(
            GooglePlayTangle.Data(),
            AppleTangle.Data(),
            UnityEngine.Application.identifier);

        var result = validator.Validate(purchasedProduct.receipt);

        // Use extension method to create ValidationRequest from Product
        return purchasedProduct.AsAppleValidationRequest();
#endif
        throw new Exception("Can't create validation request!");
    }
}
```