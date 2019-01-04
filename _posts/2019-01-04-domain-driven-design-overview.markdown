---
layout: post
title:  "Domain-Driven Design Overview"
---

## Introduction

Software architectures for iOS apps is a relevant topic in the developer community. Last year I learned and used Domain-Driven Design (DDD) and now I want to share it with you.

My colleague and friend once recommended several books on architecture, among of which was “Domain-Driven Design” by Eric Evans. It turned out to be a different kind of animal than other XYZ-Driven and XYZ-Oriented techniques. It also turned out to be quite old - from 2004!

The ideas in this book made total sense to me. It felt like I found instruction on how to build a house with what Lego blocks (design patterns) I had on my hands. It clicked. 

Nevertheless, it was a bit abstract and I kept searching how to put the ideas into practice until I found “Implementing Domain-Driven Design” by Vaughn Vernon. More importantly, the book’s example code. Finally, I had something I could get my hands dirty with.

## Domain-Driven Design Explained

As I understand it, the core of the DDD is the Domain Model architectural pattern. Combined with other patterns, it becomes an asset in your toolbox. 

The major patterns that DDD uses are:

- Domain Model
- Ports and Adapter
- Registry
- Value Object
- Factory

Here I will only discuss the first one, the **Domain Model**.

In essence, the Domain-Driven Design is a model of a domain implemented as software. It is a system of the following:

- Bounded Contexts
- Entities
- Value Objects
- Aggregates
- Repositories
- Domain Services

The **Bounded Context** is a model of a part of your domain. In other words, it is a model of a sub-domain.  It defines a context for the names of the entities, value objects and everything else. For example, the “Account” in the accounting domain model is different from the “Account” in the logistic system, those two accounts belong to different domains, and therefore they should be part of different bounded contexts. Without a context, a domain model gets bloated with different kinds of entities relevant for different subdomains.

The **Entity** classes represent identifiable entities, i.e. anything that has an identity. Entities are mutable, they can have different properties throughout their lifetime. Examples are User, BankAccount, or something else with ID. Two entities with the same properties are different if they have different IDs.

The **Value Objects** model non-identifiable structures. Any two value objects with the same properties are identical. Think of such things as Address (in most e-commerce systems), Money or ContactInformation structures.

The **Aggregates** are what I call “uber”-Entities - they are using or composed of other entities and value objects. This role is handy together with Repositories.

The **Repositories** are classes that represent in-memory collections of entities or value objects. The Repository is required for each Aggregate entity. It is up to the repository implementation to decide how to persist the entity’s state, how to find, filter or load an object.

Next, the **Domain Services** encode complicated processes or procedures involving multiple entities, repositories and value objects. The services must not have any state, meaning that they only use Entities and Repositories to get the current state information.

## Conclusion

As existing wisdom suggests, you should know what different architectures are there and when to apply them. You should consider various alternatives and support your choice with appropriate reasoning. To me, learning about DDD changed the way I approach a fairly complicated iOS software development project. 

You shouldn’t use DDD in every project. According to the authors’ recommendations, it’s useful in big projects having at least 30 features. Also, it can be applied if the engineering team is unfamiliar with the technology or domain, or if the project has vague requirements that are changing throughout the project’s life. As I understand it, the DDD is more applicable to business applications than to systems software.

After having the DDD applied in a production iOS project, I can definitely say that this approach improves readability, maintainability, flexibility, and testability of the software. It helps to build modular software with each module having own subdomain model and a specific set of responsibilities.

The essence of the Domain-Driven Design is a Domain Model pattern. Its core components are Bounded Context, Entity, Value Object, Aggregate, Repository and Domain Service. All these roles combined together provide you with a toolbox to model an actual domain, in the language of the domain. I think it is a concept that you should definitely know about.

## Recommended Reading
- Evans, Eric (2004). Domain-Driven Design: Tackling Complexity in the Heart of Software. Addison-Wesley. ISBN 978-032-112521-7
- Vernon, Vaughn (2013). Implementing Domain-Driven Design. Addison-Wesley. ISBN 978-032-183457-7