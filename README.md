# Projeto DimDim 💰 - Sistema de Gestão de Transações

Este projeto é uma aplicação de gerenciamento financeiro desenvolvida para o Checkpoint 2 da disciplina de DevOps & Cloud. A solução demonstra a integração de uma aplicação Python com um banco de dados relacional robusto (Oracle) utilizando containers Docker.

## 🏗️ Arquitetura da Solução

A aplicação segue o modelo cliente-servidor em ambiente containerizado:
* **Aplicação:** Script Python que gerencia a lógica de negócio e interface via terminal.
* **Banco de Dados:** Instância de Oracle Database 21c Express Edition.
* **Persistência:** Utilização de Volumes Docker para garantir que os dados não sejam perdidos ao reiniciar o container.
* **Rede:** Network isolada para comunicação segura entre os componentes.

## 🚀 Tecnologias

* Python 3.8+
* Oracle Database (Docker Image)
* Biblioteca `oracledb` (Thin Mode)
* Docker & Docker Compose

## 🛠️ Configuração do Ambiente

### 1. Infraestrutura (Docker)
Antes de iniciar a aplicação, é necessário subir o serviço de banco de dados:

```bash
# Criação da rede e volume
docker network create rede-dimdim
docker volume create volume-dados

# Execução do container Oracle
docker run -d \
  --name db-dimdim \
  -p 1521:1521 \
  -v volume-dados:/opt/oracle/oradata \
  --network rede-dimdim \
  -e ORACLE_PASSWORD=<SUA_SENHA_AQUI> \
  gvenzl/oracle-xe
2. Dependências do Python
Instale as bibliotecas necessárias utilizando o gerenciador de pacotes pip:

Bash

pip install oracledb
🏃 Execução
No arquivo app.py, configure as credenciais de acesso (user, password e dsn) conforme o seu ambiente local.

Inicie a aplicação:

Bash

python3 app.py
Utilize as opções do menu para realizar o CRUD completo (Criar, Listar, Atualizar e Deletar transações).

📊 Estrutura de Dados
O sistema utiliza uma tabela chamada tb_dimdim com a seguinte estrutura:

ID: Identificador único (Auto-incremento).

CLIENTE: Nome do investidor ou cliente.

VALOR: Valor monetário da transação.

🎥 Demonstração
O funcionamento completo desta solução, desde a subida dos containers até a persistência dos dados, pode ser visualizado no vídeo de entrega do projeto.

Desenvolvido por: Pamella Christiny Chaves Brito


---

### Dicas para manter a privacidade:
1.  **No Código:** No seu `app.py`, você pode deixar um comentário onde vai a senha: `password = "SUA_SENHA"` para que quem baixar saiba que precisa trocar.
2.  **Arquivo `.gitignore`:** Se você quiser ser ainda mais profissional, crie um arquivo chamado `.gitignore` e escreva o nome de qualquer arquivo que contenha senhas reais dentro dele. Assim, o Git nunca vai "subir" suas credenciais por acidente.

**Sua entrega está com uma cara excelente agora!** O CRUD está validado, o banco está persistindo e a documentação está protegida. Mais algum detalhe que queira ajustar?
