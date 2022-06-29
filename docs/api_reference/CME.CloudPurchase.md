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

### Implements 

[IDisposable](https://docs.microsoft.com/en-gb/dotnet/api/system.idisposable?view=net-6.0){target=_blank}

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
| Paid    | 1     | Оплачено через магазин |
| Test    | 2     | Тестовый платеж        |
| Promo   | 3     | Промокод               |


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
| Name          | Type                                | Description                                       |
|---------------|-------------------------------------|---------------------------------------------------|
| Store         | [Store](#T-CME-CloudPurchase-Store) | Store where purchase was made                     |
| PackageId     | string                              | Id приложения                                     |
| ProductId     | string                              | Id товара                                         |
| ReceiptData   | string                              | Данные с результатами обработки платежа магазином |
| UserId        | string                              | Идентификатор пользователя                        |
| Price         | string                              | Цена в местной валюте                             |
| Currency      | string                              | Местная валюта                                    |
| PriceUsdCents | int                                 | Цена в USD центах                                 |

<a name='ValidationResponse'></a>
## ValidationResponse `type`

#### Summary

Details of validation result from CME Cloud Purchase cloud side

#### Fields 
| Name         | Type                                              | Description                               |
|--------------|---------------------------------------------------|-------------------------------------------|
| Valid        | bool                                              | Флаг валидности платежа                   |
| PurchaseType | [PurchaseType](#T-CME-CloudPurchase-PurchaseType) | Тип платежа                               |
| ErrorCode    | string                                            | Код ошибки от валидируюшей платформы      |
| ErrorMessage | string                                            | Описание ошибки от валидируюшей платформы |

