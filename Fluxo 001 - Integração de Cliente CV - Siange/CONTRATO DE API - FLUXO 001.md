<p align="center">
  <a href="https://onsac.com/">
    <img src="https://github.com/onsac/Prestes/blob/main/Projeto%20OnSAC-Prestes.png" >
  </a>
</p>

<h3 align="center">Contrato de API</h3>

<p align="center">
  Fluxo 001 - Integração de Cliente CV - Siange
  </p>
  
## API – NEXXERA

* **Atividade 2** Notificação de Boleto

```sh 
 {
          "instructions": [{
              "type": "BOLETO",
              "txid": "",
              "endToEndId": "",
              "fare_amount": "",
              "environment": "HOMOLOGACAO",
              "bank": 341,
              "agreement_number": "1234567890",
              "portfolio_id": "109",
              "document_number": "123456",
              "our_number": "123456",
              "your_number": "123456",
              "emission_date": "2021-09-13",
              "due_date": "2021-10-13",
              "nominal_amount": "999.88",
              "return_code": 6,
              "remittance_code": 0,
              "description": "Liquidação",
              "value_one": {
                  "type": "VALOR_PAGO",
                  "old_value": "0.00",
                  "new_value": "125.00"
              },
              "value_two": {
                  "type": "ACRESCIMO_COBRADO",
                  "old_value": "0.00",
                  "new_value": "0.05"
              },
              "value_three": {
                  "type": "DESCONTO_CONCEDIDO",
                  "old_value": "0.00",
                  "new_value": "0.01"
              },
              "value_four": {
                  "type": "ABATIMENTO_CONCEDIDO",
                  "old_value": "0.00",
                  "new_value": "0.02"
              },
              "value_five": {
                  "type": "DATA_CREDITO",
                  "old_value": 0,
                  "new_value": "2019-01-29"
              },
              "value_six": {
                  "type": "DATA_LIQUIDACAO",
                  "old_value": 0,
                  "new_value": "2019-03-25"
              }
          }]
      }
```
## APIs – SIENGE

* **Atividade 8 , Atividade 9 e Atividade 10** Busca um contrato de vendas.
 
```sh 
  URL PROD: https://api.sienge.com.br/produtoeinovacao/public/api/v1/sales-contracts/{id}
```

* **Atividade 10.1, Atividade 11 e Atividade 12** : Atualiza dados de contratos vinculados ao crédito associativo

 ```sh 
  URL PROD: https://api.sienge.com.br/produtoeinovacao/public/api/v1/sales-contracts/{id}
 ```

## Contrato de APIs Origem e Destino

> **Atividade 8 , Atividade 9 e Atividade 10 ** : Busca um contrato de vendas.

```diff
+ API GET: https://api.sienge.com.br/produtoeinovacao/public/api/v1/sales-contracts/{id}
```

```sh
{
  "id": 0,
  "enterpriseId": 0,
  "receivableBillId": 0,
  "contractDate": "string",
  "issueDate": "string",
  "number": "string",
  "externalId": "string",
  "correctionType": "string",
  "situation": "string",
  "discountType": "string",
  "discountPercentage": 0,
  "value": 0,
  "totalSellingValue": 0,
  "cancellationDate": "string",
  "cancellationReason": "string",
  "proRataIndexer": 0,
  "interestType": "string",
  "interestPercentage": 0,
  "fineRate": 0,
  "lateInterestCalculationType": "string",
  "dailyLateInterestValue": 0,
  "salesContractCustomers": {
    "id": 0,
    "main": true,
    "spouse": true,
    "participationPercentage": 0
  },
  "salesContractUnits": {
    "id": 0,
    "main": true,
    "name": "string",
    "participationPercentage": 0
  },
  "paymentConditions": {
    "conditionTypeId": "string",
    "conditionTypeName": "string",
    "totalValue": 0,
    "installmentsNumber": 0,
    "firstPayment": "string",
    "bearerId": "string",
    "bearerName": "string",
    "unitsGrouping": "string"
  },
  "brokers": {
    "id": 0,
    "main": true
  },
  "links": [
    {
      "rel": "guarantors",
      "href": "http://../v1/sales-contracts/1/guarantors"
    }
  ]
}
```

> **Atividade 10.1, Atividade 11 e Atividade 12** : Atualiza dados de contratos vinculados ao crédito associativo


```diff
+ API PATCH: https://api.sienge.com.br/produtoeinovacao/public/api/v1/sales-contracts/{id}
```

```sh
{
  "financialInstitutionNumber": "string",
  "financialInstitutionDate": "string",
  "keysDeliveredAt": "string",
  "registerPropertyDate": "string",
  "sellingCategory": "string",
  "financingStatus": "string"
}
```

> **Atividade 10.1** : Atualiza dados de contratos vinculados ao crédito associativo

