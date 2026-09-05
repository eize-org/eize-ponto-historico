# eize-ponto-historico

Este é o repositório responsável por exibir a interface pública do histórico de horas trabalhadas do projeto **[eize-ponto](https://github.com/eize-org/eize-ponto)**. 

Ele é uma página 100% estática (HTML, CSS, JS puros com Bootstrap 5), hospedada gratuitamente no **GitHub Pages**.

## ☁️ Arquitetura (GitOps / Serverless)

Diferente de sistemas web tradicionais, este frontend não consome dados de uma API ou banco de dados convencional (não há Python, Node, MySQL, etc., rodando por trás).

Nós utilizamos uma arquitetura baseada em **arquivos estáticos**:
1. O sistema principal (`eize-ponto`) rodando localmente na biblioteca gera um arquivo JSON consolidado cada vez que um ponto é batido.
2. Através da API REST do próprio GitHub, o sistema principal faz um "commit automático" enviando esse arquivo para a pasta `api/` deste repositório (ex: `api/TOKEN123.json`).
3. O JavaScript desta página (o arquivo `index.html`) apenas lê a URL, extrai o token (`?token=TOKEN123`) e faz um `fetch()` diretamente nesse arquivo JSON estático local.

Essa abordagem garante que o sistema suporte infinitos acessos, não tenha custo de manutenção de banco de dados e nunca saia do ar por expiração de servidores gratuitos.

## 🚀 Como acessar

O bolsista não precisa de usuário ou senha, apenas do link pessoal intransferível gerado pelo sistema principal, que deve ser no formato:

```
https://eize-org.github.io/eize-ponto-historico/?token=<TOKEN_DO_BOLSISTA>
```

## 🛠️ Como rodar e testar localmente

Se você quiser modificar o design ou testar o frontend localmente no seu computador, não basta abrir o `index.html` com dois cliques (o protocolo `file://` bloqueia o `fetch()` por segurança CORS).

Você precisa subir um servidor local simples. Se tiver o Python instalado, basta abrir o terminal na pasta deste repositório e rodar:

```bash
python -m http.server 8080
```
Em seguida, acesse no navegador: `http://localhost:8080/?token=COLOQUE_UM_TOKEN_AQUI` (certifique-se de que existe um arquivo com esse nome na pasta `api/`).
