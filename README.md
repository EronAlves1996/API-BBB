# API-BBB

API feita com o intuito de praticar princípios de modelagem REST, usando como base a dinâmica do Reality Show Big Brother Brasil.

## Planejamento geral para construção da API

A API simulará como funciona o reality show do BBB, podendo ter quantas edições quiserem e também rolando ao mesmo tempo. 
As features para a API foram subdivididas de forma a reduzir o escopo de cada uma das partes para facilitar o desenvolvimento.
Será feito nas seguintes fases:

### 1 - Bootstrapping

[Issue correspondente](https://github.com/EronAlves1996/API-BBB/issues/1)


O bootstraping será a fase onde se cria uma nova edição e realiza-se o cadastro dos participantes. Nesse caso, teremos dois tipos de usuários: uma é o organizador e a outra é o participante.
Primeiramente, um usuário não cadastrado que quiser realizar uma edição irá se cadastrar na API. Ao se cadastrar, caso não exista um pré-cadastro de um organizador, automaticamente já é registrado como organizador. O organizador já terá uma edição do reality já associada a ele, bastando dar prosseguimento ao pré-cadastro dos participantes.
Feito o pré-cadastro, os participantes poderão se cadastrar e complementar suas informações.

### 2 - Dinâmica do jogo

Após realizado o bootstrapping do jogo, dá-se início à dinâmica dele.
A dinâmica sempre se dá de forma sequencial em espaços denominados rodadas:

1. É eleito um líder da rodada
2. É eleito um anjo da rodada
3. O anjo imuniza outro participante
4. O líder indica um participante ao paredão
5. Os demais participantes votam em um outro participante (exceto imunizados) ao paredão
6. O organizador poderá ter algum outro critério para que mais um participante participe do paredão
7. É feita uma votação aberta, no qual não-usuários poderão escolher quem é eliminado da rodada
8. O mais votado é eliminado
9. Retorna ao 1

Essa dinâmica se repete até ir para a final do jogo

### 3 - Final do jogo

O final do jogo é atingido quando há apenas 5 participantes. Neste caso, é eleito um líder e eleito um anjo. O líder está imunizado e o anjo irá imunizar outro participante. Os 3 participantes que sobraram estarão no paredão.

Após essa eliminação, ocorre a última eleição do líder, não tendo eleição do anjo. Nesta rodada, o líder é imunizado e as outras três pessoas estão no paredão.

Após a eliminação, há a final, onde a votação dos não-participantes é para decidir o ganhador. Após eleito o ganhador, todos os participantes são automaticamente eliminados e o organizador automaticamente é deposto com o final da edição. Caso ele queira organizar novo jogo, terá que se cadastrar novamente.

** Todas as três fases acima terão issues correspondentes **
