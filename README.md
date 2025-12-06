# Projeto Santander Dev Week - ETL com Python e IA Generativa

## Resumo do Projeto

Este projeto apresenta um pipeline ETL (Extract, Transform, Load) desenvolvido em Python que integra uma API externa do Santander e utiliza IA generativa (API Gemini/Google Generative AI) para criar mensagens de marketing personalizadas a clientes bancários.

---

## Visão Detalhada do Pipeline

1. **Extração**: Lê IDs de clientes do arquivo `SDW2023.csv` e recupera os detalhes completos de cada usuário via requisições `GET` em uma API externa (`/users/{id}`).

2. **Transformação**: Com os dados do cliente, utiliza a API Gemini para criar, automaticamente, mensagens personalizadas que incentivam investimentos, mencionando o nome do usuário.

3. **Carga**: Atualiza os dados dos clientes via `PUT /users/{id}`, incluindo a mensagem criada no campo `news` do usuário.

---

## Estrutura dos Arquivos

- `SantanderDev.ipynb`: Notebook principal contendo todo o fluxo ETL e exemplos de uso das APIs.
- `SDW2023.csv`: Planilha simples, lista de IDs de clientes de exemplo utilizada pelo pipeline.
- `README.md`: Documentação do projeto.

---

## Dependências e Instalação

Instale os requisitos com:

```bash
pip install pandas requests google-generativeai python-dotenv
```

---

## Configuração da API Gemini

1. Gere sua chave em: https://aistudio.google.com/app/apikey
2. Substitua em `google_api_key` no notebook pelo valor da sua chave.
3. (Opcional) Para maior segurança, utilize um arquivo `.env` com a biblioteca `python-dotenv`.

---

## Resumo do Funcionamento

- Lê IDs do CSV (pandas);
- Busca e atualiza usuários pela API (requests);
- Gera mensagem de marketing usando IA Gemini (`google-generativeai`);
- Atualiza as mensagens do usuário pela API externa.

---

## API Externa — Endpoints Utilizados

- **GET `/users/{id}`**: Buscar dados do cliente.
- **POST `/users`**: Criar usuários de teste (exemplo Pyterson, Pip, Pep).
- **PUT `/users/{id}`**: Atualizar o cliente, incluindo a nova mensagem personalizada.

---

## Como Executar

1. Instale as dependências;
2. Abra `SantanderDev.ipynb` no Jupyter;
3. Execute as células sequencialmente para extrair dados, gerar mensagens com IA e atualizar a base.

---

## Observações Finais

- O projeto pode ser adaptado a outros setores/objetivos que exijam personalização de comunicações com clientes.
- Para produção, recomenda-se uso seguro das chaves e melhorias na manipulação de dados sensíveis.
- A API utilizada por definição não aceita que o id 1 atualize, logo foram atualizados somente os seguintes ids: 2, 3 e 4.

Fique à vontade para explorar, adaptar e sugerir melhorias!
