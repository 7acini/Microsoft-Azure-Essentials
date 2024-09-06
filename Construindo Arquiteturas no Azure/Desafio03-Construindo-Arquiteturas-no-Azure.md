### Criação de Infraestrutura no Azure: Passo a Passo no Portal Web e via Azure CLI

A seguir, um guia passo a passo para criar infraestrutura no Azure, incluindo Grupo de Recursos, Rede Virtual e Regras de Segurança, tanto pelo Portal Web quanto pela Azure CLI.

## Configuração Usando o Portal do Azure

### 1. Portal do Azure 🌑

- Faça login no [Portal do Azure](https://portal.azure.com).

### 2. Criação do Grupo de Recursos 📁

1. No painel do Azure, pesquise por “Grupos de Recursos” ou “Resource Groups”.
2. Clique em **"Criar"** para iniciar a criação de um novo grupo de recursos.
3. Preencha os seguintes detalhes:
   - **Nome do Grupo de Recursos**: Nomeie o grupo de forma que ele seja facilmente identificado.
   - **Região**: Escolha a região para o grupo. Recomenda-se usar a mesma região para todos os recursos relacionados para reduzir latência e custos.
4. Clique em **"Revisar + Criar"** e depois em **"Criar"** para finalizar.

### 3. Criação da Rede Virtual 🌒

1. No painel do Azure, pesquise por “Redes Virtuais” ou “Virtual Networks”.
2. Clique em **"Criar"** para configurar uma nova rede virtual.
3. Preencha os detalhes:
   - **Nome da Rede Virtual**: Escolha um nome para identificar a rede.
   - **Grupo de Recursos**: Selecione o grupo de recursos criado anteriormente.
   - **Região**: Selecione a mesma região do grupo de recursos.
   - **Endereço IP**: Defina o intervalo de endereços IP para a rede.
4. Clique em **"Revisar + Criar"** e depois em **"Criar"** para finalizar.

### 4. Boa Prática em Segurança da Informação na Azure

#### Criação de Regras no Grupo de Recursos 🏴

1. **Acesse o Grupo de Recursos**:
   - No painel do Azure, busque por “Grupos de Recursos” e selecione o grupo que você deseja configurar.

2. **Configuração de Regras de Segurança**:
   - **Grupo de Segurança de Rede (NSG)**: Configure regras para controlar o tráfego de entrada e saída, baseadas em IPs, portas e protocolos.
   - **Regras de Acesso**: Defina permissões e políticas para usuários e serviços, garantindo que apenas os autorizados possam acessar os recursos.

3. **Monitoramento e Alertas**:
   - Configure alertas para monitorar atividades e detectar violações de segurança. Defina notificações para ações suspeitas.

4. **Revisão e Atualização**:
   - Realize revisões periódicas das regras e políticas para garantir conformidade com as melhores práticas.

---

## Configuração Usando Azure CLI

### 1. Faça Login no Azure CLI

Certifique-se de que o Azure CLI está instalado e atualizado. Abra o terminal e faça login:

```bash
az login
```

### 2. Criação do Grupo de Recursos

```bash
az group create --name MeuGrupoDeRecursos --location eastus
```

### 3. Criação da Rede Virtual

```bash
az network vnet create \
  --name MinhaRedeVirtual \
  --resource-group MeuGrupoDeRecursos \
  --address-prefix 10.0.0.0/16 \
  --location eastus
```

### 4. Criação de um Grupo de Segurança de Rede (NSG)

```bash
az network nsg create \
  --resource-group MeuGrupoDeRecursos \
  --name MeuGrupoDeSegurancaRede \
  --location eastus
```

### 5. Configuração de Regras de Segurança no NSG

Adicione uma regra de segurança para permitir o tráfego HTTP na porta 80:

```bash
az network nsg rule create \
  --resource-group MeuGrupoDeRecursos \
  --nsg-name MeuGrupoDeSegurancaRede \
  --name PermitirHTTP \
  --protocol Tcp \
  --direction Inbound \
  --priority 1000 \
  --source-address-prefix '*' \
  --source-port-range '*' \
  --destination-address-prefix '*' \
  --destination-port-range 80 \
  --access Allow
```

### 6. Configuração de Monitoramento e Alertas

Defina uma regra de alerta para monitorar o consumo de recursos:

```bash
az monitor metrics alert create \
  --name AlertaUsoAltoCPU \
  --resource-group MeuGrupoDeRecursos \
  --scopes /subscriptions/{SubscriptionID}/resourceGroups/MeuGrupoDeRecursos/providers/Microsoft.Compute/virtualMachines/MinhaVM \
  --condition "avg Percentage CPU > 80" \
  --description "Alerta quando a CPU estiver acima de 80%"
```

Substitua `{SubscriptionID}` pelo ID da sua assinatura do Azure.