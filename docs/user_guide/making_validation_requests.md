# Making Validation Requests

При установке **CME CloudPurchase** в вашем Unity проекте появится файл `Assets/CME/Sample/CloudPurchaseSample.cs` в котором есть примеры использования `CloudPurchaseClient`.

Процесс проверки платежей с помощью **CME CloudPurchase** довольно прост. По-сути, все сводится к созданию инстанса [`CloudPurchaseClient`](../api_reference/API.md#T-CME-CloudPurchase-CloudPurchaseClient) и использованию его метода [`Validate`](../api_reference/API.md#M-CME-CloudPurchase-CloudPurchaseClient-Validate-CME-CloudPurchase-ValidationRequest,System-Action{System-String}-). Примеры использования можно видеть ниже.

## <a id="client"></a> Using CloudPurchaseClient
Пример использования `CloudPurchaseClient` для валидации платежей:

``` c#
public async Task Validate()
{
    using (var cloudPurchaseClient = new CloudPurchaseClient()) // (1)
    {
        var request = new ValidationRequest // (2)
        {
            Store = Store.GooglePlay,
            PackageId = "com.my.package.name",
            ProductId = "my.product1",
            ReceiptData = "Receipt data from store",
            UserId = "Optional User ID in game", // (3)
            Price = 9.99,
            Currency = "USD",
            PriceUsdCents = 999 // (4)
        };

        var response = await cloudPurchaseClient.Validate(request);

        if (response.Valid) // (5)
        {
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

1. Create `CloudPurchaseClient` instance for validation
2. Create validation request directly
3. Set `UserId` to investigate logs and solve possible user problems. **Warning:** this is personal data, see details [here](usage_statistics.md#sensetive-data).
4. Set `PriceUsdCents` for analytics and revenue diagrams in [dashboard](usage_statistics.md).
5. It means that purchase is good.


## <a id="unity-iap"></a> Within the Unity IAP IStoreListener

Для того, чтобы использовать `CloudPurchaseClient` вместе с **Unity IAP** сначала найдите файл `Assets/CME/Sample/Extensions.cs` в вашем проекте и раскомментировать его. Это нужно для того, чтобы использовать соответствующие extension методы.

Подробнее про работу с **Unity IAP** можно найти в [официальной документации](https://docs.unity3d.com/Manual/UnityIAP.html).

Пример использования `CloudPurchaseClient` c **Unity IAP** для валидации платежей:

``` c#
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
        ValidatePurchase(purchaseEvent.purchasedProduct); // (6)
        
        return PurchaseProcessingResult.Pending; // (1)
    }

    public void OnPurchaseFailed(Product product, PurchaseFailureReason failureReason)
    {
        // Process error
    }

    private async void ValidatePurchase(Product purchasedProduct)
    {
        try
        {
            using (var iapValidator = new CloudPurchaseClient())
            {
                var request = CreateValidationRequest(purchasedProduct);
                var response = await iapValidator.Validate(request);

                if (response.Valid) // (2)
                {
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
            _storeController?.ConfirmPendingPurchase(purchasedProduct); // (3)
        }
    }

    private ValidationRequest CreateValidationRequest(Product purchasedProduct)
    {
#if UNITY_ANDROID
        var validator = new CrossPlatformValidator(
            GooglePlayTangle.Data(),
            AppleTangle.Data(),
            UnityEngine.Application.identifier);

        var result = validator.Validate(purchasedProduct.receipt);
        
        foreach (var purchaseReceipt in result)
        {
            if (purchaseReceipt is GooglePlayReceipt googlePlayReceipt)
            {
                return googlePlayReceipt.AsValidationRequest(); // (4)
            }
        }
        
        throw new Exception("Can't create validation request!");
#elif UNITY_IOS
        var validator = new CrossPlatformValidator(
            GooglePlayTangle.Data(),
            AppleTangle.Data(),
            UnityEngine.Application.identifier);

        var result = validator.Validate(purchasedProduct.receipt);

        return purchasedProduct.AsAppleValidationRequest(); // (5)
#endif
    }
}
```

1. Still waiting for the purchase validation. Confirmation will be after validation.
2. It means that purchase is good.
3. Finally confirm the purchase.
4. Use extension method to create ValidationRequest from GooglePlayReceipt.
5. Use extension method to create ValidationRequest from Product.
6. Don't need to await this call because we set purchase state to `Pending` below.
