# Banco API Performance Tests (k6 + JavaScript)

## Introdução
Este repositório contém testes de performance para a API do projeto Banco, utilizando a ferramenta [Grafana k6](http://k6.io) e escritos em  JavaScript. 

Repositório: 
https://github.com/esbietta/banco-api-performance

## Objetivo

O objetivo é validar a estabilidade, desempenho e escalabilidade dos endpoints sob diferentes cargas.Os testes são escritos com foco em modularidade, organização por contexto e reutilização de modelos de dados.

Uma variável de ambiente obrigatória deve ser definida para execução dos testes:

- BASE_URL: URL base da API a ser testada

---

## Tecnologias Utilizadas
- JavaScript (ES6+)
- k6 (ferramenta de testes de performance)
- [GJSON] para extração de dados em resposta JSON
- Node.js (ferramenta para suporte e organização)

---

## Estrutura do Repositório
```
banco-api-performance/
│
├── config/             # Arquio de configuração de variáveis de ambiente
├── fixtures/            # Dados de entrada para os testes
├── helpers/           # Funções de acesso aos endpoints
├── test/              # Scripts principais de testes
├── utils/              # Funções auxiliares
└── README.md            # Este documento
```

---

## Objetivo de Cada Grupo de Arquivos

- **config/**: Define configuração de variáveis de ambiente
- **helpers/**: Funções utilitárias reutilizáveis para iteração com API
- **test/**: Contém os arquivos principais que executam os testes   
- **fixtures/**: Armazena dados utilizados nos testes
- **utils/**: Funções reutilizáveis como validações e helpers

---

## Modo de Instalação
1. Instale o k6:
   https://k6.io/docs/getting-started/installation/

2. Instale Node.js:
   https://nodejs.org/

3. Clone o repositório:
```
git clone https://github.com/esbietta/banco-api-performance.git
cd banco-api-performance
```

---

## Modo de Execução
Antes de executar, defina a variável de ambiente BASE_URL:

Altere o arquivo `config.local.json` e defina a URL base da API a ser testada:

```json
{  
        "baseUrl": "http://localhost:3000"
}
```
Essas variáveis serão usadas dinamicamente nos testes para montar as requisições.

```bash
k6 run test/login.test.js
```
Certifique-se de passar a variável de ambiente `BASE_URL`, caso não esteja usando um
`config.local.json` ou uma abordagem de carregamento automáatico:

 ```bash
k6 run .\test\login.test.js -e BASE_URL=http://localhost:3000
```

---

## Execução  em Tempo Real e Exportação de Relátorios

```bash
K6_WEB_DASHBOARD=true \
K6_WEB_DASHBOARD_EXPORT=html-report.html \
k6 run test/login.test.js\
-e BASE_URL=http://localhost:3000

```

Isso irá gerar um relatório visual completo do teste ao final da execução como
`html-report.html`
