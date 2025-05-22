# Matriz de Rastreabilidade - Sistema de Agendamento de Viagens

## Informações do Projeto

**Sistema:** Plataforma de Agendamento de Viagens  
**Objetivo:** Rastrear a relação entre requisitos funcionais, componentes do sistema, diagramas e funcionalidades implementadas  
**Data:** Maio 2025

## Legenda

- ✓ = Implementado/Relacionado
- P = Parcialmente Relacionado
- (vazio) = Não Relacionado

## Matriz de Rastreabilidade: Requisitos vs Componentes do Sistema

| Requisitos Funcionais | Formulário Digital | Módulo de Aprovação | Sistema de Notificações | Calendário Interno | Calendário Público | Validação de Horários | Interface do Gestor | Seleção de Motorista/Veículo | API de E-mail | Banco de Dados |
|----------------------|-------------------|-------------------|------------------------|-------------------|-------------------|---------------------|-------------------|------------------------------|---------------|----------------|
| **RF01 - Cadastro de Solicitações** | ✓ | P | | | | ✓ | | | | ✓ |
| **RF02 - Validação Automática de Horários** | P | | | | | ✓ | | | | ✓ |
| **RF03 - Aprovação/Negação pelo Gestor** | | ✓ | P | | | | ✓ | ✓ | | ✓ |
| **RF04 - Atribuição de Motorista e Veículo** | | ✓ | | | | | ✓ | ✓ | | ✓ |
| **RF05 - Envio de Notificações por E-mail** | | P | ✓ | | | | | | ✓ | ✓ |
| **RF06 - Armazenamento de Viagens** | | | | ✓ | ✓ | | | | | ✓ |
| **RF07 - Visualização em Calendários** | | | | ✓ | ✓ | | P | | | ✓ |

## Matriz de Rastreabilidade: Funcionalidades vs Diagramas

| Funcionalidades | Diagrama de Caso de Uso | Diagrama de Atividades | Diagrama de Componentes |
|----------------|------------------------|----------------------|------------------------|
| **Funcionalidade 1 - Cadastro e Submissão de Solicitações** | ✓ | ✓ | ✓ |
| **Funcionalidade 2 - Aprovação e Gestão pelo Gestor** | ✓ | ✓ | ✓ |
| **Validação de Horários** | P | ✓ | ✓ |
| **Sistema de Notificações** | P | ✓ | ✓ |
| **Gestão de Calendários** | ✓ | P | ✓ |

## Matriz de Rastreabilidade: Atores vs Funcionalidades

| Atores do Sistema | Cadastro de Solicitações | Validação de Horários | Aprovação/Negação | Atribuição de Recursos | Recebimento de Notificações | Visualização de Calendários |
|------------------|-------------------------|---------------------|------------------|----------------------|---------------------------|---------------------------|
| **Solicitante** | ✓ | P | | | ✓ | ✓ |
| **Gestor** | | | ✓ | ✓ | ✓ | ✓ |
| **Motorista** | | | | P | ✓ | ✓ |
| **Sistema (Automático)** | P | ✓ | | | ✓ | ✓ |

## Detalhamento dos Requisitos Funcionais

### RF01 - Cadastro de Solicitações
**Descrição:** O sistema deve permitir que solicitantes preencham um formulário digital com dados da viagem (nome, datas, horários, locais, observações).  
**Componentes Relacionados:** Formulário Digital, Validação de Horários, Banco de Dados  
**Critérios de Aceite:**
- Formulário deve validar campos obrigatórios
- Interface deve ser intuitiva e responsiva
- Dados devem ser armazenados no banco de dados

### RF02 - Validação Automática de Horários
**Descrição:** O sistema deve validar automaticamente os horários informados conforme a carga horária operacional da empresa.  
**Componentes Relacionados:** Validação de Horários, Banco de Dados  
**Critérios de Aceite:**
- Validação deve ocorrer em tempo real
- Mensagens de erro devem ser claras
- Regras de negócio devem ser configuráveis

### RF03 - Aprovação/Negação pelo Gestor
**Descrição:** Gestores devem poder aprovar ou negar solicitações através de interface dedicada.  
**Componentes Relacionados:** Módulo de Aprovação, Interface do Gestor, Seleção de Motorista/Veículo, Banco de Dados  
**Critérios de Aceite:**
- Interface deve listar solicitações pendentes
- Decisão deve ser registrada com timestamp
- Comentários devem ser opcionais

### RF04 - Atribuição de Motorista e Veículo
**Descrição:** Durante a aprovação, gestores devem selecionar motorista e veículo adequados.  
**Componentes Relacionados:** Módulo de Aprovação, Interface do Gestor, Seleção de Motorista/Veículo, Banco de Dados  
**Critérios de Aceite:**
- Lista deve mostrar apenas recursos disponíveis
- Conflitos de agenda devem ser identificados
- Atribuição deve ser registrada no sistema

### RF05 - Envio de Notificações por E-mail
**Descrição:** O sistema deve enviar automaticamente e-mails informando status das solicitações.  
**Componentes Relacionados:** Sistema de Notificações, API de E-mail, Banco de Dados  
**Critérios de Aceite:**
- E-mails devem ser enviados automaticamente
- Templates devem ser personalizáveis
- Histórico de envios deve ser mantido

### RF06 - Armazenamento de Viagens
**Descrição:** Todas as viagens aprovadas devem ser armazenadas no sistema.  
**Componentes Relacionados:** Calendário Interno, Calendário Público, Banco de Dados  
**Critérios de Aceite:**
- Dados devem ser íntegros e consistentes
- Backup automático deve ser realizado
- Acesso deve ser controlado por perfil

### RF07 - Visualização em Calendários
**Descrição:** Viagens devem ser exibidas em calendários internos e públicos.  
**Componentes Relacionados:** Calendário Interno, Calendário Público, Banco de Dados  
**Critérios de Aceite:**
- Calendários devem ser atualizados em tempo real
- Diferentes visualizações devem estar disponíveis
- Filtros devem permitir personalização

## Observações e Dependências

### Dependências Críticas
- **Módulo de Validação de Horários:** Fundamental para o funcionamento do sistema, deve ser implementado antes da funcionalidade de cadastro
- **API de E-mail:** Essencial para o sistema de notificações, deve ser configurada adequadamente
- **Banco de Dados:** Base para todos os componentes, deve ser estruturado e otimizado desde o início

### Considerações de Segurança
- Todos os componentes que manipulam dados sensíveis devem implementar controles de acesso apropriados
- Autenticação e autorização devem ser implementadas em todas as interfaces
- Logs de auditoria devem ser mantidos para todas as operações críticas

### Considerações de Performance
- Sistema de calendários deve ser otimizado para consultas rápidas
- Cache deve ser implementado para melhorar performance
- Banco de dados deve ser indexado adequadamente

### Integrações Externas
- **API de E-mail:** Integração com serviços de e-mail externos
- **Calendários Digitais:** Sincronização com calendários externos (Google Calendar, Outlook)
- **Sistemas de RH:** Possível integração para validação de funcionários

## Status de Implementação

### Implementado (✓)
Componente/funcionalidade totalmente desenvolvido e testado, pronto para produção.

### Parcial (P)
Componente/funcionalidade em desenvolvimento ou com implementação parcial, necessita complementação.

### Não Implementado (vazio)
Componente/funcionalidade pendente de desenvolvimento, deve ser planejado para próximas iterações.
