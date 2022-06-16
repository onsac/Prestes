<p align="center">
    <img src="https://github.com/onsac/Prestes/blob/main/Imagens/Projeto%20OnSAC-Prestes.png" >
  </a>
</p>

<h3 align="center">Contrato de API</h3>

<p align="center">
  Fluxo 001 - Integração de Cliente CV - Siange
  </p>
  
 ## Workflow do Fluxo 001 
  <p align="center">
    <img src="https://github.com/onsac/Prestes/blob/main/Fluxo%20001%20-%20Integra%C3%A7%C3%A3o%20de%20Cliente%20CV%20-%20Siange/Workflow%20do%20Fluxo%20001.pptx.png" >
  </a>
</p>
 
  
## API – NEXXERA

* **Notificação de Boleto** 

```diff
- Webhook
- {
-          "instructions": [{
-              "type": "BOLETO",
-              "txid": "",
-              "endToEndId": "",
-              "fare_amount": "",
-              "environment": "HOMOLOGACAO",
-              "bank": 341,
-              "agreement_number": "1234567890",
-              "portfolio_id": "109",
-              "document_number": "123456",
-              "our_number": "123456",
-              "your_number": "123456",
-              "emission_date": "2021-09-13",
-              "due_date": "2021-10-13",
-              "nominal_amount": "999.88",
-              "return_code": 6,
-              "remittance_code": 0,
-              "description": "Liquidação",
-              "value_one": {
-                  "type": "VALOR_PAGO",
-                  "old_value": "0.00",
-                  "new_value": "125.00"
-              },
-              "value_two": {
-                  "type": "ACRESCIMO_COBRADO",
-                  "old_value": "0.00",
-                  "new_value": "0.05"
-              },
-              "value_three": {
-                  "type": "DESCONTO_CONCEDIDO",
-                  "old_value": "0.00",
-                  "new_value": "0.01"
-              },
-              "value_four": {
-                  "type": "ABATIMENTO_CONCEDIDO",
-                  "old_value": "0.00",
-                  "new_value": "0.02"
-              },
-              "value_five": {
-                  "type": "DATA_CREDITO",
-                  "old_value": 0,
-                  "new_value": "2019-01-29"
-              },
-              "value_six": {
-                  "type": "DATA_LIQUIDACAO",
-                  "old_value": 0,
-                  "new_value": "2019-03-25"
-              }
-          }]
-      }
```

* **Consulta de Títulos - Boleto / Pix**

```diff
- URL GET: https://cobranca-eletronica-core-dev.cloudint.nexxera.com/v1/billet
- {"our_number": null, "digitable_line": "", "status": "", "message": {"key": ["This field is required."], "hash": ["This field is required."]}, "pdf_content": ""}
```
## APIs – SIENGE

* **Busca um contrato de vendas:** 
 
```sh 
  URL GET: https://api.sienge.com.br/produtoeinovacao/public/api/v1/sales-contracts/{id}
```

* **Atualiza dados de contratos vinculados ao crédito associativo:**

 ```sh 
  URL POST: https://api.sienge.com.br/produtoeinovacao/public/api/v1/sales-contracts/{id}
 ```
 ## APIs CVCRM

* **GET - /RESERVA** Esta API serve como um informativo ao sistema legado acerca das reservas que podem ser integradas como vendidas, por esse motivo não há solicitação de preenchimento de dados para a sua execução. Neste caso, como a requisição é do tipo 'GET', somente são necessários passar os parâmetros de autenticação por meio do HEADER, ou seja, a requisição não terá BODY.

 ```sh 
  URL PROD://integracao.cvcrm.com.br/api/v1/prestes/cvio/reserva
```
* **GET - /LOTES** A interface viabiliza a consulta de lote do sistema CV. A consulta é realizada através dos dados enviados na URL, podendo conter id do lote, podendo também passar o limite e a página por parâmetro. A requisição retorna os dados do(s) lote(s) caso seja especifícado um id do lote, caso não, retorna todos os lotes.

 ```sh 
  URL PROD://integracao.cvcrm.com.br/api/v1/prestes/cv/lotes/{idLote}
```
* **POST - /BOLETOS** :Interface responsável por cadastrar boletos dentro do Construtor de Vendas quando a parcela da reserva for da série ato ou sinal.
 ```sh 
  URL PROD://integracao.cvcrm.com.br/api/v1/prestes/cv/boletos
```
## Contrato de APIs Origem e Destino

> **GET - SALES CONTRACTS** 

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

> **POST - SALES CONTRACTS** 

```diff
+ API POST: https://api.sienge.com.br/produtoeinovacao/public/api/v1/sales-contracts/{id}
```

```sh
{
  "enterpriseId": 0,
  "externalId": "string",
  "number": "string",
  "contractDate": "string",
  "keysDeliveredAt": "string",
  "accountingDate": "string",
  "readjustAfterOf": "string",
  "saleType": "string",
  "correctionType": "string",
  "anualCorrectionType": "string",
  "generateResidue": "string",
  "diluteResidue": "string",
  "financialPlanAccount": "string",
  "value": 0,
  "totalSellingValue": 0,
  "note": "string",
  "readjustEach": 0,
  "readjustMonth": 0,
  "lateInterestDaily": true,
  "proRataIndexer": 0,
  "interestType": "string",
  "interestPercentage": 0,
  "fineRate": 0,
  "dailyLateInterestValue": 0,
  "paymentConditions": [
    {
      "conditionTypeId": "string",
      "installmentsNumber": 0,
      "firstPayment": "string",
      "totalValue": 0,
      "matchMaturities": "string",
      "bearerId": 0,
      "indexerId": 0,
      "baseDate": "string",
      "interestType": "string",
      "interestPercentage": 0,
      "monthsGracePeriod": 0,
      "baseDateInterest": "string"
    }
  ],
  "salesContractCustomers": [
    {
      "id": 0,
      "main": true,
      "participationPercentage": 0,
      "safePercentage": 0,
      "participationPercentageSpouse": 0
    }
  ],
  "salesContractUnits": [
    {
      "id": 0,
      "main": true,
      "participationPercentage": 0
    }
  ],
  "brokers": [
    {
      "id": 0,
      "main": true
    }
  ],
  "salesContractGuarantors": [
    {
      "name": "string",
      "cnpj": "string",
      "cpf": "string",
      "nationality": "string",
      "numberIdentityCard": "string",
      "professionId": 0,
      "civilStatusId": 0,
      "address": {
        "cityId": 0,
        "complement": "string",
        "neighborhood": "string",
        "number": "string",
        "streetName": "string",
        "zipCode": "string"
      },
      "spouse": {
        "name": "string",
        "cpf": "string",
        "numberIndentityCard": "string",
        "email": "string",
        "birthDate": "string",
        "address": {
          "cityId": 0,
          "complement": "string",
          "neighborhood": "string",
          "number": "string",
          "streetName": "string",
          "zipCode": "string"
        }
      },
      "phones": [
        {
          "number": "string",
          "main": true,
          "type": "string",
          "note": "string"
        }
      ]
    }
  ]
}
```
> **GET - /RESERVA** 

```diff
+ API GET://integracao.cvcrm.com.br/api/v1/prestes/cvio/reserva
```
```sh
{
  "7367": {
    "situacao": {
      "idsituacao": "47",
      "situacao": "Pode Faturar"
    },
    "imobiliaria": {
      "email": "email_imobiliaria@mail.com",
      "telefone": "(79) 99999-8888",
      "cnpj": "12345678000123"
    },
    "unidade": {
      "empreendimento": "Empreendimento Alegria",
      "idempreendimento_int": "4502",
      "etapa": "FASE 2",
      "idetapa_int": "f2",
      "bloco": "Bloco 01",
      "idbloco_int": "035",
      "unidade": "101",
      "idunidade_cv": "27449",
      "idunidade_int": "9",
      "planta": null,
      "tipologia": "2 Qts / 1 Suíte",
      "posicao": "Sul",
      "area_privativa": "100.00",
      "andar": "1",
      "coluna": "1",
      "tipo": "apartamento",
      "numeracao_deposito": "1",
      "vagas_garagem": "1",
      "area_garagem": "10.00",
      "area_comum": "50.00",
      "area_terreno": "120.00",
      "fracao_ideal": "1.0000000"
    },
    "titular": {
      "nome": "Cliente teste",
      "idpessoa_cv": "16651",
      "idpessoa_int": "0000361801",
      "documento_tipo": "cpf",
      "nascimento": "1996-01-23",
      "documento": "05873544530",
      "rg": "54343435",
      "rg_orgao_emissor": "SSP-SE1",
      "rg_data_emissao": "2019-08-01",
      "estado_civil": "Solteiro(a)",
      "profissao": "Promotor Público",
      "logradouro": "Travessa",
      "idlogradouro": "10",
      "endereco": "Travessa Benjamin Constant",
      "numero": "1020",
      "complemento": "casa2",
      "bairro": "Centro",
      "cep": "49010100",
      "cidade": "Aracaju",
      "estado": "Sergipe",
      "pais": "Brasil",
      "telefone": "(22) 2222-22222",
      "celular": "(98) 99999-7777",
      "email": "email_titular@mail.com",
      "sexo": "F",
      "marketing_pos_venda": "Sergipe",
      "como_ficou_sabendo": "sITE",
      "renda_familiar": "23121.21"
    },
    "coretor": {
      "corretor": "Corretor teste",
      "idcorretor_int": "187",
      "idcorretor_cv": "5928",
      "idimobiliaria_cv": "274",
      "idimobiliaria_int": "41250",
      "email": "email_corretor@mail.com",
      "telefone": "(11) 11111-1111",
      "documento": "30828950504",
      "cnpj_faturamento": "12399934000105",
      "razaosocial_faturamento": "CORRETOR QC",
      "nomefantasia_faturamento": "Central",
      "data_nasc": "1970-01-28",
      "sexo": "M",
      "creci": "98547",
      "imobiliaria": "IMOBILIÁRIA QC"
    },
    "condicoes": {
      "valor_contrato": "323.000",
      "valor_venda": "300.000",
      "series": [
        {
          "idcondicao": "452556",
          "indexador": "REAL",
          "forma_pagamento": "BL",
          "quantidade": "1",
          "serie": "ATO - Bexs",
          "possui_juros": "S",
          "possui_correcao": "N",
          "juros_condicao": "NC",
          "juros_contrato": 1003.7,
          "prestacao_saf": 1003.7,
          "idserie_int": "1874",
          "valor": "323.000",
          "vencimento": "2020-12-22",
          "fixo": 1
        }
      ],
      "total_proposta": "323.000"
    },
    "comissoes": {
      "1234": {
        "comissao_para": "Corretor",
        "cpf_faturamento": "13836782000145",
        "cnpj_faturamento": "Corretor",
        "comissao_quem": "CORRETOR QC",
        "comissao_tipo": "Comissão",
        "comissao_porcentagem": "2.00",
        "comissao_valor": "6.460"
      },
      "comissao_valortotal": "6.460",
      "premio_valortotal": "0.00"
    },
    "idproposta_cv": "8417",
    "idproposta_int": "743",
    "vendida": null,
    "observacoes": "Observação exemplo",
    "data_contrato": "2022-04-12",
    "data": "2021-04-19 11:45:43",
    "contratos": [
      {
        "idcontrato": "1",
        "contrato": "ATO - Bexs",
        "data": "1874"
      }
    ],
    "campos_adicionais": [
      {
        "idcampo_adicional": "1",
        "nome": "Título do campo",
        "valor": "valor gravado na reserva",
        "nome_referencia": "nome da referência"
      }
    ]
  }
}
```

> **GET - /LOTES**

```diff
+ API GET://integracao.cvcrm.com.br/api/v1/prestes/cv/lotes/{idLote}
```
```sh
{
  "total": 12340,
  "limite": "5",
  "lotes": [
    {
      "idlotepagamento": "123",
      "situacao_lote": "1",
      "valor_lote": "100.50",
      "nome": "Lote de Pagamento #123",
      "nota_fiscal": "0000",
      "descricao": "Descrição de teste",
      "observacao": "Observação de teste",
      "comissoes": {
        "idcomissao": "456",
        "pagamentos": {
          "idpagamento_comissao": "456",
          "data_pagamento": "2021-07-17",
          "idcomissao": "456",
          "nota_fiscal_pagamento": "000001",
          "situacao_comissao": "Pagamento Direto",
          "situacao_pagamamento": "Programado",
          "valor_pagamento": "90.37",
          "data_medicao_pagamento": "2021-07-17",
          "observacao_pagamento": "Observação de teste"
        }
      }
    }
  ]
}
```

> **POST - /BOLETOS** 

```diff
+ API POST://integracao.cvcrm.com.br/api/v1/prestes/cv/boletos
```
```sh
{
  "idreserva_cv": 5458954,
  "idcondicaoparcela_cv": 58625569,
  "documento_cliente": "45670622804",
  "situacaoparcela_cv": "EA",
  "boleto_base64": "T2zDoSwgbXVuZG8h"
}
```
