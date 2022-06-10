<p align="center">
  <a href="https://onsac.com/">
    <img src="https://github.com/onsac/Prestes/blob/main/Imagens/Projeto%20OnSAC-Prestes.png" >
  </a>
</p>

<h3 align="center">Contrato de API</h3>

<p align="center">
  Fluxo 001 - Integração de Cliente CV - Siange
  </p>
  
## API – NEXXERA

* **Atividade 2** Notificação de Boleto
Webhook
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
 ## APIs CVCRM

* **Atividade 3, Atividade 4, Atividade 5, Atividade 6, Atividade 7, Atividade 8 e Atividade 9** : Retornar os contratos das unidades do cliente

 ```sh 
  URL PROD://integracao.cvcrm.com.br/api/v1/prestes/contratos
```

## Contrato de APIs Origem e Destino

> **Atividade 8 , Atividade 9 e Atividade 10** : Busca um contrato de vendas.

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
> **Atividade 3, Atividade 4, Atividade 5, Atividade 6, Atividade 7, Atividade 8 e Atividade 9** : Retornar os contratos das unidades do cliente

 ```diff
  + API GET://integracao.cvcrm.com.br/api/v1/prestes/contratos
```
```sh
{
  "total": 22,
  "offset": 0,
  "limit": 30,
  "contratos": [
    {
      "idcontrato": 1662,
      "titulo": "Associado",
      "tipo": "Distrato",
      "criado": "2020-02-17 13:40:36",
      "unidade": {
        "unidades": [
          {
            "idunidade": 140,
            "nome": "504"
          }
        ],
        "perfil": {
          "nome": "Titular da Reserva",
          "sigla": "TR"
        },
        "previsao_entrega": "2021-02-01",
        "porcentagem_total_estagio_obra_unidade": 22.27,
        "etapa": {
          "idetapa": 4,
          "nome": "Única"
        },
        "bloco": {
          "idbloco": 2216,
          "nome": "Várias unidades"
        },
        "empreendimento": {
          "idempreendimento": 3,
          "nome": "9201 - Varándãs Do Garcia 9",
          "porcentagem_total_estagio_obra": 50,
          "permitir_criar_atendimento": true,
          "foto": {
            "nome": "construtor.jpg",
            "tipo": "image/jpeg",
            "tamanho": 2672,
            "url": "https://relacionar.cvcrm.com.br/api/get/imagens/painel_cliente_logo/[[LARGURA]]/[[ALTURA]]/20210111152544_5ffc98284c62c.jpg"
          }
        },
        "andar": "1º Andar",
        "coluna": "3"
      },
      "arquivo": {
        "nome": "ATO - Boleto _ 24_02_2019 - 3.pdf",
        "tipo": "application/pdf",
        "tamanho": "16298",
        "url": "http://dev.cvcrm.com.br/api/get/download/reservas_contratos|2020|01|3867/20200514091903_5ebd373739148.pdf"
      }
    }
  ]
}
```
