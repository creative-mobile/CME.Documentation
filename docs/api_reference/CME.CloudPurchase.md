<a name='assembly'></a>
# Namespace CME.CloudPurchase

## Top-level entities

- [CloudPurchaseClient](#T-CME-CloudPurchase-CloudPurchaseClient 'CME.CloudPurchase.CloudPurchaseClient')

- [PurchaseType](#T-CME-CloudPurchase-PurchaseType 'CME.CloudPurchase.PurchaseType')

- [Store](#T-CME-CloudPurchase-Store 'CME.CloudPurchase.Store')

- [ValidationRequest](#T-CME-CloudPurchase-ValidationRequest 'CME.CloudPurchase.ValidationRequest')

- [ValidationResponse](#T-CME-CloudPurchase-ValidationResponse 'CME.CloudPurchase.ValidationResponse')


<a name='T-CME-CloudPurchase-CloudPurchaseClient'></a>
## CloudPurchaseClient `type`

### Implements 

[IDisposable](https://docs.microsoft.com/en-gb/dotnet/api/system.idisposable?view=net-6.0){target=_blank}

### Overview

Client for validating purchases.

### Methods overview
| Name                                            | Description                                                                |
|-------------------------------------------------|----------------------------------------------------------------------------|
| #ctor() `constructor`                           | Default constructor                                                        |
| Dispose()                                       | IDisposable implementation                                                 |
| [Validate(request, executionLogger)](#Validate) | Initiates payment validation request to the cloud side of CME Cloud Purchase|

### Methods

<a name='Validate'></a>
#### Validate(request, executionLogger) `method`

##### Parameters

| Name            | Type                                                                                                                                      | Description                            |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| request         | [CME.CloudPurchase.ValidationRequest](#T-CME-CloudPurchase-ValidationRequest 'CME.CloudPurchase.ValidationRequest')                       | Purchase details to validate           |
| executionLogger | [System.Action{System.String}](https://docs.microsoft.com/en-gb/dotnet/api/system.action-1?view=net-6.0 'System.Action{System.String}'){target=_blank} | Delegate for logging validation result |

##### Returns

Task<[ValidationResponse](#ValidationResponse) \>

<a name='T-CME-CloudPurchase-PurchaseType'></a>
## PurchaseType `enum`

#### Summary

Enum of types of purchase.

#### Values

| Name    | Value | Description            |
|---------|-------|------------------------|
| Unknown | 0     | Unknown type           |
| Paid    | 1     | Paid through the store |
| Test    | 2     | Test payment           |
| Promo   | 3     | Promo code             |


<a name='T-CME-CloudPurchase-Store'></a>
## Store `enum`

#### Summary

Enum of app stores

#### Values

| Name       | Description       |
|------------|-------------------|
| Apple      | AppStore          |
| Fake       | For test purpose  |
| GooglePlay | Google Play Store |


## ValidationRequest `type`

#### Overview

Purchase info to validate

#### Fields
| Name          | Type                                | Description                                       |
|---------------|-------------------------------------|---------------------------------------------------|
| Store         | [Store](#T-CME-CloudPurchase-Store) | Store where the purchase was made                 |
| PackageId     | string                              | App Id                                            |
| ProductId     | string                              | Product ID                                         |
| ReceiptData   | string                              | Data with payment processing results from the store|
| UserId        | string                              | User ID                                           |
| Price         | string                              | Price in local currency                           |
| Currency      | string                              | Local currency                                    |
| PriceUsdCents | int                                 | Price in USD cents                                |

<a name='ValidationResponse'></a>
## ValidationResponse `type`

#### Overview

Details of validation result from CME Cloud Purchase cloud side

#### Fields 
| Name         | Type                                              | Description                               |
|--------------|---------------------------------------------------|-------------------------------------------|
| Valid        | bool                                              | Payment validity flag                     |
| PurchaseType | [PurchaseType](#T-CME-CloudPurchase-PurchaseType) | Payment type                              |
| ErrorCode    | string                                            | Error code from the validating platform   |
| ErrorMessage | string                                            | Error description from the validating platform |

