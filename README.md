# Testes de Performance com K6

Repositório com testes de performance para a API do projeto [banco-api](https://github.com/ledapires/banco-api), utilizando a ferramenta [K6](https://k6.io/) e scripts escritos em JavaScript.

## 📌 Introdução

Este projeto tem como objetivo simular diferentes cargas e cenários de uso para a API do banco. Os testes são escritos com foco em modularidade, organização por contexto e reutilização de modelos de dados.

## 🚀 Tecnologias Utilizadas

- [K6](https://k6.io/) – Ferramenta de testes de carga e performance
- JavaScript – Linguagem utilizada para escrever os scripts
- Node.js – Para instalação de dependências e eventual automação
- Variáveis de ambiente para configuração dinâmica (ex: 'BASE_URL')
– Para flexibilidade na execução

## 📁 Estrutura do Repositório

```
banco-api-performance/
├── fixtures/       # Dados de entrada para os testes (ex: usuários, payloads)
├── helpers/        # Funções utilitários reutilizáveis para interação com a API
├── tests/          # Casos de teste organozados por módulo da API.
│   ├── contas.js
│   ├── transacoes.js
│   └── usuarios.js  
├──  utils /    # Funções utilitárias reutilizáveis
├── config/     # Arquivos de configuração de variáveis de ambiente
└── README.md
```

## 🧩 Objetivo de Cada Grupo de Arquivos

- **`fixtures/`**: Dados de entrada para os testes (ex: usuários, payloads).
- **`helps/`**: Funções utilitários reutilizáveis para interação com a API.
- **`tests/`**: Casos de teste organozados por módulo da API.
- **`utils/`**: Funções utilitárias reutilizáveis.
- **`config/`**: Arquivos de configuração de variáveis de ambiente.

## ⚙️ Instalação e Execução

1. Clone este repositório:

```bash
git clone https://github.com/ledapires/banco-api-performance.git
cd banco-api-performance
```

2. Configure as Variáveis de Ambiente

altere o arquivo `config.local.json` com base e define a URL base da API a ser testada:

```json
{
    "baseUrl" : "http://localhost:3000"
}
> Essas variáveis serão usada dinamicamente nos testes para montar as requisições.

```

## ▶️ Execução

Antes de rodar os testes, é necessário definir a variável de ambiente `BASE_URL` com a URL base da API que será testada. Exemplo:

```bash
export BASE_URL=http://localhost:3000
```

### Execução simples de um script

```bash
k6 run scripts/contas.js
```

### Execução com relatório em tempo real via Dashboard Web

```bash
k6 run tests/login.test.js
```
Certifique-se de passar a variável de ambiente `BASE_URL`, caso não esteja usando um `config.local.json` ou uma abordagem de carregamento automático: 

```bash
k6 run tests/cenário-principal.js -e BASE_URL=http://localhost:3000
```

### Acompanhamento em Tempo Real + Exportação de Relatório

Você pode ativar o modo dashboard do K6 e exportar o relatório ao final do teste:

```bash
K6_WEB_DASHBOARD=true \
K6_WEB_DASHBOARD_EXPORT=html-report.html \
k6 run tests/autenticacao/login.test.js \
-e BASE_URL=http://localhost:3000
```

Após a execução, o relatório estará salvo como `html-report.html`.
