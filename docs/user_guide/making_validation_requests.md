# Making Validation Requests

When installing **CME CloudPurchase**, you will find the file 'Assets/CME/Sample/CloudPurchaseSample.cs' in your Unity project containing examples of how to use 'CloudPurchaseClient'.

The payment verification process with **CME CloudPurchase** is pretty straightforward. Basically it is all about creating an instance [`CloudPurchaseClient`](../api_reference/CME.CloudPurchase.md#T-CME-CloudPurchase-CloudPurchaseClient) and using its [`Validate`](../api_reference/CME.CloudPurchase.md#Validate) method . See the examples of usage below.
method . See the examples of usage below.

## <a id="client"></a> Using CloudPurchaseClient
Example of using 'CloudPurchaseClient' to validate payments:

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

1. Create 'CloudPurchaseClient' instance for validation.
2. Create validation request directly.
3. Set 'UserId' to study the logs and solve potential user problems. **Warning:** This is personal data, for more information see [here](usage_statistics.md#sensetive-data).
4. Set `PriceUsdCents` for analytics and revenue diagrams in the [dashboard](usage_statistics.md).
5. It means that the purchase has been completed successfully.


## <a id="unity-iap"></a> Unity IAP IStoreListener

If you want to use 'CloudPurchaseClient' along with **Unity IAP**, first find the file 'Assets/CME/Sample/Extensions.cs' in your project and uncomment it. It is required to use the appropriate extension methods.

For more details on working with **Unity IAP**, see the [official userguide](https://docs.unity3d.com/Manual/UnityIAP.html){target=_blank}.

Here is an example of using 'CloudPurchaseClient' with **Unity IAP** to validate payments:

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

1. Still waiting for the purchase validation. Confirmation will come after validation.
2. It means that the purchase has been completed successfully.
3. Finally confirm the purchase.
4. Use extension method to create ValidationRequest from GooglePlayReceipt.
5. Use extension method to create ValidationRequest from Product.
6. No need to wait for this request to be completed because we bring back the 'Pending' status of the purchase below.
