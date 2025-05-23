# Artefato de Arquitetura – Projeto de Transporte Autônomo

## Iteração 1 – Núcleo Funcional (Continuação)

### 8. Arquitetura Interna: Diagrama de Componentes (Nível 3)

Nesta seção detalhamos os componentes internos do principal contêiner, a **API Backend**, responsável pela lógica de negócio que suporta os primeiros 5 requisitos.

#### Principais Componentes da API Backend

- **Controlador de Solicitação de Corrida**  
  Recebe e processa as requisições de veículos autônomos (RF01), valida dados e interage com o banco para agendamento.

- **Módulo de Cálculo de Rota**  
  Responsável pela comunicação com o serviço externo de cálculo de rotas (RF02), requisitando e recebendo a rota otimizada.

- **Validador de Código de Confirmação**  
  Compara códigos fornecidos pelo usuário e pela interface do veículo para garantir a segurança da viagem (RF03).

- **Gerenciador de Geoposicionamento**  
  Consolida dados do GPS do dispositivo, sensores do veículo e atualizações da API de trânsito, monitorando a posição da corrida (RF04).

- **Central de Ajuda Integrada**  
  Serve conteúdos da FAQ e gerencia acesso offline para suporte ao usuário (RF05).

- **Repositórios de Dados**  
  Interfaces para interação com o banco de dados, abstraindo a persistência das informações críticas.

---

### 9. Arquitetura de Código: Diagrama de Código (Nível 4)

O diagrama de código detalha o componente **Controlador de Solicitação de Corrida**, que é crítico para o funcionamento do sistema.

#### Classes e Interfaces Principais

- **SolicitacaoCorridaController**  
  Expõe endpoints REST para receber as requisições do app móvel, orquestra o fluxo de validação e agendamento.

- **SolicitacaoService**  
  Contém a lógica para validar dados de entrada, verificar disponibilidade dos veículos e registrar a corrida no banco.

- **CodigoValidacaoService**  
  Gera e valida códigos únicos para confirmação da corrida, garantindo a segurança no embarque.

- **RotaServiceClient**  
  Cliente HTTP que comunica com o serviço de cálculo de rotas, requisitando trajetos otimizados.

- **LocalizacaoTracker**  
  Processa e armazena os dados de geoposicionamento recebidos do dispositivo e veículo.

- **FAQService**  
  Controla o acesso às perguntas frequentes e conteúdo de suporte, garantindo disponibilidade offline.

---

### 10. Fluxo de Interação Interna

1. O **SolicitacaoCorridaController** recebe uma solicitação do app contendo localização e destino.
2. Encaminha a requisição ao **SolicitacaoService**, que valida os dados e verifica disponibilidade.
3. Solicita a rota otimizada ao **RotaServiceClient**.
4. Registra a corrida no banco via repositórios de dados.
5. Gera um código de confirmação pelo **CodigoValidacaoService**.
6. Retorna a confirmação e detalhes da corrida para o app.
7. Durante a corrida, o **LocalizacaoTracker** atualiza a posição em tempo real.
8. Em caso de dúvidas, o app consulta o **FAQService**.

---

### 11. Tecnologias e Padrões de Implementação

- **REST API** utilizando Express (Node.js) ou Spring Boot (Java).
- **Padrão Repository** para abstração da persistência no PostgreSQL.
- **Cliente HTTP** para integração com microserviço de rotas.
- **JWT** para autenticação e segurança dos endpoints.
- **Cache Local** no app para suporte offline da FAQ.
- Uso de **Mensageria** ou **WebSocket** para atualizações em tempo real da localização (opcional para futuras iterações).

---

### 12. Considerações Finais

Esta detalhamento interno prepara a base para implementação e testes focados, além de garantir que a arquitetura seja clara para desenvolvedores, QA e demais envolvidos.

---

### 13. Próximos Artefatos

- Diagramas PlantUML para Componentes e Código que ilustram exatamente estes detalhes estarão disponíveis para complementar esta documentação.

---

Quer que eu gere agora os arquivos PlantUML correspondentes para esses diagramas?  
