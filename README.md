# Documentação

Esta documentação contém diagramas que visualizam a solução implementada para a **Fábrica de Software LabTech**, detalhando a topologia dos serviços e o processo de reservas.

## Topologia da Solução da Fábrica de Software

Este diagrama mostra a arquitetura da solução, integrando diversos serviços utilizados no sistema:

![](/topologia_da_solucao_da_fabrica_de_software_labtech.png?raw=true)

### Componentes Principais:
- **API Gateway**: Gerencia a comunicação entre os clientes e os serviços internos.
- **Servidor de Autenticação (SSO)**: Serviço de autenticação centralizado que permite login único para todos os usuários.
- **APIs**:
  - **Reservas**
  - **Alocação de Professores**
  - **Eventos**
- **Recursos Compartilhados**:
  - **GraphQL**: Interface para consultas.
  - **Cache Redis**: Armazena dados temporários.
  - **Serviço de Autenticação**: Provê tokens e os valida
- **Serviço de Email**: GCP Function que gerencia notificações por email usando SMTP do GoDaddy.
- **Logstash**: Responsável pela coleta e agregação de logs do sistema.
  
### Comunicação:
- O sistema utiliza **Pub/Sub** para a troca de mensagens entre serviços.
    - reservas.eventos.novo-evento
    - alocacao.compartilhados.atualizar-oferta
- Os serviços são expostos e acessados internamente por uma rede de microserviços.

## BPMN Reservas

Este diagrama BPMN detalha o fluxo de atividades relacionado ao processo de reservas, desde a solicitação até a confirmação da reserva:

![](/reservas/bpmn-reservas.svg?raw=true)

