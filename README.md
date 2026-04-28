# Projeto DimDim - Sistema de Gestão de Transações 💰

## 📋 Descrição
Este projeto é uma aplicação de gerenciamento financeiro desenvolvida para o **Checkpoint 2** da disciplina de **DevOps & Cloud**. A solução demonstra a integração de uma aplicação Python com um banco de dados relacional robusto (Oracle) utilizando containers Docker, focando em persistência e isolamento de rede.

## 👥 Equipe (Representantes)
* **João Pedro Pereira Camilo** | RM 562005
* **Lucas Matsubara Reis** | RM 565020
* **Pamella Christiny Chaves Brito** | RM 565206

---

## 🎥 Demonstração
O funcionamento completo desta solução, desde a subida dos containers até a persistência dos dados, pode ser visualizado no vídeo de entrega:
[Link do vídeo no YouTube](https://youtu.be/BW3W2jYLk1s)

---

## 🏗️ Arquitetura da Solução
A aplicação segue o modelo cliente-servidor em ambiente containerizado:
* **Aplicação:** Script Python que gerencia a lógica de negócio e interface via terminal.
* **Banco de Dados:** Instância de Oracle Database 21c Express Edition rodando em Docker.
* **Persistência:** Utilização de **Volumes Nomeados** para garantir que os dados não sejam perdidos ao reiniciar o container.
* **Rede:** Rede bridge isolada para comunicação segura entre os componentes.

---

## 🛠️ Configuração do Ambiente

### 1. Infraestrutura (Docker)
Para atender aos requisitos de infraestrutura, execute os comandos abaixo no terminal:

```bash
# Criar a rede isolada
docker network create rede-dimdim

# Criar o volume para persistência de dados
docker volume create volume-dados

# Executar o container Oracle (Com RM no nome e porta exposta)
docker run -d \
  --name db-rm565206 \
  -p 1521:1521 \
  -v volume-dados:/opt/oracle/oradata \
  --network rede-dimdim \
  -e ORACLE_PASSWORD=200806 \
  gvenzl/oracle-xe
2. Dependências do Python
Certifique-se de ter o Python 3.8+ instalado e instale o driver de conexão:

Bash

pip install oracledb
🏃 Execução
Certifique-se de que o container esteja com o status Up (o Oracle leva cerca de 1 min para iniciar).

Execute o script principal:

Bash

python3 app.py
Utilize as opções do menu para realizar o CRUD completo:

1 - Inserir Investimento

2 - Listar Investimentos

3 - Atualizar Investimento

4 - Deletar Investimento

📊 Estrutura de Dados
O sistema utiliza a tabela tb_dimdim criada automaticamente ou via script:

ID_INVESTIMENTO: Identificador único (Primary Key).

CLIENTE: Nome do investidor.

VALOR: Valor da transação.
