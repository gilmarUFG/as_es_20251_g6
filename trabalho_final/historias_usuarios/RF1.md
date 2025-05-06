# RF1 - Solicitação de Veículo Autônomo

## Narrativa:
- **Como** usuário passageiro
- **Eu quero** solicitar um veículo autônomo, por meio do aplicativo
- **Para** que eu possa embarcar em um veículo autônomo e chegar até meu destino

## Cenário 1: Solicitação de Veículo Autônomo com Sucesso
- **Como** usuário passageiro
- **Quando** Eu estiver devidamente logado
- **Eu quero** solicitar um veículo autônomo, por meio do aplicativo
- **Assim que** informar minha localização atual e destino desejado, sendo ambos válidos
- **E** visualizar a estimativa de tempo para que o veículo chegue
- **E** Confirmar o pedido da viagem
- **Então** Um veículo será direcionado à minha localização

 ## Cenário 2: Solicitação de Veículo Autônomo com Localização Atual e Destino Iguais
- **Como** usuário passageiro
- **Quando** Eu estiver devidamente logado
- **Eu quero** solicitar um veículo autônomo, por meio do aplicativo
- **Assim que** informar minha localização atual e destino desejado, sendo ambos iguais
- **Então** Uma mensagem de erro impedirá o prosseguimento, informando o erro na rota

 ## Cenário 3: Solicitação de Veículo Autônomo na Faltando Veículos na Proximidade
- **Como** usuário passageiro
- **Quando** Eu estiver devidamente logado
- **Eu quero** solicitar um veículo autônomo, por meio do aplicativo
- **Assim que** informar minha localização atual e destino desejado, sendo ambos válidos
- **E** ser detectada a falta de oferta de veículos autônomos em minha região
- **Então** Uma mensagem de erro impedirá o prosseguimento, informando a falta de veículos disponíveis