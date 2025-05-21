# Artefato de Arquitetura – Projeto de Transporte Autônomo

## Iteração 1 – Núcleo Funcional

### 1. Visão Geral da Arquitetura

Esta primeira fase concentra-se no núcleo funcional do sistema de transporte autônomo, abordando as funcionalidades mínimas necessárias para garantir o funcionamento básico da aplicação. O objetivo principal é permitir que os usuários possam solicitar veículos autônomos, receber rotas otimizadas, validar a segurança da viagem, rastrear com precisão a localização, e obter suporte para dúvidas comuns. A arquitetura é pensada para ser escalável, modular e resiliente, com integração a serviços externos essenciais.

### 2. Requisitos Contemplados

| Código | Requisito                                                      |
|--------|----------------------------------------------------------------|
| RF01   | Solicitação de Veículo Autônomo                                |
| RF02   | Cálculo de Rotas Otimizadas                                    |
| RF03   | Validação do Veículo por Código de Confirmação                 |
| RF04   | Sistema de Geoposicionamento Preciso                           |
| RF05   | Suporte a Problemas Comuns (FAQs e Central de Ajuda)           |

### 3. Estrutura Arquitetural

A arquitetura adotada segue o modelo C4, destacando os níveis de Contexto (nível 1) e Contêiner (nível 2) nesta etapa do projeto.

- **Aplicativo Móvel (App):** Interface principal para interação do usuário. Permite solicitações, exibe rotas, códigos de validação e acesso à central de ajuda.
- **API Backend:** Responsável por toda a lógica de negócio, validação, gerenciamento de sessões, controle de corridas e integração com serviços externos.
- **Serviço de Cálculo de Rotas:** Microserviço especializado que calcula rotas otimizadas considerando dados dinâmicos de tráfego e clima.
- **Banco de Dados Relacional:** Armazena informações críticas como cadastro de usuários, dados dos veículos, corridas agendadas, códigos de validação e históricos.
- **Central de Ajuda (FAQ):** Aplicação web estática que oferece respostas organizadas para problemas comuns, garantindo suporte contínuo mesmo offline.
- **Integração com Serviços Externos:** APIs externas de trânsito e clima são acessadas pela API Backend para enriquecer o cálculo de rotas e garantir atualização constante.

### 4. Processos Detalhados Relacionados aos Requisitos

#### RF01 – Solicitação de Veículo Autônomo
- **Fluxo:** Usuário abre o app e informa sua localização e destino.
- **API Backend:** Recebe a solicitação, valida os dados e verifica a disponibilidade de veículos próximos.
- **Agendamento:** Reserva o veículo e registra a corrida no banco de dados.
- **Feedback:** Envia ao app a confirmação da solicitação com uma estimativa de tempo de chegada.

#### RF02 – Cálculo de Rotas Otimizadas
- **Dados de Entrada:** Origem, destino, tráfego em tempo real e condições climáticas.
- **Serviço de Rotas:** Executa algoritmo A* adaptado para considerar condições dinâmicas.
- **Atualização Dinâmica:** Caso o tráfego ou clima se altere, o serviço pode recalcular a rota e notificar o backend.
- **API Backend:** Repassa a rota otimizada ao app para navegação.

#### RF03 – Validação do Veículo por Código de Confirmação
- **Código Único:** Gerado pela API no momento da reserva, exibido no app.
- **Validação Física:** Passageiro verifica o código no painel do veículo.
- **API Backend:** Recebe confirmação do código, libera a corrida ou bloqueia o acesso caso haja divergência.
- **Segurança:** Impede que usuários entrem em veículos errados, aumentando a confiabilidade do sistema.

#### RF04 – Sistema de Geoposicionamento Preciso
- **Coleta de Dados:** O app usa GPS do dispositivo, complementado por sensores do veículo.
- **Sincronização:** Dados são enviados continuamente ao backend para monitoramento.
- **Precisão:** Algoritmos de filtragem e correção evitam erros comuns em localização.
- **Interface:** O app apresenta a posição atual do veículo e progresso da viagem ao usuário.

#### RF05 – Suporte a Problemas Comuns
- **Central de Ajuda:** Aplicação web estática hospedada para fornecer FAQs organizadas por categoria.
- **Acesso Offline:** Permite consulta mesmo sem conexão, utilizando cache local.
- **Atualização:** FAQs são atualizadas pelo time de suporte, refletindo as dúvidas mais frequentes.
- **Navegação:** O app direciona os usuários para a central de ajuda quando necessário.

### 5. Tecnologias Envolvidas

| Componente        | Tecnologia Sugerida                 |
|-------------------|-----------------------------------|
| Aplicativo Mobile | Flutter ou React Native            |
| Backend API       | Node.js (Express) ou Spring Boot  |
| Banco de Dados    | PostgreSQL                       |
| Serviço de Rotas  | Python com algoritmo A*            |
| Central de Ajuda  | WebApp Estático (HTML, CSS, JS)   |

### 6. Aspectos de Segurança e Resiliência

- **Autenticação:** Uso de tokens JWT para autenticação segura das requisições.
- **Validação de Dados:** Todos os inputs são validados para evitar inconsistências e ataques.
- **Tolerância a Falhas:** Em caso de indisponibilidade dos serviços externos, o backend mantém operações básicas com dados em cache.
- **Monitoramento:** Logs detalhados e métricas de desempenho para análise contínua.

---

### 7. Próximos Passos: Diagrama de Contexto e Contêiner

Os diagramas de Contexto (Nível 1) e Contêiner (Nível 2) serão gerados em PlantUML para complementar esta documentação, detalhando as interações entre os atores, sistemas e componentes envolvidos nesta fase da arquitetura.

---

