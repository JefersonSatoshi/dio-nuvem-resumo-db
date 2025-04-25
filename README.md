
# Desafio Azure SQL Database

## Objetivo

Este desafio visa a criação e configuração de um banco de dados SQL no **Azure** para prática e aprendizado. O banco de dados foi configurado com um servidor SQL básico utilizando autenticação do **Microsoft Entra** (Azure Active Directory) e configurações de computação e armazenamento adequadas para fins de desenvolvimento.

## Tecnologias Utilizadas

- **Azure SQL Database**
- **Azure Active Directory (Microsoft Entra)**

## Banco de Dados na Nuvem

Os bancos de dados na nuvem, como o **Azure SQL Database**, oferecem uma série de vantagens em relação aos bancos de dados tradicionais on-premises. Entre as principais vantagens, destacam-se:

- **Escalabilidade**: A capacidade de ajustar os recursos de computação e armazenamento conforme a necessidade, sem a necessidade de hardware físico.
- **Alta Disponibilidade**: Os bancos de dados em nuvem geralmente oferecem mecanismos automáticos de backup e failover, garantindo maior disponibilidade e resiliência.
- **Gestão Simplificada**: Com o gerenciamento do banco de dados na nuvem, não há necessidade de lidar com infraestrutura, patches, ou configurações complexas.
- **Segurança**: Com autenticação avançada, criptografia e compliance, os bancos de dados na nuvem oferecem segurança de alto nível.
- **Custos sob Demanda**: Você paga somente pelos recursos consumidos, o que pode ser mais econômico do que manter uma infraestrutura própria.



## Configuração do Banco de Dados

### Passos para Criação do Banco de Dados

1. **Grupo de Recursos**: `vm-dio-lab_group`  
   O grupo de recursos foi utilizado para organizar todos os recursos relacionados ao banco de dados.

2. **Servidor SQL**:
   - Nome do Servidor: `db-dio-sql-lab`
   - Localização: **Brazil South**
   - Método de Autenticação: **Microsoft Entra** (Autenticação única usando o Microsoft Entra)
   - Administrador: O administrador foi configurado utilizando um usuário do **Microsoft Entra**.

3. **Banco de Dados**:
   - Nome do Banco de Dados: `db-dio-lab`
   - Configuração de Computação + Armazenamento: **Uso Geral - Sem servidor** (1 vCore, 1 GB de armazenamento, zona redundante desabilitada)
   - Redundância de Backup: **Armazenamento de backup com redundância local**

4. **Configuração de Rede e Segurança**:
   - A opção de **ponto de extremidade privado** não foi ativada.
   - **Transparent Data Encryption** foi habilitado com chave gerenciada pelo serviço.

5. **Configuração de Rede**:
   - A opção **Permitir que serviços e recursos do Azure acessem este servidor** foi configurada como **não**.
   - A **versão mínima do TLS** foi configurada como **1.2** para maior segurança.

6. **Redundância de Backup**:
   - Foi configurado o **armazenamento de backup com redundância local**.

## Como Conectar ao Banco de Dados

Para conectar ao banco de dados, utilize as credenciais de administrador configuradas durante o processo de criação do banco. A autenticação será realizada através do **Microsoft Entra**.

### Exemplo de String de Conexão:

```plaintext
Server=seu-servidor.database.windows.net;Database=seu-banco-de-dados;Authentication=Active Directory Interactive;Encrypt=True;TrustServerCertificate=False;
```

## Testando a Conexão

Para validar se o banco foi criado corretamente e está acessível, recomenda-se utilizar uma ferramenta de gerenciamento como o **Azure Data Studio** ou o **SQL Server Management Studio (SSMS)**.

### Passos:

1. Abra o **Azure Data Studio**.
2. Clique em **Nova Conexão**.
3. Insira os dados da conexão:
   - **Servidor**: `seu-servidor.database.windows.net`
   - **Banco de Dados**: `db-dio-lab`
   - **Tipo de Autenticação**: Active Directory - Interactive
4. Clique em **Conectar** e aguarde a verificação.

Se a conexão for bem-sucedida, o banco está pronto para uso!

## Conclusão

Este banco de dados foi configurado para fins de prática e aprendizado no **Azure SQL Database**, permitindo que exploremos conceitos de configuração de banco de dados na nuvem, autenticação com **Microsoft Entra**, e outras configurações do Azure.
