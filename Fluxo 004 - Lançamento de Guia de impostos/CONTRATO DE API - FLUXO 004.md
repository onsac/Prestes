 <p align="center">
    <img src="https://github.com/onsac/Prestes/blob/main/Imagens/Projeto%20OnSAC-Prestes.png" >
  </a>
</p>

<h3 align="center">Contrato de API</h3>

<p align="center">
  Fluxo 004 - Lançamento de Guia de impostos
</p>

## Workflow do Fluxo 004
<p align="center">
    <img src="https://github.com/onsac/Prestes/blob/main/Fluxo%20004%20-%20Lan%C3%A7amento%20de%20Guia%20de%20impostos/Desenho%20Fluxo%20004.png" >
</p>

## APIs SIENGE

* **Inserção do título no Sienge:** 
 
```sh 
  URL POST: https://api.sienge.com.br/produtoeinovacao/public/api/v1/bills/
```
* **Busca os títulos no Sienge de acordo com a data de alteração:** 
 
```sh 
  URL GET: https://api.sienge.com.br/produtoeinovacao/public/api/v1/bills/by-change-date
```
* **Busca o título no Sienge:** 
 
```sh 
  URL GET: https://api.sienge.com.br/produtoeinovacao/public/api/v1/bills/{billId}
```
* **Atualiza o título no Sienge:** 
 
```sh 
  URL PATCH: https://api.sienge.com.br/produtoeinovacao/public/api/v1/bills/{billId}
```
* **Atualiza o título no Sienge:** 
 
```sh 
  URL PATCH: https://api.sienge.com.br/produtoeinovacao/public/api/v1/bills/{billId}
```
* **Busca todos os centros de custo no Sienge:** 
 
```sh 
  URL GET: https://api.sienge.com.br/produtoeinovacao/public/api/v1/cost-centers/{costCenterId}
```
* **Departamento conforme Planilha:** 
 
```sh 
  URL GET: https://api.sienge.com.br/produtoeinovacao/public/api/v1/departments/{departmentId}
```
* **Realizar liberação do pagamento:** 
 
```sh 
  URL PUT: https://api.sienge.com.br/produtoeinovacao/public/api/v1/purchase-orders/{purchaseOrderId}/authorize
```
## Contrato de APIs Origem e Destino
> **POST - /BILLS/**

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

> **GET - /BILLS/BY-CHANGE-DATE**

```diff
+ API GET: https://api.sienge.com.br/produtoeinovacao/public/api/v1/bills/by-change-date
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
> **GET - /BILLS/{BILLID}**

```diff
+ API GET: https://api.sienge.com.br/produtoeinovacao/public/api/v1/bills/{billId}
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
> **PATCH - /BILLS/{BILLID}**

```diff
+ API PATCH: https://api.sienge.com.br/produtoeinovacao/public/api/v1/bills/{billId}
```

```sh
{
  "documentIdentificationId": "NF",
  "documentNumber": "AX123"
}
```

> **GET - /COST-CENTERS/{COSTCENTERID}**

```diff
+ API PATCH: https://api.sienge.com.br/produtoeinovacao/public/api/v1/cost-centers/{costCenterId}
```

```sh
{
  "id": 0,
  "name": "string",
  "idCompany": 0,
  "cnpj": "string",
  "buildingSectors": [
    {
      "id": "string",
      "name": "string",
      "accountableId": "string",
      "accountableName": "string"
    }
  ]
}
```
> **GET - /DEPARTMENTS/{DEPARTMENTID}**

```diff
+ API PATCH: https://api.sienge.com.br/produtoeinovacao/public/api/v1/departments/{departmentId}
```

```sh
{
  "departmentId": 1,
  "departmentName": "Departamento 1"
}
```

> **GET - /DEPARTMENTS/{DEPARTMENTID}**

```diff
+ API PATCH: https://api.sienge.com.br/produtoeinovacao/public/api/v1/purchase-orders/{purchaseOrderId}/authorize

```sh
{
  "status": "string",
  "developerMessage": "string",
  "clientMessage": "string",
  "errors": [
    {
      "field": "string",
      "message": "string"
    }
  ]
}
```
