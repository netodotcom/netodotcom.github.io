---
author: Neto Silveira
pubDatetime: 2019-09-09T12:01:00Z
title: Princípios SOLID
postSlug: solid-principles
featured: true
draft: false
tags:
  - Portuguese
  - Programming
  - Object-oriented Design
  - SOLID Principles
ogImage: ""
description: SOLID e suas aplicações práticas.
---

# What is SOLID

SOLID é um conjunto de princípios de design que ajuda os desenvolvedores a criar softwares mais sustentáveis, escaláveis e flexíveis usando OOP. Esses princípios foram introduzidos pela primeira vez por Robert C. Martin (também conhecido como Uncle Bob) em seu livro "Desenvolvimento Ágil de Software, Princípios, Padrões e Práticas".

Existem cinco princípios no SOLID, que são frequentemente referidos por suas siglas: SRP, OCP, LSP, ISP e DIP.

- Princípio da Responsabilidade Única (SRP)
- Princípio Aberto-Fechado (OCP)
- Princípio da Substituição de Liskov (LSP)
- Princípio da Segregação da Interface (ISP)
- Princípio da Inversão de Dependência (DIP)
  <br><br>

# Princípio da Responsabilidade Única (SRP)

O "princípio da Responsabilidade Única" é um conceito fundamental na engenharia de software que afirma que uma classe ou componente deve ter apenas UMA responsabilidade. O bônus prático de utilizar esse conceito no desenvolvimento é organização que traz legibilidade e manutenabilidade.

## Exemplos

O código a seguir viola o princípio SRP porque contém múltiplas responsabilidades em uma única classe.

```java
public class Exemplo {

  public List<Post> carregarFeed() {
    // lógica para carregar as atualizações mais recentes do feed de notícias
  }

  public void exibirNotificacoes() {
    // lógica para exibir as notificações do usuário
  }
  public List<Post> filtrarFeedPorTipo(TipoPostagem tipo) {
    // lógica para filtrar o feed de notícias por tipo de postagem
  }

  public List<Amigo> listarAmigos() {
    // lógica para listar os amigos do usuário
  }

}
```

O ideal seria implementar todas essas classes, cada uma com sua responsabilidade. O código a seguir é um exemplo, portanto `FeedLoader` que tem o método `carregarFeed()` mas normalmente haveriam outros métodos relativos a responsabilidade desta classe.

```java
public class FeedLoader {

  public List<Post> carregarFeed() {
    // lógica para carregar as atualizações mais recentes do feed de notícias
  }

}

public class FeedFilter {

  public List<Post> filtrarFeedPorTipo(List<Post> feed, TipoPostagem tipo) {
    // lógica para filtrar o feed de notícias por tipo de postagem
  }

}

public class FriendsManager {

  public List<Amigo> listarAmigos() {
    // lógica para listar os amigos do usuário
  }

  public void adicionarAmigo(Amigo amigo) {
    // lógica para adicionar um novo amigo à lista
  }

  public void removerAmigo(Amigo amigo) {
    // lógica para remover um amigo da lista
  }

}

public class Notifications {

  public void exibirNotificacoes() {
    // lógica para exibir as notificações do usuário
  }

}
```

## O princípio da responsabildiade única, MVC e DDD.

O conceito está fortemente relacionado com o Domain-Driven Design (DDD) e o padrão de arquitetura MVC.
<br><br>

### Model View Controller

No padrão de arquitetura MVC, o SRP é aplicado para separar as responsabilidades de cada componente.

`Model` é responsável apenas por gerenciar os dados do sistema.

`View` é responsável apenas por exibir esses dados para o usuário.

`Controller` é responsável apenas por atualizar o `Model` e a `View` de acordo com as entradas do usuário.
<br><br>

### Domain Driven Design

No `DDD`, a ideia de responsabilidade é fundamental para a modelagem de um domínio rico e expressivo. Cada classe ou componente do sistema deve ter uma única responsabilidade clara e definida, de modo que cada parte do modelo de domínio represente um único conceito.
