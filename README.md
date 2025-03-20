# Church

# Documentação da Arquitetura do CRM para Igrejas

## Visão Geral
O CRM para Igrejas é um sistema multi-tenant baseado em microserviços, projetado para a gestão financeira e de membros das igrejas. O sistema permite a administração de doações, eventos e patrimônio, garantindo segurança e escalabilidade.

## Tecnologias Utilizadas
- **Backend:** .NET Core
- **Frontend:** Flutter ou Angular
- **Banco de Dados:** SQL Server (dados estruturados) e MongoDB (logs, interações, eventos)
- **Mensageria:** RabbitMQ
- **Autenticação e Autorizacão:** JWT com RBAC (Role-Based Access Control)
- **Containerização e Deploy:** Docker e Kubernetes
- **Hospedagem:** AWS

## Arquitetura
A arquitetura do sistema é baseada nos seguintes componentes:

### Microserviços
1. **Identidade** - Gerencia autenticação e autorização.
2. **Membros** - Gerencia informações de membros e suas interações.
3. **Financeiro** - Controla doações, despesas e relatórios financeiros.
4. **Gateway API** - Orquestra chamadas entre os microserviços.

### Banco de Dados
- **SQL Server**: Utilizado para armazenar dados estruturados das igrejas, como membros, contribuições e eventos.
- **MongoDB**: Utilizado para armazenar logs, interações e eventos do sistema.

### Multi-Tenancy
Cada igreja terá seus dados separados por meio do **ChurchId**, que estará embutido no token JWT do usuário autenticado. Isso garante isolamento lógico dos dados sem necessidade de bancos de dados separados para cada igreja.

### Comunicação
- **RabbitMQ**: Utilizado para comunicação assíncrona entre os microserviços, garantindo escalabilidade e resiliência.

## Execução Local
Para rodar o projeto localmente:

### Requisitos
- Docker e Docker Compose instalados.
- .NET SDK instalado.
- SQL Server e MongoDB em contêineres ou instalados localmente.

### Passos
1. Clone o repositório:
   ```bash
   git clone https://github.com/seu-repositorio/crm-igrejas.git
   cd crm-igrejas
   ```
2. Configure as variáveis de ambiente no arquivo `.env`.
3. Suba os contêineres:
   ```bash
   docker-compose up -d
   ```
4. Execute os microserviços manualmente ou via Docker.
5. Acesse o Swagger para testar a API em `http://localhost:{PORT}/swagger`.

## Documentação da API
A documentação da API está disponível via Swagger. Para acessá-la:
1. Execute o microserviço desejado.
2. Acesse `http://localhost:{PORT}/swagger` para visualizar e testar os endpoints.

## Considerações Finais
Essa arquitetura foi projetada para garantir modularidade, escalabilidade e segurança. Melhorias futuras incluirão integração com bancos para transações Pix e suporte a mais funcionalidades de gestão e automação.

