<a name='assembly'></a>
# Docs

## Contents

- [CloudPurchaseClient](#T-CME-CloudPurchase-CloudPurchaseClient 'CME.CloudPurchase.CloudPurchaseClient')
  - [#ctor()](#M-CME-CloudPurchase-CloudPurchaseClient-#ctor 'CME.CloudPurchase.CloudPurchaseClient.#ctor')
  - [Dispose()](#M-CME-CloudPurchase-CloudPurchaseClient-Dispose 'CME.CloudPurchase.CloudPurchaseClient.Dispose')
  - [Validate(request,executionLogger)](#M-CME-CloudPurchase-CloudPurchaseClient-Validate-CME-CloudPurchase-ValidationRequest,System-Action{System-String}- 'CME.CloudPurchase.CloudPurchaseClient.Validate(CME.CloudPurchase.ValidationRequest,System.Action{System.String})')
- [PurchaseType](#T-CME-CloudPurchase-PurchaseType 'CME.CloudPurchase.PurchaseType')
  - [Paid](#F-CME-CloudPurchase-PurchaseType-Paid 'CME.CloudPurchase.PurchaseType.Paid')
  - [Promo](#F-CME-CloudPurchase-PurchaseType-Promo 'CME.CloudPurchase.PurchaseType.Promo')
  - [Test](#F-CME-CloudPurchase-PurchaseType-Test 'CME.CloudPurchase.PurchaseType.Test')
  - [Unknown](#F-CME-CloudPurchase-PurchaseType-Unknown 'CME.CloudPurchase.PurchaseType.Unknown')
- [Store](#T-CME-CloudPurchase-Store 'CME.CloudPurchase.Store')
  - [Apple](#F-CME-CloudPurchase-Store-Apple 'CME.CloudPurchase.Store.Apple')
  - [Fake](#F-CME-CloudPurchase-Store-Fake 'CME.CloudPurchase.Store.Fake')
  - [GooglePlay](#F-CME-CloudPurchase-Store-GooglePlay 'CME.CloudPurchase.Store.GooglePlay')
- [ValidationRequest](#T-CME-CloudPurchase-ValidationRequest 'CME.CloudPurchase.ValidationRequest')
  - [Currency](#F-CME-CloudPurchase-ValidationRequest-Currency 'CME.CloudPurchase.ValidationRequest.Currency')
  - [PackageId](#F-CME-CloudPurchase-ValidationRequest-PackageId 'CME.CloudPurchase.ValidationRequest.PackageId')
  - [Price](#F-CME-CloudPurchase-ValidationRequest-Price 'CME.CloudPurchase.ValidationRequest.Price')
  - [PriceUsdCents](#F-CME-CloudPurchase-ValidationRequest-PriceUsdCents 'CME.CloudPurchase.ValidationRequest.PriceUsdCents')
  - [ProductId](#F-CME-CloudPurchase-ValidationRequest-ProductId 'CME.CloudPurchase.ValidationRequest.ProductId')
  - [ReceiptData](#F-CME-CloudPurchase-ValidationRequest-ReceiptData 'CME.CloudPurchase.ValidationRequest.ReceiptData')
  - [Store](#F-CME-CloudPurchase-ValidationRequest-Store 'CME.CloudPurchase.ValidationRequest.Store')
  - [UserId](#F-CME-CloudPurchase-ValidationRequest-UserId 'CME.CloudPurchase.ValidationRequest.UserId')
- [ValidationResponse](#T-CME-CloudPurchase-ValidationResponse 'CME.CloudPurchase.ValidationResponse')
  - [ErrorCode](#F-CME-CloudPurchase-ValidationResponse-ErrorCode 'CME.CloudPurchase.ValidationResponse.ErrorCode')
  - [ErrorMessage](#F-CME-CloudPurchase-ValidationResponse-ErrorMessage 'CME.CloudPurchase.ValidationResponse.ErrorMessage')
  - [PurchaseType](#F-CME-CloudPurchase-ValidationResponse-PurchaseType 'CME.CloudPurchase.ValidationResponse.PurchaseType')
  - [Valid](#F-CME-CloudPurchase-ValidationResponse-Valid 'CME.CloudPurchase.ValidationResponse.Valid')

<a name='T-CME-CloudPurchase-CloudPurchaseClient'></a>
## CloudPurchaseClient `type`

##### Namespace

CME.CloudPurchase

##### Summary

Client for validating purchases.

<a name='M-CME-CloudPurchase-CloudPurchaseClient-#ctor'></a>
### #ctor() `constructor`

##### Summary

Default constructor.

##### Parameters

This constructor has no parameters.

<a name='M-CME-CloudPurchase-CloudPurchaseClient-Dispose'></a>
### Dispose() `method`

##### Summary

IDisposable implementation.

##### Parameters

This method has no parameters.

<a name='M-CME-CloudPurchase-CloudPurchaseClient-Validate-CME-CloudPurchase-ValidationRequest,System-Action{System-String}-'></a>
### Validate(request,executionLogger) `method`

##### Summary

Validate in-app purchase.

##### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| request | [CME.CloudPurchase.ValidationRequest](#T-CME-CloudPurchase-ValidationRequest 'CME.CloudPurchase.ValidationRequest') | Purchase details to validate |
| executionLogger | [System.Action{System.String}](http://msdn.microsoft.com/query/dev14.query?appId=Dev14IDEF1&l=EN-US&k=k:System.Action 'System.Action{System.String}') | Delegate for logging validation result |

<a name='T-CME-CloudPurchase-PurchaseType'></a>
## PurchaseType `type`

##### Namespace

CME.CloudPurchase

##### Summary

Enum of types of purchase.

<a name='F-CME-CloudPurchase-PurchaseType-Paid'></a>
### Paid `constants`

##### Summary



<a name='F-CME-CloudPurchase-PurchaseType-Promo'></a>
### Promo `constants`

##### Summary



<a name='F-CME-CloudPurchase-PurchaseType-Test'></a>
### Test `constants`

##### Summary



<a name='F-CME-CloudPurchase-PurchaseType-Unknown'></a>
### Unknown `constants`

##### Summary



<a name='T-CME-CloudPurchase-Store'></a>
## Store `type`

##### Namespace

CME.CloudPurchase

##### Summary

Enum of app stores

<a name='F-CME-CloudPurchase-Store-Apple'></a>
### Apple `constants`

##### Summary

AppStore

<a name='F-CME-CloudPurchase-Store-Fake'></a>
### Fake `constants`

##### Summary

For test purpose

<a name='F-CME-CloudPurchase-Store-GooglePlay'></a>
### GooglePlay `constants`

##### Summary

Google Play Store

<a name='T-CME-CloudPurchase-ValidationRequest'></a>
## ValidationRequest `type`

##### Namespace

CME.CloudPurchase

##### Summary

Purchase info to validate

<a name='F-CME-CloudPurchase-ValidationRequest-Currency'></a>
### Currency `constants`

##### Summary



<a name='F-CME-CloudPurchase-ValidationRequest-PackageId'></a>
### PackageId `constants`

##### Summary



<a name='F-CME-CloudPurchase-ValidationRequest-Price'></a>
### Price `constants`

##### Summary



<a name='F-CME-CloudPurchase-ValidationRequest-PriceUsdCents'></a>
### PriceUsdCents `constants`

##### Summary



<a name='F-CME-CloudPurchase-ValidationRequest-ProductId'></a>
### ProductId `constants`

##### Summary



<a name='F-CME-CloudPurchase-ValidationRequest-ReceiptData'></a>
### ReceiptData `constants`

##### Summary



<a name='F-CME-CloudPurchase-ValidationRequest-Store'></a>
### Store `constants`

##### Summary

Store where purchase was made.

##### See Also

- [CME.CloudPurchase.Store](#T-CME-CloudPurchase-Store 'CME.CloudPurchase.Store')

<a name='F-CME-CloudPurchase-ValidationRequest-UserId'></a>
### UserId `constants`

##### Summary

User's sensitive data.

<a name='T-CME-CloudPurchase-ValidationResponse'></a>
## ValidationResponse `type`

##### Namespace

CME.CloudPurchase

##### Summary

Details of validation result

<a name='F-CME-CloudPurchase-ValidationResponse-ErrorCode'></a>
### ErrorCode `constants`

##### Summary



<a name='F-CME-CloudPurchase-ValidationResponse-ErrorMessage'></a>
### ErrorMessage `constants`

##### Summary



<a name='F-CME-CloudPurchase-ValidationResponse-PurchaseType'></a>
### PurchaseType `constants`

##### Summary

Type of validated purchase.

##### See Also

- [CME.CloudPurchase.PurchaseType](#T-CME-CloudPurchase-PurchaseType 'CME.CloudPurchase.PurchaseType')

<a name='F-CME-CloudPurchase-ValidationResponse-Valid'></a>
### Valid `constants`

##### Summary

Is purchase valid or not.
