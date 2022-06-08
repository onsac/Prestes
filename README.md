
<p align="center">
  <a href="https://onsac.com/">
    <img src="https://github.com/onsac/Prestes/blob/main/Projeto%20OnSAC-Prestes.png" >
  </a>
</p>

<h3 align="center">Contrato de API</h3>

<p align="center">
  Fluxo 001 - Integração de Cliente CV - Siange
  </p>

## APIs – SIENGE

* **Atividade 8 , Atividade 9 e Atividade 10  ** Busca um contrato de vendas.
  ```sh 
  URL PROD: https://api.sienge.com.br/produtoeinovacao/public/api/v1/sales-contracts/{id}
  ```

* **Atividade 10.1, Atividade 11 e Atividade 12** : Atualiza dados de contratos vinculados ao crédito associativo

 ```sh 
  URL PROD: https://api.sienge.com.br/produtoeinovacao/public/api/v1/sales-contracts/{id}
  ```

## AIO-QUOTE – Contrato de APIs Origem e Destino

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

