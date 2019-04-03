# IFace

Funcionalidades

Atráves do padrão de projeto ** Command ** as funcionalidades do projeto foram implmentadas cada uma em um objeto que implementam o Commando tendo em cada classe um método execute que implementa o que aquela funcionalidade especifica deve fazer.

## Iterator

  - Motivação: Implementar o padrão de projeto Iterator de forma generica podendo criar um Iterator para qualquer tipo de objeto
  - Solução: Criar uma interface que permita a criação de um iterator genérico fazendo uso dos Generics de Java
  - Vantagens: Deixa o código mais fácil de ser interpretado; para qualquer lista de qualquer objeto tem-se uma maneira direta de iterar pelos seus itens.
  - Desvantagens: aumenta o número de classes necessárias para o projeto, pois o iterator depende de outras duas classes.
### métodos de iterator
  - hasNext: retorna um boolean informando se existe ou não um elemento depois do atual
  - next: retorna um tipo generico que será o proximo objeto da lista

## ContainerIterator

  - Motivação: Ter uma maneira direta de ter uma instancia de um iiterator
  - Solução: criar o ContainerIterator e atráves dele retornar uma instancia de um objeto iterator
  - Vantagens: Uma forma direta de ter acesso a uma instancia de iterator
  - Desvantagens: crescimento do número de classes necessárias.
### métodos de containerIterator
  - getIterator: retorna uma instancia de iterator

## RepositoryMessage

  - Motivação: ter uma maneira direta de invocar um metodo que retorne um iterator para as mensagens
  - Solução: criar a implementação do Iterator para as mensagens
  - Vantagens: ter como acessar as mensagens atraves de um Iterator
  - desvantagem: aumento no número de classes, pois além dela mesma é necessário, ainda, criar uma classe interna para cada tipo de Iterator que desejar ter.
### métodos de repositoryMessage 
  - getIterator: retorna o iterator de mensagem

## MessageIterator

  - Motivação: ter um iterator para as mensagens
  - Solução: atraves do repositoryMessage criar uma classe interna que implemente um Iterator só para as mensagens
  - Vantagens: ter como iterar pelos objetos do tipo mensagem de uma lista de mensagens enviadas
  - desvantagens: o número de classes criadas para que isso seja possivel
### métodos de MessageIterator
implementação dos métodos definidos em **Iterator**

## Message

  - Motivação: representar uma mensagem do sistemas
  - Solução: criar um objeto com os aspectos que definem uma mensagem
  - Vantagens: ter todos os atributos de mensagem num só objeto

## User
  - Motivação: Agrupar todas as informações que cabem no usuário em relação as especificações sistema
  - Solução: criar um usuário e dar a ele acesso as suas informações
  - vantagem: Poder ter uma lista de usuários global compartilhada para todos os usuários.
  - Desvantagem: Informação duplicada, para formar a lista de amigos e de notificações de amizade é salvo todo o objeto do outro usuário em duas novas listas além da lista global.
### métodos de User
  - addNotification: adiciona uma solicitaçãod e amizade

## Community
  - Motivação: Definir o que é uma comunidade para o sistema
  - Solução: Com isso é possivel ter dados compartilhados globalmente com todos os usuário através de uma lista de comunidades
  - Vantagem: Com ela é possível agrupar todas as informações de uma comunidade
### métodos de community
  - sendMessage: envia uma mensagem para todos os membros da comunidade
  - showMembers: exibe todos os membros da comunidade

## Pair

  - Motivação: Criar um objeto que possa agrupar informações em pares para salvar os novos detalhes de cada usuário (tendo na chave e valor o titulo e a descrição da caracteristica)
  - Solução: Criar um objeto que agrupe informações em pares
  - Vantagem: Quando a relação direta entre os objetos (como no caso de titulo e descrição) é interessante que os dois sejam salvos juntos, para evitar a chance de ter um chaveamento errado e relacionar o que deveria ser uma chave com o valor errado


## Account
  - Motivação agrupar em um só lugar todas as informações e ações possiveis para uma conta
  - Solução: criar uma classe que perimitisse usar todas as ações possiveis do sistema (usando o padrão de projeto command)
  - Vantagens: extensibilidade para demais ações futuras
  - Desvantagens: por usar o padrão de projeto command ha um crescimento no número de objetos necessários
### Métodos de account
  - execute

## CommandIterface
  - Motivação: unificar a forma de executar ações difrerentes com assinaturas iguais
  - Solução: implementar uma interface comum para todas as ações, de forma  que, ao executar, basta chamar de uma instancia da interface e o comando correto será executado
  - Vantagem: escrever menos código para executar determinada tarefa deixando-o mais légivel
  - Desvantagem: escrever mais código para preparar as coisas para a execução das tarefas

 ## RemoveAccount, SendMessage, addFriend, createCommunity, editProfile, showProfile, addMemberInCommunity
   - Motivação: unificar a forma de executar todas as funcionalidades do sistema
   - Solução: utilizar o padrão de projeto Command
   - Vantagem: facilidade de invocar qualquer comando do projeto
   - Desvantagem: o crescente número de classes necessárias ( uma para cada comando )
