<p align="center">
  <a href="https://onsac.com/">
    <img src="https://github.com/onsac/Prestes/blob/main/Imagens/Projeto%20OnSAC-Prestes.png" >
  </a>
</p>

<h3 align="center">Contrato de API</h3>

<p align="center">
  Fluxo 002 - Liberação de Comissões
  </p>
  

## APIs – SIENGE

* **Atividade 3** Inserção do título no Sienge com base em nota fiscal eletrônica recebida.
```sh 
  URL PROD: https://api.sienge.com.br/produtoeinovacao/public/api/v1/eletronic-invoice-bills/ 
```
* **Atividade Atividade 17** Atualiza o título no Sienge.
```sh 
  URL PROD: https://api.sienge.com.br/produtoeinovacao/public/api/v1/bills/{billId}
```
* **Atividade Atividade 18 e Atividade 19** Inserção do título no Sienge.
```sh 
  URL PROD: https://api.sienge.com.br/produtoeinovacao/public/api/v1/bills/ 
```
## Contrato de APIs Origem e Destino

> **Atividade 3** : Inserção do título no Sienge com base em nota fiscal eletrônica recebida.

```diff
+ API POST: https://api.sienge.com.br/produtoeinovacao/public/api/v1/eletronic-invoice-bills/ 
```

```sh
{
  "debtorId": 0,
  "creditorId": 0,
  "documentIdentificationId": "string",
  "accessKey": "1231231231231231231231231231231231231231231",
  "installmentsNumber": 0,
  "indexId": 0,
  "baseDate": "2018-12-22",
  "dueDate": "2018-12-22",
  "billDate": "2018-12-22",
  "notes": "Despesa da obra",
  "budgetCategories": [
    {
      "costCenterId": 0,
      "paymentCategoriesId": "string",
      "percentage": 0
    }
  ]
}
```
> **Atividade 17** : Atualiza o título no Sienge.

```diff
+ API PATCH: https://api.sienge.com.br/produtoeinovacao/public/api/v1/bills/{billId}
```

```sh
{
  "documentIdentificationId": "NF",
  "documentNumber": "AX123"
}
```
> **Atividade 18 e Atividade 19** : Inserção do título no Sienge.

```diff
+ API POST: https://api.sienge.com.br/produtoeinovacao/public/api/v1/bills/
```

```sh
{
  "debtorId": 0,
  "creditorId": 0,
  "documentIdentificationId": "string",
  "documentNumber": "string",
  "issueDate": "2018-12-22",
  "installmentsNumber": 0,
  "indexId": 0,
  "baseDate": "2018-12-22",
  "dueDate": "2018-12-22",
  "billDate": "2018-12-22",
  "totalInvoiceAmount": 0,
  "notes": "string",
  "discount": 0,
  "budgetCategories": [
    {
      "costCenterId": 0,
      "paymentCategoriesId": "string",
      "percentage": 0
    }
  ],
  "taxes": [
    {
      "taxId": 0,
      "ibgeCityId": "4205407",
      "rate": 0,
      "amount": 0,
      "taxableBaseAmount": 0,
      "taxRateMarker": 0,
      "usesIncomeTaxTable": true
    }
  ],
  "departmentsCost": [
    {
      "departmentId": 0,
      "percentage": 0
    }
  ],
  "buildingsCost": [
    {
      "buildingId": 0,
      "buildingUnitId": 0,
      "costEstimationSheetId": "string",
      "percentage": 0
    }
  ]
}
```
