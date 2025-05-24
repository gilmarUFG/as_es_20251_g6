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

- **SolicitacaoVeiculoController**  
  Expõe endpoints REST para receber as requisições do app móvel, orquestra o fluxo de validação e agendamento.

- **SolicitacaoVeiculoService**  
  Contém a lógica para validar dados de entrada, verificar disponibilidade dos veículos e registrar a corrida no banco.

- **SolicitacaoVeiculosRepository**  
  Responsável pela persistência dos dados de solicitações de corridas no banco de dados.

- **CalculoRotasService**  
  Realiza o cálculo de rotas otimizadas, utilizando dados de geoposicionamento e integrando-se ao serviço externo de rotas.

- **ValidacaoVeiculoController**  
  Expõe endpoints REST para manipulação e validação dos códigos de confirmação de embarque.

- **ValidacaoVeiculoService**  
  Processa a geração e validação dos códigos de confirmação, garantindo a segurança do embarque.

- **ValidacaoVeiculoRepository**  
  Gerencia a persistência dos dados relacionados aos códigos de confirmação.

- **GeoposicionamentoController**  
  Recebe e processa requisições de atualização de localização dos veículos e dispositivos.

- **GeoposicionamentoService**  
  Gerencia e consolida informações de localização, garantindo precisão e confiabilidade dos dados.

- **GeoposicionamentoRepository**  
  Responsável pela persistência dos dados de geoposicionamento no banco de dados.

---

### 10. Fluxo de Interação Interna

1. O **SolicitacaoVeiculoController** recebe uma solicitação do app contendo localização e destino do usuário.
2. O controller encaminha a requisição ao **SolicitacaoVeiculoService**, que valida os dados recebidos e verifica a disponibilidade de veículos.
3. O **SolicitacaoVeiculoService** solicita ao **CalculoRotasService** o cálculo da rota otimizada, utilizando informações do **GeoposicionamentoService** para obter a posição atual dos veículos.
4. Após obter a rota, o **SolicitacaoVeiculoService** registra a corrida no banco de dados por meio do **SolicitacaoVeiculosRepository**.
5. Em seguida, o **SolicitacaoVeiculoService** aciona o **ValidacaoVeiculoService** para gerar o código de confirmação de embarque, que é persistido pelo **ValidacaoVeiculoRepository**.
6. O controller retorna ao app a confirmação da corrida, detalhes da rota e o código de embarque.
7. Durante a corrida, o **GeoposicionamentoController** recebe atualizações de localização dos veículos e dispositivos, repassando ao **GeoposicionamentoService**, que consolida e armazena os dados via **GeoposicionamentoRepository**.
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
