### Passo a Passo para Localizar Serviços por Categoria

#### 1. Acesse o Portal do Azure 🌐
- Faça login no [Portal do Azure](https://portal.azure.com).

#### 2. Vá para a Seção "Criar um Recurso" 🛠️
- No painel principal, clique em **"Criar um recurso"**. 
- Você será direcionado para a galeria de recursos onde poderá navegar por categorias de serviços.

#### 3. Navegue Pelas Categorias de Serviço 📂
- No menu à esquerda, você verá várias categorias como:
  - **Compute (Computação)**: Para encontrar serviços como Máquinas Virtuais, Funções do Azure, etc.
  - **Networking (Rede)**: Para localizar serviços como Redes Virtuais, Gateways de Aplicações, Balanceadores de Carga, etc.
  - **Storage (Armazenamento)**: Para encontrar serviços como Contas de Armazenamento, Azure Blob Storage, Discos Gerenciados, etc.
  - **Databases (Banco de Dados)**: Para serviços como Azure SQL Database, Cosmos DB, Azure Database for MySQL, etc.
  - **AI + Machine Learning (Inteligência Artificial e Aprendizado de Máquina)**: Para serviços como Azure Machine Learning, Cognitive Services, etc.
  - **DevOps**: Para ferramentas e serviços de CI/CD como Azure DevOps, Repos, Pipelines, etc.

#### 4. Selecione a Categoria e o Serviço 🔍
- Clique na categoria desejada para visualizar todos os serviços disponíveis dentro dela.
- Clique no serviço que você quer explorar ou implementar para ver detalhes adicionais, como opções de configuração, preços e documentação.

#### 5. Utilize a Barra de Pesquisa se Necessário 🔎
- Caso tenha dificuldade para encontrar um serviço específico, utilize a barra de pesquisa no topo da página. Digite o nome do serviço ou palavras-chave relacionadas, e o portal do Azure exibirá resultados relevantes.

### Exemplos de Serviços por Categoria

- **Computação**:
  - Máquinas Virtuais (Virtual Machines)
  - Azure Kubernetes Service (AKS)
  - App Service (Hospedagem de Aplicações Web)
- **Rede**:
  - Redes Virtuais (Virtual Networks)
  - Firewall do Azure
  - VPN Gateway
- **Armazenamento**:
  - Azure Blob Storage (Armazenamento de Objetos)
  - Azure File Storage (Compartilhamento de Arquivos)
  - Discos Gerenciados
- **Banco de Dados**:
  - Azure SQL Database
  - Azure Database for PostgreSQL
  - Cosmos DB

### Alternativa Usando a Azure CLI

Se preferir usar a Azure CLI para listar serviços por categoria, você pode usar o comando abaixo para listar os recursos disponíveis:

```bash
# Listar todos os serviços disponíveis no Azure
az provider list --query "[].namespace" -o table
```

Ou listar os serviços de um determinado grupo de recursos:

```bash
# Listar serviços dentro de um grupo específico
az resource list --resource-group <nome-do-grupo>
```
---
