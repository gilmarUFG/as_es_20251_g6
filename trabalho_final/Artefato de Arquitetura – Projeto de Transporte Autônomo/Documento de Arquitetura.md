## 1. Introdução e Objetivos

### 1.1 Visão Geral
O Sistema de Veículo Autônomo é uma solução completa para solicitação, gerenciamento e operação de veículos autônomos. O sistema permite que usuários solicitem corridas através de um aplicativo móvel, enquanto veículos autônomos operam de forma segura e eficiente, fornecendo transporte inteligente e conectado.

### 1.2 Objetivos do Sistema
- Fornecer uma plataforma confiável para solicitação de transporte autônomo
- Garantir segurança através de validação por código de confirmação
- Otimizar rotas considerando tráfego e condições climáticas em tempo real
- Proporcionar experiência de usuário fluida com comunicação por voz
- Monitorar constantemente a saúde dos veículos e detectar riscos

### 1.3 Stakeholders
- **Usuários/Passageiros**: Solicitam e utilizam o serviço de transporte
- **Operadores do Sistema**: Monitoram frota e operações
- **Desenvolvedores**: Mantêm e evoluem o sistema
- **Autoridades de Trânsito**: Regulamentam o serviço

## 2. Restrições

### 2.1 Restrições Técnicas
- Sistema deve operar 24/7 com alta disponibilidade (99.9%)
- Latência máxima de 2 segundos para solicitações críticas
- Suporte a dispositivos móveis iOS e Android
- Conformidade com protocolos de segurança veicular (ISO 26262)

### 2.2 Restrições Organizacionais
- Conformidade com LGPD para proteção de dados pessoais
- Regulamentações locais de transporte e trânsito
- Certificações de segurança para veículos autônomos

### 2.3 Convenções
- Padrão REST para APIs externas
- MQTT para comunicação veículo-backend
- Documentação em português brasileiro

## 3. Contexto e Escopo

### 3.1 Contexto do Negócio
O sistema opera no domínio de mobilidade urbana, integrando-se com sistemas de pagamento, APIs de trânsito e serviços meteorológicos. O contexto inclui interação direta com usuários através de aplicativo móvel e operação autônoma de veículos em ambiente urbano.

### 3.2 Escopo do Sistema
O escopo compreende:
- Aplicativo móvel para usuários
- Sistema backend de gerenciamento
- Sistemas embarcados veiculares
- Serviços de cálculo de rotas
- Central de ajuda e FAQs
- Integração com sistemas externos

### 3.3 Sistemas Externos
- **Sistema de Pagamentos**: Processamento de transações financeiras
- **API de Trânsito**: Dados de tráfego em tempo real
- **API de Clima**: Condições meteorológicas

### 3.4 Requisitos por Iteração

O desenvolvimento do sistema foi organizado em duas iterações principais, cada uma focada em entregar funcionalidades específicas:

| **Iteração** | **Requisito** | **Descrição** | **Prioridade** | **Autor** |
|--------------|---------------|---------------|----------------|-----------|
|**1** | RF01 | Solicitação de Veículo Autônomo - O usuário deve ser capaz de solicitar um veículo autônomo pelo aplicativo, informando sua localização atual e destino desejado, e receber uma estimativa de tempo para a chegada do veículo. | Alta | Guilherme Gonçalves Dutra de Mendonça |
|**1** | RF02 | Cálculo de Rotas Otimizadas - O aplicativo deve ser capaz de calcular rotas otimizadas para veículos autônomos, levando em consideração o tráfego em tempo real, condições meteorológicas e restrições de tráfego. | Alta | Lucas Gabriel Nunes Alves |
|**1** | RF03 | Validação do Veículo por Código de Confirmação - O sistema deve permitir que o passageiro valide se o veículo que chegou é o correto por meio de um código de confirmação exibido no aplicativo e no painel do veículo. | Alta | Stephany de Oliveira Sousa Milhomem |
|**1** | RF04 | Sistema de Geoposicionamento Preciso - Sistema de geoposicionamento deve ser preciso e à prova de falhas, para evitar erros de localização ao solicitar o veículo e definir destino. | Alta | Álvaro Veloso Lisboa |
|**1** | RF05 | Suporte a Problemas Comuns (FAQs e Central de Ajuda) - O sistema deve ter uma seção de FAQs e uma central de ajuda dentro do app para problemas comuns, como agendamento de corridas, pagamento e questões de segurança. | Alta | Samuel José Evangelista Alves |
|**2** | RF06 | Comunicação com o Usuário via Voz - O sistema deve ser capaz de falar, dando instruções ao usuário e respondendo a dúvidas em tempo real, reduzindo a tensão no uso e aumentando a confiança. | Alta | Mateus Henrique Gandi de Oliveira |
|**2** | RF07 | Avaliação do Serviço - Após a viagem, o usuário deve poder avaliar o serviço e relatar problemas. | Média | Aline Lima Martins Coelho |
|**2** | RF08 | Relato de Problemas Durante a Viagem - O aplicativo deve incluir um sistema de comunicação ou chamada de emergência para que os usuários possam relatar problemas durante a viagem. | Alta | José Alves De Oliveira Neto |
|**2**| RF09 | Detecção de Veículo com Baixa Carga - O sistema deve ser capaz de identificar quando um veículo precisa ser recarregado ou abastecido e não disponibilizá-lo para uso até que esteja pronto. | Alta | Jheissyane Kelly da Silva Souza |
|**2** | RF10 | Detecção de Riscos - O veículo deve ser capaz de perceber riscos e reagir antes que ocorram acidentes. | Alta | Aline Nunes Dos Santos |

## 4. Estratégia da Solução

### 4.1 Abordagem Arquitetural
A arquitetura segue padrão de microserviços com separação clara entre frontend móvel, backend de negócios, sistemas embarcados e serviços especializados. A comunicação é baseada em protocolos assíncronos para garantir responsividade e confiabilidade.

### 4.2 Tecnologias Principais
- **Frontend**: Flutter para aplicativo móvel multiplataforma
- **Backend**: Node.js para API Controller, Java para serviços de negócio
- **Banco de Dados**: PostgreSQL para persistência
- **Comunicação Veicular**: MQTT para mensageria
- **Serviços de Rota**: Python com algoritmos de otimização
- **Sistemas Embarcados**: ROS (Robot Operating System) e C++

### 4.3 Padrões Arquiteturais
- **C4 Model**: Modelagem arquitetural em quatro níveis hierárquicos (Contexto, Container, Componente e Código) para documentação visual da arquitetura do sistema
- **Microserviços**: Separação por domínio funcional
- **Event-Driven**: Comunicação assíncrona baseada em eventos
  
## 5. Visão de Blocos de Construção

### 5.1 Decomposição do Sistema
O sistema é decomposto em containeres principais:

**Aplicativo Móvel**
- Interface única para todas as funcionalidades do usuário (solicitação, confirmação, avaliação)
- Comunicação segura com backend via HTTPS

**API Backend**
- Gerenciamento centralizado da lógica de negócio (corridas, usuários, veículos)
- Orquestração de serviços e comunicação com veículos via MQTT
- Controle de autenticação e autorização
- Processamento de emergências e situações críticas
- Gerenciamento de avaliações e feedback dos usuários

**Banco de Dados**
- Armazenamento persistente de dados de usuários, veículos e corridas
- Repositório de códigos de confirmação e histórico de viagens
- Dados de localização e rotas calculadas
- Registros de emergências, acidentes e eventos de risco
- Informações de recargas e status de veículos

**Central de Ajuda / FAQs**
- Conteúdo estático com perguntas frequentes
- Interface web responsiva integrada ao aplicativo

**Sistemas Embarcados do Veículo**
- Processamento local de sensores e tomada de decisão autônoma
- Comunicação bidirecional com backend via MQTT
- Sistemas de detecção de riscos com IA embarcada
- Monitoramento contínuo de energia e status operacional
- Capacidade de operação offline para situações críticas

**Serviço de Cálculo de Rotas**
- Algoritmos especializados de otimização considerando múltiplos fatores
- Integração com dados externos de tráfego e clima em tempo real
- Cache inteligente para rotas frequentes
- Cálculo de estimativas precisas de tempo e consumo energético
- Recalculo dinâmico de rotas durante viagens

### 5.2 Componentes por Container

**Container: Aplicativo Móvel (Flutter)**
- **Interface Principal**: Tela de solicitação de corridas com seleção de origem e destino
- **Módulo de Localização**: Integração com GPS do dispositivo e seleção manual de endereços
- **Sistema de Validação**: Interface para inserção e validação de códigos de confirmação
- **Módulo de Comunicação por Voz**: Reprodução de instruções e feedback do sistema
- **Sistema de Avaliação**: Interface para avaliação pós-viagem e relato de problemas
- **Central de Ajuda Integrada**: Acesso direto às FAQs e sistema de suporte
- **Módulo de Emergência**: Botão de pânico e comunicação direta com operadores

**Container: API Backend**
- **API Controller (Node.js)**:
  - Endpoint de solicitação de corridas (/solicitar-corrida)
  - Endpoint de confirmação (/confirmar-corrida)
  - Endpoint de validação de códigos (/validar-codigo)
  - Endpoint de emergências (/emergencia)
  - Endpoint de avaliações (/avaliar-servico)

- **API Service (Java)**:
  - Processamento de regras de negócio para corridas
  - Gerenciamento de usuários e autenticação
  - Controle de estados de veículos e disponibilidade
  - Processamento de avaliações e feedback
  - Gerenciamento de emergências e acidentes
  - Processamento de pagamento

- **API Bridge (MQTT Client)**:
  - Comunicação bidirecional com veículos
  - Publicação de comandos (iniciar-corrida, parar, desviar)
  - Recepção de eventos (posição, status, emergências)
  - Gerenciamento de filas de mensagens
  - Tratamento de desconexões e reconnexões

**Container: Central de Ajuda / FAQs (WebApp Estático)**
- **Módulo de Busca**: Sistema de busca por palavras-chave e categorias
- **Base de Conhecimento**: Artigos organizados por temas (pagamento, segurança, operação)
- **Guias Visuais**: Tutoriais passo-a-passo com imagens e vídeos
- **Sistema de Feedback**: Avaliação da utilidade dos artigos

**Container: Serviço de Cálculo de Rotas (Python)**
- **RotasController (REST API)**:
  - Endpoint de cálculo de rotas (/calcular-rota)
  - Endpoint de atualização de rotas (/atualizar-rota)
  - Endpoint de consulta de tráfego (/consultar-trafego)

- **RotasService (Python)**:
  - Algoritmo otimizado para múltiplos critérios
  - Processamento de dados de tráfego em tempo real
  - Análise de condições meteorológicas e impacto nas rotas
  - Cálculo de consumo energético por rota
  - Sistema de cache distribuído para rotas frequentes

**Container: Sistemas Embarcados do Veículo**
- **Vehicle Bridge (MQTT Gateway)**:
  - Cliente MQTT para comunicação com backend
  - Heartbeat para monitoramento de conectividade

- **Vehicle Controller (ROS/Node.js)**:
  - Recepção e interpretação de comandos remotos
  - Coordenação entre sistemas embarcados

- **Vehicle Service (C++)**:
  - Algoritmos de navegação autônoma
  - Controle de velocidade e direção
  - Integração com sistemas de frenagem
  - Processamento de dados de sensores em tempo real

- **GeoPositioning Controller/Service**:
  - **Controller**: Driver para sensores GPS e IMU
  - **Service**: Fusão de dados de localização, correção de erros, mapeamento de posição

- **PowerMonitor Controller/Service**:
  - **Controller**: Interface com sistema de bateria e sensores de energia
  - **Service**: Análise de autonomia, previsão de consumo, alertas de recarga

- **RiskDetection Controller/Service**:
  - **Controller**: Fusão de dados de LIDAR, câmeras e sensores ultrassônicos
  - **Service**: Detecção de obstáculos, previsão de colisões, execução de manobras evasivas

**Componentes de Integração com Sistemas Externos:**
- **Integração API de Tráfego**: Cliente REST para consulta de dados de trânsito
- **Integração API de Clima**: Cliente REST para dados meteorológicos
- **Integração Sistema de Pagamentos**: Interface segura para processamento de transações

## 6. Visão de Runtime

### 6.1 Cenários Principais

**Cenário 1: Solicitação e Confirmação de Corrida**
1. **Solicitação Inicial**: Usuário abre app, define origem e destino
2. **Validação de Dados**: Sistema valida localizações e disponibilidade de veículos
3. **Cálculo de Rota**: RotasService calcula melhor rota considerando tráfego e clima
4. **Seleção de Veículo**: GeoPositioningService identifica veículo mais próximo disponível
5. **Apresentação de Estimativa**: App exibe tempo estimado, rota e preço
6. **Confirmação**: Usuário confirma, sistema cria registro no banco de dados
7. **Acionamento do Veículo**: API Bridge envia comando MQTT para veículo
8. **Geração de Código**: Sistema gera código único de confirmação
9. **Deslocamento**: Veículo inicia movimento em direção ao passageiro

**Cenário 2: Viagem em Andamento com Monitoramento Contínuo**
1. **Chegada e Validação**: Usuário valida veículo através do código de confirmação
2. **Início da Viagem**: Sistema registra início e ativa monitoramento contínuo
3. **Monitoramento de Riscos**: RiskDetectionService analisa ambiente constantemente
4. **Comunicação por Voz**: Sistema informa status da viagem e próximas ações
5. **Ajuste Dinâmico de Rota**: Recalculo automático baseado em condições em tempo real
6. **Monitoramento de Energia**: PowerMonitorService verifica autonomia continuamente
7. **Chegada ao Destino**: Sistema confirma chegada e finaliza viagem
8. **Avaliação**: Usuário avalia serviço e pode reportar problemas

**Cenário 3: Situação de Emergência e Detecção de Riscos**
1. **Detecção de Risco**: Sensores LIDAR/câmeras detectam obstáculo ou situação perigosa
2. **Análise em Tempo Real**: RiskDetectionService processa dados em < 100ms
3. **Tomada de Decisão**: IA determina melhor ação (frenar, desviar, parar)
4. **Execução Automática**: VehicleService executa manobra evasiva imediatamente
5. **Notificação Backend**: Evento é enviado via MQTT para sistema central
6. **Alerta ao Usuário**: Sistema comunica situação via voz e app
7. **Acionamento Manual**: Usuário pode ativar emergência via botão no app
8. **Comunicação com Operadores**: Sistema escala para atendimento humano
9. **Registro de Evento**: Todos os dados são salvos para análise posterior

**Cenário 4: Gerenciamento de Energia e Disponibilidade**
1. **Monitoramento Contínuo**: PowerMonitorService verifica níveis de bateria
2. **Previsão de Autonomia**: Sistema calcula autonomia restante baseado no consumo
3. **Alerta Preventivo**: Sistema identifica necessidade de recarga com antecedência
4. **Remoção da Disponibilidade**: Veículo é retirado automaticamente da lista de disponíveis
5. **Localização de Ponto de Recarga**: Sistema identifica ponto mais próximo disponível
6. **Deslocamento para Recarga**: Veículo se dirige automaticamente para recarga
7. **Processo de Recarga**: Sistema monitora processo e registra dados de energia
8. **Retorno à Operação**: Após recarga completa, veículo retorna à disponibilidade

**Cenário 5: Tratamento de FAQs e Suporte**
1. **Acesso à Central de Ajuda**: Usuário acessa seção de ajuda no app
2. **Busca por Problema**: Sistema de busca localiza artigos relevantes
3. **Exibição de Soluções**: FAQs são apresentadas de forma categorizada
4. **Feedback de Utilidade**: Usuário avalia se a solução foi útil
5. **Escalação para Suporte**: Caso necessário, sistema conecta com atendimento humano
6. **Registro de Interação**: Dados são coletados para melhoria contínua do sistema

### 6.2 Qualidade e Desempenho

**Métricas de Performance Críticas:**
- **Tempo de Resposta para Solicitação**: < 2s desde request até apresentação de estimativa
- **Latência de Detecção de Riscos**: < 100ms para processamento de dados de sensores
- **Tempo de Geração de Código**: < 500ms para geração e sincronização
- **Latência de Comunicação MQTT**: < 200ms para comandos críticos veículo-backend
- **Tempo de Cálculo de Rota**: < 3s para rotas complexas com múltiplos critérios

**Disponibilidade e Confiabilidade:**
- **Uptime do Sistema**: 99.9% (máximo 8.76 horas de indisponibilidade por ano)
- **Disponibilidade de Veículos**: 95% da frota disponível durante horários de pico
- **Taxa de Sucesso de Viagens**: > 99.5% de viagens completadas sem falhas críticas
- **Recuperação de Falhas**: Tempo médio de recuperação < 5 minutos

**Escalabilidade:**
- **Solicitações Simultâneas**: Suporte a 10.000 solicitações concurrent
- **Processamento de Eventos**: 50.000 eventos de sensores por segundo por veículo
- **Mensagens MQTT**: 100.000 mensagens por segundo na infrastrutura
- **Usuários Simultâneos**: Suporte a 100.000 usuários ativos simultaneamente

**Métricas de Segurança:**
- **Tempo de Detecção de Intrusão**: < 1 segundo para ameaças conhecidas
- **Taxa de Falsos Positivos em Detecção de Riscos**: < 0.1%
- **Autenticação**: Tempo médio de autenticação < 1 segundo
- **Auditoria**: 100% das operações críticas logadas com rastreabilidade completa

## 7. Visão de Deployment

### 7.1 Infraestrutura
- **Cloud Híbrida**: Serviços críticos em cloud privada, demais em cloud pública
- **Edge Computing**: Processamento local nos veículos para decisões críticas
  
### 7.2 Ambientes
- **Desenvolvimento**: Ambiente local com simuladores
- **Teste**: Ambiente de integração com veículos de teste
- **Homologação**: Replica produção para validação final
- **Produção**: Ambiente real com alta disponibilidade

### 7.3 Monitoramento
- Alertas automáticos para situações críticas
- Dashboard centralizado para operadores
- Logs distribuídos com rastreabilidade completa

## 8. Conceitos Transversais

### 8.1 Segurança
- Criptografia TLS 1.3 para todas as comunicações
- Autenticação multifator para usuários
- Tokenização de dados sensíveis
- Auditoria completa de operações críticas

### 8.2 Tratamento de Erros e Padrões de Resiliência

**Estratégias por Nível de Criticidade:**

**Nível Crítico (Segurança):**
- **Redundância Tripla**: Sensores críticos com três fontes independentes
- **Processamento Distribuído**: Decisões críticas processadas localmente no veículo
- **Timeout Agressivo**: 100ms para operações de segurança

**Nível Alto (Operacional):**
- **Fallback Graceful**: Degradação controlada mantendo funcionalidades básicas
- **Health Checks**: Monitoramento contínuo de saúde dos componentes

**Nível Médio (Experiência do Usuário):**
- **Cache Inteligente**: Dados frequentes mantidos localmente
- **Retry Transparente**: Tentativas automáticas sem notificar usuário
- **Feedback Proativo**: Notificação de status durante operações longas

**Padrões de Recuperação:**
- **Self-Healing**: Reinicialização automática de componentes com falha
- **Rolling Updates**: Atualizações sem interrupção de serviço

## 9. Decisões Arquiteturais

### 9.1 DR-001: Arquitetura de Microserviços
**Status**: Aprovada  
**Contexto**: Necessidade de escalabilidade e manutenibilidade  
**Decisão**: Adoção de arquitetura de microserviços com comunicação assíncrona  
**Consequências**: Maior complexidade operacional, mas melhor escalabilidade e isolamento de falhas

### 9.2 DR-002: Comunicação Veicular via MQTT
**Status**: Aprovada  
**Contexto**: Necessidade de comunicação confiável e eficiente com veículos  
**Decisão**: Uso de MQTT para comunicação bidirecional  
**Consequências**: Baixa latência e consumo de dados, com garantia de entrega

### 9.3 DR-003: Processamento Edge nos Veículos
**Status**: Aprovada  
**Contexto**: Decisões críticas de segurança não podem depender de conectividade  
**Decisão**: Processamento local para detecção de riscos e navegação básica  
**Consequências**: Maior autonomia dos veículos, mas necessidade de sincronização periódica

## 10. Requisitos de Qualidade

### 10.1 Disponibilidade
- Sistema deve estar disponível 99.9% do tempo
- Tempo de recuperação máximo de 5 minutos para falhas
- Backup automático e recovery em múltiplas regiões

### 10.2 Performance
- Latência máxima de 200ms para solicitações de corrida
- Tempo de resposta do veículo < 3 segundos

### 10.3 Usabilidade
- Interface intuitiva com no máximo 3 toques para solicitar corrida
- Suporte a acessibilidade
- Tempo de aprendizado < 10 minutos para novos usuários

## 11. Riscos e Débito Técnico

### 11.1 Riscos Identificados e Análise de Impacto

**Riscos Técnicos - Alta Prioridade:**

**RT-001: Falha de Sensores Críticos**
- **Probabilidade**: Baixa | **Impacto**: Crítico
- **Descrição**: Falha nos sensores LIDAR ou câmeras principais
- **Consequências**: Risco de acidentes, parada imediata do veículo
- **Mitigação**: Redundância de sensores, validação cruzada, fail-safe automático

**RT-002: Sobrecarga do Sistema em Picos**
- **Probabilidade**: Alta | **Impacto**: Médio
- **Descrição**: Sistema não suporta demanda em horários de pico
- **Consequências**: Lentidão, timeout de operações, experiência degradada
- **Mitigação**: Auto-scaling, load balancing, cache distribuído

**Riscos de Segurança - Alta Prioridade:**

**RS-001: Ataque Cibernético aos Veículos**
- **Probabilidade**: Baixa | **Impacto**: Crítico
- **Descrição**: Invasão dos sistemas embarcados dos veículos
- **Consequências**: Controle malicioso, roubo de dados, acidentes intencionais
- **Mitigação**: Criptografia end-to-end, isolamento de redes críticas

**RS-002: Vazamento de Dados Pessoais**
- **Probabilidade**: Média | **Impacto**: Alto
- **Descrição**: Exposição de dados de localização e informações pessoais
- **Consequências**: Violação de privacidade, multas regulatórias, perda de confiança
- **Mitigação**: Criptografia de dados, controle de acesso rigoroso

**Riscos Operacionais - Prioridade Média:**

**RO-001: Falha em APIs Externas Críticas**
- **Probabilidade**: Alta | **Impacto**: Médio
- **Descrição**: Indisponibilidade de APIs de tráfego ou clima
- **Consequências**: Estimativas incorretas
- **Mitigação**: Múltiplos provedores, cache de dados históricos, fallback para dados locais

**Riscos Regulatórios - Prioridade Alta:**

**RR-001: Mudanças na Legislação**
- **Probabilidade**: Alta | **Impacro**: Alto
- **Descrição**: Novas regulamentações para veículos autônomos
- **Consequências**: Necessidade de modificações significativas, possível suspensão
- **Mitigação**: Acompanhamento regulatório contínuo, arquitetura flexível

## 12. Glossário

**API**: Interface de Programação de Aplicações - conjunto de definições e protocolos para construção de software

**MQTT**: Protocolo de mensageria leve para comunicação máquina-a-máquina

**Edge Computing**: Processamento de dados próximo à fonte de geração, reduzindo latência

**LIDAR**: Tecnologia de detecção que usa luz laser para medir distâncias

**ROS**: Robot Operating System - framework para desenvolvimento de software robótico

**Failover**: Processo automático de transferência para sistema backup em caso de falha

**Graceful Degradation**: Capacidade do sistema de manter funcionalidades básicas mesmo com componentes falhando
