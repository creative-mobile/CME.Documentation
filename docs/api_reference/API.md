<a name='assembly'></a>
# Docs

## Contents

- [CloudPurchaseClient](#T-CME-CloudPurchase-CloudPurchaseClient 'CME.CloudPurchase.CloudPurchaseClient')
  - [Validate(request,executionLogger)](#M-CME-CloudPurchase-CloudPurchaseClient-Validate-CME-CloudPurchase-ValidationRequest,System-Action{System-String}- 'CME.CloudPurchase.CloudPurchaseClient.Validate(CME.CloudPurchase.ValidationRequest,System.Action{System.String})')
- [FakeReceipt](#T-CME-CloudPurchase-FakeReceipt 'CME.CloudPurchase.FakeReceipt')
- [ValidationRequest](#T-CME-CloudPurchase-ValidationRequest 'CME.CloudPurchase.ValidationRequest')
- [ValidationResponse](#T-CME-CloudPurchase-ValidationResponse 'CME.CloudPurchase.ValidationResponse')

<a name='T-CME-CloudPurchase-CloudPurchaseClient'></a>
## CloudPurchaseClient `type`

##### Namespace

CME.CloudPurchase

##### Summary

Client for validating purchases.

<a name='M-CME-CloudPurchase-CloudPurchaseClient-Validate-CME-CloudPurchase-ValidationRequest,System-Action{System-String}-'></a>
### Validate(request,executionLogger) `method`

##### Summary

Validate in-app purchase.

##### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| request | [CME.CloudPurchase.ValidationRequest](#T-CME-CloudPurchase-ValidationRequest 'CME.CloudPurchase.ValidationRequest') | Purchase details to validate |
| executionLogger | [System.Action{System.String}](http://msdn.microsoft.com/query/dev14.query?appId=Dev14IDEF1&l=EN-US&k=k:System.Action 'System.Action{System.String}') | Delegate for logging validation result |

<a name='T-CME-CloudPurchase-FakeReceipt'></a>
## FakeReceipt `type`

##### Namespace

CME.CloudPurchase

##### Summary

Class for emulating purchase

<a name='T-CME-CloudPurchase-ValidationRequest'></a>
## ValidationRequest `type`

##### Namespace

CME.CloudPurchase

##### Summary

Purchase info to validate

<a name='T-CME-CloudPurchase-ValidationResponse'></a>
## ValidationResponse `type`

##### Namespace

CME.CloudPurchase

##### Summary

Details of validation result
