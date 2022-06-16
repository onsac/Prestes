<p align="center">
    <img src="https://github.com/onsac/Prestes/blob/main/Imagens/Projeto%20OnSAC-Prestes.png" >
  </a>
</p>

<h3 align="center">Contrato de API</h3>

<p align="center">
  Fluxo 003 - Lançamento de NFs
  </p>

## APIs Sienge

* **Busca o credor no Sienge:** 
 
```sh 
  URL GET: https://api.sienge.com.br/produtoeinovacao/public/api/v1/creditors/{creditorId}
```
* **Inserção do título no Sienge:** 
 
```sh 
  URL POST: https://api.sienge.com.br/produtoeinovacao/public/api/v1/bills
```

* **Cadastra uma nota fiscal de compra:**

```sh
URL POST: https://api.sienge.com.br/produtoeinovacao/public/api/v1/purchase-invoices
```
* **Insere itens em uma nota fiscal já existente:**

```sh
URL POST: https://api.sienge.com.br/produtoeinovacao/public/api/v1/purchase-invoices/{sequentialNumber}/items/purchase-orders/delivery-schedules
```
* **Busca os títulos no Sienge:**

```sh
URL GET: https://api.sienge.com.br/produtoeinovacao/public/api/v1/bills
```

* **Retorna a liberação de uma medição:**

```sh
URL GET: https://api.sienge.com.br/produtoeinovacao/public/api/v1/supply-contracts/measurements/clearing
```

* **Cria uma nova medição para o respectivo contrato e obra:**

```sh
URL POST: https://api.sienge.com.br/produtoeinovacao/public/api/v1/supply-contracts/measurements
```
* **Busca os impostos do título:**

```sh
URL GET: https://api.sienge.com.br/produtoeinovacao/public/api/v1/bills/{billId}/taxes
```
* **Inserção de anexo no título:**

```sh
URL POST: https://api.sienge.com.br/produtoeinovacao/public/api/v1/bills/{billId}/attachments
```
* **Consulta solicitação de compra:**

```sh
URL GET: https://api.sienge.com.br/produtoeinovacao/public/api/v1/purchase-requests/{purchaseRequestId}
```
* **Realiza leitura de títulos:**

```sh
URL GET: https://api.sienge.com.br/produtoeinovacao/public/api/v1/defaulters-receivable-bills
```
## APIs NEXXERA


* **Consulta de Títulos - Boleto / Pix**

```diff
- URL GET: https://cobranca-eletronica-core-dev.cloudint.nexxera.com/v1/billet
- {"our_number": null, "digitable_line": "", "status": "", "message": {"key": ["This field is required."], "hash": ["This field is required."]}, "pdf_content": ""}
```

* **Inclusão de Títulos - Boleto / Pix**
```diff
- URL POST: https://cobranca-eletronica-core-dev.cloudint.nexxera.com/v1/billet
- {"our_number": null, "digitable_line": "", "status": "", "message": {"key": ["This field is required."], "hash": ["This field is required."]}, "pdf_content": ""}
```


## Contrato de APIs Origem e Destino

> **GET - /CREDITORS/{CREDITORID** 

```diff
+ API GET: https://api.sienge.com.br/produtoeinovacao/public/api/v1/creditors/{creditorId}
```

```sh
{
  "id": 0,
  "name": "string",
  "tradeName": "string",
  "cpf": "string",
  "cnpj": "string",
  "supplier": "string",
  "broker": "string",
  "employee": "string"
}

```

> **GET - /BILLS** 

```diff
+ API GET: https://api.sienge.com.br/produtoeinovacao/public/api/v1/bills
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

> **GET - /BILLS** 

```diff
+ API GET: https://api.sienge.com.br/produtoeinovacao/public/api/v1/bills
```

```sh
{
  "id": 0,
  "debtorId": 0,
  "creditorId": 0,
  "documentIdentificationId": "string",
  "documentNumber": "string",
  "issueDate": "2018-12-22",
  "installmentsNumber": 0,
  "totalInvoiceAmount": 0,
  "tenantUrl": "https://api.sienge.com.br/suporte/sienge/public/api",
  "notes": "Observação título Dez2017",
  "discount": 0,
  "status": "\"S\" - Completo | \"N\" - Incompleto | \"I\" - Em inclusão",
  "originId": "\"AC\" - Administração de Compras | \"RA\" - Administração de Obras | \"AI\" - Apuração de Impostos | \"CO\" - Comercial | \"CF\" - Conhecimento de Frete | \"CP\" - Contas a Pagar | \"ME\" - Contratos e Medições | \"MO\" - Controle de Mão de Obra | \"DV\" - Devolução de Nota Fiscal | \"RF\" - Financiamento Bancário | \"FP\" - Folha de Pagamento | \"FE\" - Frota de Equipamentos | \"GI\" - Guia de Impostos | \"LO\" - Locação de Imóveis\" | \"SE\" - Sistemas Externos",
  "registeredBy": "USER",
  "registeredDate": "2022-06-10 10:00:00",
  "changedBy": "USER",
  "changedDate": "2022-06-10 10:00:00",
  "links": [
    {
      "rel": "debtor",
      "href": "http://../v1/debtor/1"
    }
  ]
}
```
> **POST - PURCHASE-INVOICES** 

```diff
+ API POST: https://api.sienge.com.br/produtoeinovacao/public/api/v1/purchase-invoices
```

```sh

  "documentId": "NF",
  "number": "6546523",
  "series": "123",
  "supplierId": 236,
  "companyId": 29,
  "movementTypeId": 1,
  "movementDate": "2021-04-23",
  "issueDate": "2021-04-23",
  "notes": "Compra de materiais faltantes para a obra XPTO"
}
```

> **POST - PURCHASE-INVOICES/{SEQUENTIALNUMBER}/ITEMS/PURCHASE-ORDERS/DELIVERY-SCHEDULES** 

```diff
+ API POST: https://api.sienge.com.br/produtoeinovacao/public/api/v1/purchase-invoices/{sequentialNumber}/items/purchase-orders/delivery-schedules
```

```sh
{
  "deliveriesOrder": [
    {
      "purchaseOrderId": 457,
      "itemNumber": 2,
      "deliveryScheduleNumber": 1,
      "deliveredQuantity": 4.5,
      "keepBalance": true
    }
  ],
  "copyNotesPurchaseOrders": true,
  "copyNotesResources": false,
  "copyAttachmentsPurchaseOrders": true
}

```

> **GET - SUPPLY-CONTRACTS/MEASUREMENTS/CLEARING** 

```diff
+ API GET: https://api.sienge.com.br/produtoeinovacao/public/api/v1/supply-contracts/measurements/clearing
```
```sh
{
  "documentId": "CT",
  "contractNumber": "123A",
  "buildingId": 1,
  "measurementNumber": 1,
  "securityDepositBillId": 12345,
  "exchangeBillId": 12345,
  "isFinished": true,
  "downPaymentValue": 12.47,
  "bills": [
    {
      "billId": 1
    }
  ]
}
```

> **POST - SUPPLY-CONTRACTS/MEASUREMENTS** 

```diff
+ API POST: https://api.sienge.com.br/produtoeinovacao/public/api/v1/supply-contracts/measurements
```
```sh
{
  "measurementDate": "2021-04-18",
  "dueDate": "2021-06-22",
  "notes": "Lorem ipsum dolor sit amet.",
  "makeUnauthorized": true,
  "items": [
    {
      "buildingUnitId": 3,
      "itemId": 25,
      "measuredQuantity": 45.4918
    }
  ]
}
```
> **GET - /BILLS/{BILLID}/TAXES** 

```diff
+ API GET: https://api.sienge.com.br/produtoeinovacao/public/api/v1/bills/{billId}/taxes
```
```sh
{
  "resultSetMetadata": {
    "count": 0,
    "offset": 0,
    "limit": 0
  },
  "results": [
    {
      "taxId": 0,
      "ibgeCityId": "4205407",
      "rate": 0,
      "amount": 0,
      "taxableBaseAmount": 0,
      "taxRateMarker": 0,
      "usesIncomeTaxTable": true
    }
  ]
}
```
> **POST - /BILLS/{BILLID}/ATTACHMENTS** 

```diff
+ API POST: https://api.sienge.com.br/produtoeinovacao/public/api/v1/bills/{billId}/attachments
```
```sh
{
  "status": 0,
  "developerMessage": "Developer description message",
  "clientMessage": "Client description message."
}
```
> **GET - /PURCHASE-REQUESTS/{PURCHASEREQUESTID}** 

```diff
+ API GET: https://api.sienge.com.br/produtoeinovacao/public/api/v1/purchase-requests/{purchaseRequestId}
```
```sh
{
  "id": 2104,
  "buildingId": 300,
  "departamentId": 5,
  "requesterUser": "USER",
  "requestDate": "2018-01-03",
  "notes": "Annotation",
  "status": "PENDING",
  "consitent": "CONSISTENT",
  "createdBy": "USER",
  "createdAt": "2018-03-11T14:20:00.000-03:00",
  "modifiedBy": "ANOTHERUSER",
  "modifiedAt": "2018-04-02T18:20:00.000-03:00"
}
```
> **GET - /DEFAULTERS-RECEIVABLE-BILLS** 

```diff
+ API GET: https://api.sienge.com.br/produtoeinovacao/public/api/v1/defaulters-receivable-bills
```
```sh
{
  "data": [
    {
      "receivableBillId": 0,
      "issueDate": "string",
      "documentNumber": "string",
      "units": "string",
      "receivableBillValue": 0,
      "defaulterInstallments": [
        {
          "installmentId": 0,
          "conditionType": "string",
          "dueDate": "string",
          "daysOfDelay": 0,
          "correctedValueWithoutAdditions": "string",
          "proRata": "string",
          "interest": "string",
          "fine": "string",
          "totalAdditions": "string",
          "correctedValueWithAdditions": "string"
        }
      ],
      "defaulterJudicialActivities": [
        {
          "recordDate": "string",
          "situation": "string",
          "concluded": "string",
          "observation": "string"
        }
      ]
    }
  ]
}
```
