# Documentação: Gerenciando Políticas em Acessos na Azure

## Índice
1. **Introdução**
2. **Conceitos Básicos**
   - Funções do Controle de Acesso Baseado em Funções (RBAC)
   - Azure Policy vs. RBAC
   - Escopo de Aplicação
3. **Criação e Gerenciamento de Políticas**
   - Criando uma Política no Azure
   - Definindo Iniciativas
   - Atribuindo Políticas a Grupos de Recursos ou Assinaturas
   - Exceções e Condicionais em Políticas
4. **Monitoramento e Conformidade**
   - Avaliação de Conformidade
   - Relatórios de Não-Conformidade
   - Remediação Automática
5. **Melhores Práticas para Gerenciamento de Políticas**
   - Segregação de Funções e Acessos
   - Aplicação de Políticas de Segurança e Governança
   - Automação de Processos de Conformidade
6. **Exemplos Práticos de Uso de Políticas no Azure**
   - Política para Restringir Localizações de Recursos
   - Política para Garantir Tags Obrigatórias
   - Política para Restringir Tamanho de Máquinas Virtuais
7. **Conclusão**

---

## 1. Introdução

O gerenciamento de acessos e políticas no Microsoft Azure é essencial para garantir segurança, conformidade e governança eficaz em ambientes de nuvem. Com uma combinação de **RBAC (Role-Based Access Control)** e **Azure Policy**, as organizações podem controlar quem tem acesso a quais recursos e definir regras que regem como esses recursos são configurados e utilizados. Esta documentação fornece uma visão geral de como gerenciar políticas de acesso na Azure, configurar políticas personalizadas e garantir a conformidade com as regulamentações internas e externas.

---

## 2. Conceitos Básicos

### Funções do Controle de Acesso Baseado em Funções (RBAC)
O **Azure RBAC** é usado para gerenciar permissões de usuários sobre os recursos. Ele define quem pode fazer o quê dentro de uma assinatura ou grupo de recursos. Funções comuns incluem:
- **Leitor** (acesso apenas de leitura)
- **Colaborador** (acesso para modificar, mas não para conceder permissões)
- **Proprietário** (controle total, incluindo gerenciamento de permissões)

### Azure Policy vs. RBAC
Embora o **RBAC** seja usado para controlar o acesso aos recursos, o **Azure Policy** é usado para impor configurações e práticas operacionais nos recursos. Por exemplo, enquanto o RBAC pode permitir que um usuário crie uma máquina virtual, o Azure Policy pode restringir a criação dessa máquina virtual a regiões específicas ou tamanhos de instâncias permitidos.

### Escopo de Aplicação
Tanto o RBAC quanto o Azure Policy podem ser aplicados em diferentes níveis de escopo:
- **Assinatura**: Afeta todos os recursos dentro de uma assinatura.
- **Grupo de Recursos**: Afeta todos os recursos dentro de um grupo específico.
- **Recurso Individual**: Aplicável a recursos específicos, como VMs, armazenamento, etc.

---

## 3. Criação e Gerenciamento de Políticas

### Criando uma Política no Azure
Para criar uma política no Azure, siga estes passos:
1. Acesse o **Azure Policy** no portal da Azure.
2. Selecione **Definições** e, em seguida, **Criar Definição de Política**.
3. Especifique o escopo, defina as regras no formato JSON e escolha as ações desejadas (permitir, negar, auditar, etc.).
4. Salve a política e atribua-a a uma assinatura, grupo de recursos ou recurso individual.

### Definindo Iniciativas
Uma **Iniciativa** no Azure é um conjunto de políticas agrupadas para serem aplicadas em conjunto. Elas permitem gerenciar e monitorar várias políticas de uma só vez, simplificando a governança. Exemplo: uma iniciativa de segurança pode incluir políticas para criptografia obrigatória e monitoramento de atividade de login.

### Atribuindo Políticas a Grupos de Recursos ou Assinaturas
Após criar uma política ou iniciativa, você pode atribuí-la a diferentes escopos:
1. No portal do Azure, acesse a política que deseja atribuir.
2. Escolha **Atribuir política** e selecione o escopo (assinatura, grupo de recursos, etc.).
3. Configure parâmetros adicionais, como exceções e condições.

### Exceções e Condicionais em Políticas
Você pode configurar **exceções** a determinadas políticas para permitir mais flexibilidade em cenários específicos. Por exemplo, uma política que exige que todos os recursos tenham tags pode ter uma exceção para um grupo de recursos temporário.

---

## 4. Monitoramento e Conformidade

### Avaliação de Conformidade
O **Azure Policy** realiza avaliações contínuas para verificar se os recursos estão em conformidade com as políticas atribuídas. Os resultados da avaliação de conformidade podem ser visualizados no portal da Azure e indicam quais recursos estão fora de conformidade.

### Relatórios de Não-Conformidade
As organizações podem gerar relatórios detalhados de **não-conformidade**, que indicam quais recursos estão violando as políticas e precisam de intervenção.

### Remediação Automática
O Azure permite configurar **remediações automáticas** para corrigir automaticamente recursos fora de conformidade. Por exemplo, se uma política exigir que todos os recursos tenham uma tag "departamento", o Azure pode adicionar automaticamente essa tag a recursos que não a possuem.

---

## 5. Melhores Práticas para Gerenciamento de Políticas

### Segregação de Funções e Acessos
Utilize o **RBAC** para aplicar a segregação de funções de acordo com as responsabilidades do usuário. Apenas administradores e operadores qualificados devem ter permissões elevadas.

### Aplicação de Políticas de Segurança e Governança
Implemente políticas para garantir que as melhores práticas de segurança e governança sejam seguidas, como o uso obrigatório de criptografia, backups e regras de firewall.

### Automação de Processos de Conformidade
Automatize a aplicação de políticas e monitoramento para garantir conformidade contínua, especialmente em grandes ambientes com muitos recursos.

---

## 6. Exemplos Práticos de Uso de Políticas no Azure

### Política para Restringir Localizações de Recursos
Uma política pode ser criada para garantir que novos recursos sejam implantados apenas em regiões específicas (por exemplo, "East US" ou "West Europe").

### Política para Garantir Tags Obrigatórias
Essa política garante que todos os recursos tenham tags específicas (como "departamento" ou "projeto"), o que facilita o rastreamento e a cobrança de custos.

### Política para Restringir Tamanho de Máquinas Virtuais
Você pode aplicar uma política que restringe a criação de VMs apenas a determinados tamanhos ou tipos, controlando custos e garantindo conformidade com as necessidades de desempenho.

---

## 7. Conclusão

Gerenciar políticas e acessos na Azure é um aspecto crítico da governança em nuvem. Com o uso combinado de **RBAC** para controlar permissões e **Azure Policy** para impor práticas operacionais e de segurança, as organizações podem garantir a conformidade, minimizar riscos e otimizar o gerenciamento de seus recursos. Ao seguir as melhores práticas descritas nesta documentação, você poderá aplicar políticas consistentes e eficazes em seu ambiente de nuvem Azure.