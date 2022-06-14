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

* **Atividade 1** Notificação de Boleto
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

* **Atividade 2** 

 ```sh 
  URL PROD://integracao.cvcrm.com.br/api/v1/prestes/cvio/reserva
```
* **Atividade 3, Atividade 3.1, Atividade 3.2** :A interface viabiliza a consulta de lote do sistema CV. A consulta é realizada através dos dados enviados na URL, podendo conter id do lote, podendo também passar o limite e a página por parâmetro. A requisição retorna os dados do(s) lote(s) caso seja especifícado um id do lote, caso não, retorna todos os lotes.

 ```sh 
  URL PROD://integracao.cvcrm.com.br/api/v1/prestes/cv/lotes/{idLote}
```
* **Atividade 4, Atividade 5, Atividade 6 e Atividade 7** :Interface responsável por cadastrar boletos dentro do Construtor de Vendas quando a parcela da reserva for da série ato ou sinal.
 ```sh 
  URL PROD://integracao.cvcrm.com.br/api/v1/prestes/cv/boletos
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
> **Atividade 2** 

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

> **Atividade 3, Atividade 3.1, Atividade 3.2** :A interface viabiliza a consulta de lote do sistema CV. A consulta é realizada através dos dados enviados na URL, podendo conter id do lote, podendo também passar o limite e a página por parâmetro. A requisição retorna os dados do(s) lote(s) caso seja especifícado um id do lote, caso não, retorna todos os lotes.

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

> **Atividade 4, Atividade 5, Atividade 6 e Atividade 7** :Interface responsável por cadastrar boletos dentro do Construtor de Vendas quando a parcela da reserva for da série ato ou sinal.

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
