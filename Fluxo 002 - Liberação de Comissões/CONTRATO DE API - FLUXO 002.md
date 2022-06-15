<p align="center">
  <a href="https://onsac.com/">
    <img src="https://github.com/onsac/Prestes/blob/main/Imagens/Projeto%20OnSAC-Prestes.png" >
  </a>
</p>

<h3 align="center">Contrato de API</h3>

<p align="center">
  Fluxo 002 - Liberação de Comissões
  </p>
  
  
 ## Workflow do Fluxo 002 
  <p align="center">
    <img src="https://github.com/onsac/Prestes/blob/main/Fluxo%20002%20-%20Libera%C3%A7%C3%A3o%20de%20Comiss%C3%B5es/Desenho%20do%20Fluxo%20002.pptx.png" >
</p>


## APIs – SIENGE

* **Atividade 3** Inserção do título no Sienge com base em nota fiscal eletrônica recebida.
```sh 
  URL PROD: https://api.sienge.com.br/produtoeinovacao/public/api/v1/eletronic-invoice-bills/ 
```
* **Atividade 17** Atualiza o título no Sienge.
```sh 
  URL PROD: https://api.sienge.com.br/produtoeinovacao/public/api/v1/bills/{billId}
```
* **Atividade 18 e Atividade 19** Inserção do título no Sienge.
```sh 
  URL PROD: https://api.sienge.com.br/produtoeinovacao/public/api/v1/bills/ 
```
## APIs – CVCRM

* **Atividade 2** Essa interface trará informações pertinentes referente a todos os empreendimentos ativos em seu CV.
```sh 
  URL PROD: https://integracao.cvcrm.com.br/api/v1/prestes/empreendimento
```
* **Atividade 3** Essa integração coleta informações de requisições realizadas por sistemas legados e verifica se o dado inserido no campo documento existe ou não no Construtor de Vendas. Se já existir um corretor cadastrado com o mesmo documento, essa API irá atualizar os dados solicitados na requisição, se não irá cadastrá-los. Obs: Para esta verificação, o documento CPF deve ser válido. Somente será aceito um cadastro por CPF.
```sh 
  URL PROD: https://integracao.cvcrm.com.br/api/v1/prestes/corretor
```
* **Atividade 4** A interface viabiliza a consulta das parcelas de pagamento das comissões retornando os dados, seus pagador e seu benficiário.

```sh
  URL PROD: https://integracao.cvcrm.com.br/api/v1/prestes/pagamentos/comissao
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
> **Atividade 2** Essa interface trará informações pertinentes referente a todos os empreendimentos ativos em seu CV.

```diff
+ API GET: https://integracao.cvcrm.com.br/api/v1/prestes/empreendimento
```

```sh
{
  "idempreendimento": "520",
  "codigointerno": "99999",
  "nome": "Reserva Exemplo",
  "matricula": "68045",
  "cidade": "Aracaju",
  "estado": "Sergipe",
  "endereco": "Av. Gen. Djenal Tavares de Queroz, Aracaju - SE, 49045-423, Brasil",
  "periodo_venda_inicio": "2019-05-18 00:00:00",
  "area_construida": "23373.6200",
  "area_privativa": "16705.6600",
  "idempreendimento_int": "9",
  "nome_empresa": "NOME DA EMPRESA LTDA",
  "razao_social_empesa": "RAZAO SOCIAL DA EMPRESA",
  "cnpj_empesa": "0123451234512",
  "endereco_empresa": "ENDERECO DA EMPRESA 999",
  "integrado": "S",
  "logo": "http://cv.cvcrm.com.br/api/get/imagens/empreendimentos_logo/x/x/20200811143500_5f32d6c47e24a.jpg",
  "latitude": "-10.987654321",
  "longitude": "-37.987654321",
  "titulo": "Exemplo de título",
  "descricao": "Descrição exemplo",
  "etapas": {
    "idetapa": "9501",
    "idempreendimento": "520",
    "nome": "1ª etapa",
    "data_cad": "2020-08-04 17:08:57",
    "blocos": [
      {
        "idbloco": "2576",
        "idetapa": "9501",
        "nome": "Laguna",
        "data_cad": "2020-08-04 17:08:57",
        "unidades": [
          {
            "nome": "001",
            "area_privativa": "122.00",
            "idunidade": "12345",
            "idbloco": "2576",
            "vagas_garagem": "1",
            "andar": "7",
            "area_comum": "33.39",
            "posicao": "Leste",
            "tipologia": "3 suites com terraço gourmet",
            "valor": "9999.99",
            "situacao": [
              {
                "vendida": "1332",
                "vendida_idsituacao": "3",
                "idmotivo": "1",
                "tipo": {
                  "id": "1",
                  "nome": "Garagem"
                },
                "situacao_para_venda": 1,
                "situacao_mapa_disponibilidade": 1,
                "possui_reserva_solicitacao_distrato": "N"
              }
            ]
          }
        ]
      }
    ]
  },
  "plantas": {
    "idplanta": "1",
    "nome": "Planta 11",
    "especificacoes": "Planta 3 quartos com cozinha americana e sala de estar.",
    "data_cad": "2020-08-04 17:08:57",
    "img_planta_servidor": "http://cv.cvcrm.com.br/api/get/imagens/empreendimentos_img_planta/x/x/20200811144935_5f32da2fe07ec.jpg"
  },
  "caracteristicas": [
    {
      "idcaracteristica": "3",
      "nome": "3 quartos"
    }
  ],
  "tabela": [
    {
      "idtabela": "384",
      "nome": "Tabela financiamento",
      "forma": "E",
      "tipo": "Tabela com Financiamento",
      "data_vigencia_de": "2021-03-01",
      "data_vigencia_ate": "2022-12-01",
      "aprovado": "S",
      "valor_metro": "999.99"
    }
  ],
  "materiais_campanha": [
    {
      "idarquivo": "132",
      "nome": "fachadasite-20190520093805.jpg",
      "servidor": "20200811145156_5f32dabc92758.jpg",
      "tipo": "image/jpeg",
      "tamanho": "211221",
      "titulo": "Piscina com Deck",
      "descricao": "Piscina com Deck",
      "arquivo": "http://cv.cvcrm.com.br/api/get/imagens/empreendimentos_material_campanha/x/x/20200811145156_5f32dabc92704.jpg"
    }
  ]
}
```
> **Atividade 3** Essa integração coleta informações de requisições realizadas por sistemas legados e verifica se o dado inserido no campo documento existe ou não no Construtor de Vendas. Se já existir um corretor cadastrado com o mesmo documento, essa API irá atualizar os dados solicitados na requisição, se não irá cadastrá-los. Obs: Para esta verificação, o documento CPF deve ser válido. Somente será aceito um cadastro por CPF.

```diff
+ API POST: https://integracao.cvcrm.com.br/api/v1/prestes/corretor
```

```sh
{
  "idcorretor_int": "34437",
  "nome": "José Aberlado",
  "sexo": "M",
  "data_nasc": "1993-08-11",
  "telefone": "79999995541",
  "cep": "49042-270",
  "logradouro": "Rua",
  "endereco": "Rua A-1",
  "bairro": "Atalaia",
  "numero": "12345",
  "complemento": "Próximo ao hospital",
  "cidade": "12345678000123",
  "estado": "12345678000123",
  "creci": "123456",
  "notificar_novos_leads": "S",
  "tipo_conta": "C",
  "banco": "Banco XYZ",
  "nome_agencia": "Ag. teste",
  "numero_agencia": "25841",
  "digito_agencia": "1",
  "numero_conta": "87451",
  "digito_conta": "3",
  "cpf": "31620513048",
  "cpf_favorecido": "31620513048",
  "nome_favorecido": "José Abelardo",
  "idimobiliaria_int": "5",
  "email": "exemplo@email.com",
  "ativo_login": "S",
  "remover": "0"
}

```

> **Atividade 4** A interface viabiliza a consulta das parcelas de pagamento das comissões retornando os dados, seus pagador e seu benficiário.

```diff
+ API GET: https://integracao.cvcrm.com.br/api/v1/prestes/pagamentos/comissao
```

```sh
{
  "total": 12340,
  "limite": "5",
  "pagamentos": [
    {
      "vencimento": "01/01/2022",
      "valorTotal": "121,12",
      "pagador": [
        {
          "nome": "carlos eduardo",
          "documento": "123456789",
          "telefone": "(79)99999-8888",
          "email": "mail@provedor.com.br",
          "logradouro": "avenida",
          "numero": "12345",
          "complemento": "casa 1",
          "bairro": "nome do bairro",
          "cidade": "nome da cidade",
          "estado": "nome do estado"
        }
      ],
      "beneficiario": [
        {
          "nome": "carlos eduardo",
          "documento": "123456789",
          "telefone": "(79)99999-8888",
          "email": "mail@provedor.com.br",
          "logradouro": "avenida",
          "numero": "12345",
          "complemento": "casa 1",
          "bairro": "nome do bairro",
          "cidade": "nome da cidade",
          "estado": "nome do estado"
        }
      ],
      "parcelas": [
        {
          "idpagamento": 123,
          "valor": "11.01"
        }
      ]
    }
  ]
}
```
