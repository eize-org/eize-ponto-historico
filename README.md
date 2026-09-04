# eize-ponto-historico

Frontend estático para visualizar o histórico de ponto do projeto [eize-ponto](https://github.com/eize-org/eize-ponto).

Este repositório contém apenas HTML e JavaScript puro. Ele lê um `token` da URL, faz uma requisição para a API (`eize-ponto-api-historico`) hospedada no PythonAnywhere e renderiza a tabela de histórico.

## Hospedagem

Projetado para rodar gratuitamente no **GitHub Pages**, sem backend próprio. A comunicação é feita 100% via API JSON externa.

## Como testar localmente

Basta abrir o arquivo `index.html` em qualquer navegador. Para ver um histórico real, adicione o parâmetro de token na URL, exemplo:

`file:///caminho/para/index.html?token=seu-token-aqui`
