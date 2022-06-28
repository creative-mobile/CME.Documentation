<a name='assembly'></a>
# Namespace CME.CloudPurchase

## Top level entities

- [CloudPurchaseClient](#T-CME-CloudPurchase-CloudPurchaseClient 'CME.CloudPurchase.CloudPurchaseClient')

- [PurchaseType](#T-CME-CloudPurchase-PurchaseType 'CME.CloudPurchase.PurchaseType')

- [Store](#T-CME-CloudPurchase-Store 'CME.CloudPurchase.Store')

- [ValidationRequest](#T-CME-CloudPurchase-ValidationRequest 'CME.CloudPurchase.ValidationRequest')

- [ValidationResponse](#T-CME-CloudPurchase-ValidationResponse 'CME.CloudPurchase.ValidationResponse')


<a name='T-CME-CloudPurchase-CloudPurchaseClient'></a>
## CloudPurchaseClient `type`

### Summary

Client for validating purchases.

### Methods summary
| Name                                            | Description                                                                |
|-------------------------------------------------|----------------------------------------------------------------------------|
| #ctor() `constructor`                           | Default constructor                                                        |
| Dispose()                                       | IDisposable implementation                                                 |
| [Validate(request, executionLogger)](#Validate) | Инициирует запрос на валидацию платежа в облачную часть CME Cloud Purchase |

### Methods

<a name='Validate'></a>
#### Validate(request, executionLogger) `method`

##### Parameters

| Name            | Type                                                                                                                                                  | Description                            |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| request         | [CME.CloudPurchase.ValidationRequest](#T-CME-CloudPurchase-ValidationRequest 'CME.CloudPurchase.ValidationRequest')                                   | Purchase details to validate           |
| executionLogger | [System.Action{System.String}](http://msdn.microsoft.com/query/dev14.query?appId=Dev14IDEF1&l=EN-US&k=k:System.Action 'System.Action{System.String}') | Delegate for logging validation result |

##### Returns

Task<[ValidationResponse](#ValidationResponse) \>

<a name='T-CME-CloudPurchase-PurchaseType'></a>
## PurchaseType `enum`

#### Summary

Enum of types of purchase.

#### Values

| Name    | Value | Description |
|---------|-------|-------------|
| Unknown | 0     |             |
| Paid    | 1     |             |
| Test    | 2     |             |
| Promo   | 3     |             |


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

#### Summary

Purchase info to validate

#### Fields
| Name          | Type                                | Description |
|---------------|-------------------------------------|-------------|
| Store         | [Store](#T-CME-CloudPurchase-Store) |    Store where purchase was made         |
| PackageId     | string                              |             |
| ProductId     | string                              |             |
| ReceiptData   | string                              |             |
| UserId        | string                              |             |
| Price         | string                              |             |
| Currency      | string                              |             |
| PriceUsdCents | int                                 |             |

<a name='ValidationResponse'></a>
## ValidationResponse `type`

#### Summary

Details of validation result

<a name='F-CME-CloudPurchase-ValidationResponse-ErrorCode'></a>
### ErrorCode `constants`

#### Summary



<a name='F-CME-CloudPurchase-ValidationResponse-ErrorMessage'></a>
### ErrorMessage `constants`

#### Summary

<a name='F-CME-CloudPurchase-ValidationResponse-PurchaseType'></a>
### PurchaseType `constants`

#### Summary

Type of validated purchase.

#### See Also

- [CME.CloudPurchase.PurchaseType](#T-CME-CloudPurchase-PurchaseType 'CME.CloudPurchase.PurchaseType')

<a name='F-CME-CloudPurchase-ValidationResponse-Valid'></a>
### Valid `constants`

#### Summary

Is purchase valid or not.
