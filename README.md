# Validador de Certificados - Digital Ventura

Sistema de validação de autenticidade de certificados emitidos pela Digital Ventura. Utiliza uma arquitetura Serverless/Low-code para garantir alta disponibilidade e custo zero de infraestrutura.

## Arquitetura

O sistema opera no modelo de **Static Frontend + Backend-as-a-Service (BaaS)**. O frontend é hospedado no GitHub Pages e consome uma API RESTful construída sobre o Google Apps Script, que utiliza o Google Sheets como banco de dados relacional.

```mermaid
graph LR
    A[Usuário Final] -- 1. Insere Hash --> B(GitHub Pages / Frontend)
    B -- 2. Requisição GET (Fetch API) --> C{Google Apps Script / API}
    C -- 3. Query (Lookup) --> D[(Google Sheets / DB)]
    D -- 4. Retorna Dados --> C
    C -- 5. Retorna JSON Sanitizado --> B
    B -- 6. Renderiza Resultado --> A
