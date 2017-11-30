---
title: "Vous concevez un modèle de domaine microservice"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Vous concevez un modèle de domaine microservice"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 455a2c5a39fb9b765b557610ab108f8c75882dbd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="designing-a-microservice-domain-model"></a>Vous concevez un modèle de domaine microservice

*Définir un modèle de domaine complet pour chaque entreprise microservice ou d’un contexte de limitées*

Votre objectif est de créer un modèle de domaine cohésif unique pour chaque entreprise microservice ou un contexte délimité (BC). Sachez, toutefois, qu’un BC ou business microservice peut parfois être composé de plusieurs services physiques qui partagent un modèle de domaine unique. Le modèle de domaine doit capturer les règles, le comportement, langage de l’entreprise et contraintes du seul contexte délimité ou microservice entreprise qu’elle représente.

## <a name="the-domain-entity-pattern"></a>Le modèle d’entité de domaine

Les entités représentent des objets de domaine et sont principalement définies par leur identité, la continuité des activités et la persistance au fil du temps et pas uniquement par les attributs qui les composent. Comme le dit, Eric Evans « objet principalement défini par son identité est appelé une entité ». Entités sont très importantes dans le modèle de domaine, car elles sont la base d’un modèle. Par conséquent, vous devez identifier et concevoir soigneusement.

*Identité de l’entité peut traverser plusieurs microservices ou limitées de contextes.*

La même identité (mais pas la même entité) peuvent être modélisées dans plusieurs contextes de limitées ou microservices. Toutefois, qui n’implique pas que la même entité, avec les mêmes attributs et logique serait être implémentée dans plusieurs contextes limitées. Au lieu de cela, les entités dans chaque contexte délimité limitent ses attributs et les comportements à ceux requis dans le domaine de ce contexte limitées.

Par exemple, l’entité de l’acheteur peut-être la plupart des attributs d’une personne qui sont définis dans l’entité d’utilisateur dans le microservice profil ou d’identité, y compris l’identité. Mais l’entité de l’acheteur dans l’ordre de tri microservice peut avoir moins d’attributs, car seules certaines données de l’acheteur sont associées au processus de commande. Le contexte de chaque microservice ou limitées affecte son modèle de domaine.

*Entités de domaine doivent implémenter le comportement en plus d’implémenter des attributs de données*

Une entité de domaine dans DDD doit implémenter la logique de domaine ou le comportement lié aux données d’entité (l’objet accédé dans la mémoire). Par exemple, dans le cadre d’une classe d’entité order vous devez disposer d’une logique métier et des opérations implémentées en tant que méthodes pour des tâches telles que l’ajout d’un élément de commande, la validation des données et le calcul du total. Les méthodes de l’entité, prenez soin des invariants et les règles de l’entité au lieu d’avoir ces règles réparties sur la couche application.

Figure 9-8 illustre une entité de domaine qui implémente non seulement des attributs de données, mais des opérations ou des méthodes avec une logique de domaine connexes.

![](./media/image9.png)

**Figure 9-8**. Exemple d’une entité de domaine concevoir l’implémentation de données plus de comportement

Bien entendu, vous pouvez parfois avoir les entités qui n’implémentent pas une logique dans le cadre de la classe d’entité. Cela peut se produire dans les entités enfants au sein d’un agrégat si l’entité enfant n’a pas une logique spéciale, car la plupart de la logique est défini à la racine d’agrégation. Si vous avez un microservice complexe qui contient beaucoup de logique implémentée dans les classes de service au lieu de dans les entités de domaine, vous pourriez tomber dans le modèle de domaine anemic, expliqué dans la section suivante.

### <a name="rich-domain-model-versus-anemic-domain-model"></a>Modèle de domaine riche et le modèle de domaine anemic

Dans son emploi [AnemicDomainModel](https://martinfowler.com/bliki/AnemicDomainModel.html), Martin Fowler décrit un modèle de domaine anemic de cette façon :

Le problème de base d’un modèle de domaine Anemic est qu’à première vue il ressemble à la réalité. Il existe des objets, nombreux nommée d’après les noms dans l’espace de noms et ces objets sont connectés avec les relations riches et de la structure qui ont des modèles de domaine true. Catch est fourni lorsque vous examinez le comportement, et vous Sachez qu’il y a aucun comportement de ces objets, ce qui les rend peu plus de sacs d’accesseurs Get et Set.

Bien entendu, lorsque vous utilisez un modèle de domaine anemic, ces modèles de données utilisées à partir d’un ensemble d’objets de service (généralement nommé le *couche métier*) qui capture toute la logique de domaine ou d’entreprise. La couche métier reposant sur le modèle de données et utilise le modèle de données comme données.

Le modèle de domaine anemic est simplement une conception de style procédurale. Objets d’entité anemic ne sont pas des objets réels, car ils ne disposent pas de comportement (méthodes). Elles contiennent uniquement des propriétés de données et il est donc pas conception orientée objet. En plaçant le comportement de tous les charge dans des objets de service (la couche métier) vous essentiellement au final [code spaghetti](https://en.wikipedia.org/wiki/Spaghetti_code) ou [des scripts de transaction](https://martinfowler.com/eaaCatalog/transactionScript.html), et par conséquent, vous perdez les avantages un modèle de domaine fournit.

Peu importe, si votre contexte de limitées ou de microservice est très simple (un service CRUD), le modèle de domaine anemic sous la forme d’objets d’entité avec seulement les propriétés de données peut être suffisante, et il peut être intéressant d’implémenter des modèles DDD plus complexes. Dans ce cas, il sera simplement un modèle de persistance, car vous avez intentionnellement créé une entité uniquement les données à des fins CRUD.

C’est pourquoi les architectures microservices sont parfaites pour une approche architecturale multiples en fonction de chaque contexte délimité. Par exemple, dans eShopOnContainers, le tri microservice implémente les modèles DDD, mais le catalogue microservice, qui est un service CRUD simple, n’est pas.

Certaines personnes dire que le modèle de domaine anemic est un anti-modèle. Il dépend vraiment ce que vous implémentez. Si le microservice que vous créez est très simple (par exemple, un service CRUD), suivant le modèle de domaine anemic n’est pas un anti-modèle. Toutefois, si vous avez besoin attaquer la complexité du domaine d’un microservice qui possède un grand nombre de règles d’entreprise en constante évolution, le modèle de domaine anemic peut être un anti-modèle pour ce microservice ou d’un contexte de limitées. Dans ce cas, de la conception en tant qu’une riche modèle avec les entités contenant des données plus comportement ainsi que pour implémenter des modèles DDD supplémentaires (agrégats, les objets de valeur, etc.) peut offrir des avantages significatifs pour le succès à long terme d’une telle microservice.

#### <a name="additional-resources"></a>Ressources supplémentaires

-   **DevIQ. Entité de domaine**
    [*http://deviq.com/entity/*](http://deviq.com/entity/)

-   **Martin Fowler. Le modèle de domaine**
    [*https://martinfowler.com/eaaCatalog/domainModel.html*](https://martinfowler.com/eaaCatalog/domainModel.html)

-   **Martin Fowler. Le modèle de domaine Anemic**

    <https://martinfowler.com/bliki/AnemicDomainModel.HTML>

### <a name="the-value-object-pattern"></a>Le modèle d’objet de valeur

Notée Eric Evans, « nombre d’objets n’aient pas conceptuelle identité. Ces objets décrivent certaines caractéristiques d’une chose ».

Une entité requiert une identité, mais il existe de nombreux objets dans un système qui ne le faites pas, comme le modèle d’objet de valeur. Un objet de valeur est un objet avec aucune identité conceptuel qui décrit un aspect de domaine. Ce sont des objets que vous instancier pour représenter des éléments de conception qui seulement vous concernent temporairement. Vous vous souciez *que* pas qu’ils sont *qui* qu’ils le sont. Exemples incluent des nombres et les chaînes, mais peuvent être également les concepts de niveau supérieur tels que les groupes d’attributs.

Un élément qui est une entité dans un microservice peut-être pas une entité dans un autre microservice, étant donné que dans le deuxième cas, le contexte délimité peut avoir une signification différente. Par exemple, une adresse dans une application de commerce électronique peut-être pas une identité, car il peut représenter uniquement un groupe d’attributs de profil du client pour une personne ou une entreprise. Dans ce cas, l’adresse doit être classé comme un objet de valeur. Toutefois, dans une application pour une société d’énergie électrique, l’adresse du client peut être important pour le domaine d’entreprise. Par conséquent, l’adresse doit avoir une identité pour le système de facturation peut être lié directement à l’adresse. Dans ce cas, une adresse doit être classée comme une entité de domaine.

Une personne avec un nom et le nom de famille est généralement une entité, car une personne possède une identité, même si le nom et le nom de famille coïncident avec un autre ensemble de valeurs, par exemple si ces noms fait également référence à une autre personne.

Les objets de valeur sont difficiles à gérer dans les bases de données relationnelles et ORM comme EF, tandis que dans le document orientée services qu’ils sont plus faciles à implémenter et utiliser des bases de données.

#### <a name="additional-resources"></a>Ressources supplémentaires

-   **Martin Fowler. Modèle d’objet de valeur**
    [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)

-   **Valeur d’objet**
    [*http://deviq.com/value-object/*](http://deviq.com/value-object/)

-   **Valeur des objets dans le développement piloté par tests**
    [*https://leanpub.com/tdd-ebook/read\#objets leanpub-auto-valeur*](https://leanpub.com/tdd-ebook/read#leanpub-auto-value-objects)

-   **Eric Evans. Conception domaine : Tackling Complexity in the Heart of Software.** (Livre et en savoir plus sur les objets de valeur) [ *https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

### <a name="the-aggregate-pattern"></a>Le modèle d’agrégation

Un modèle de domaine contient des clusters des entités de données différentes et des processus qui peuvent contrôler une zone importante de fonctionnalités, telles que son traitement ou de l’inventaire. Une unité DDD plus affinée est l’agrégation, qui décrit un cluster ou un groupe d’entités et les comportements qui peuvent être traitées comme une unité cohésive.

Vous définissez généralement un agrégat basé sur les transactions dont vous avez besoin. Un exemple classique est une commande qui contient également une liste d’éléments de la commande. Un élément de commande seront généralement une entité. Mais il s’agit d’une entité enfant au sein de l’agrégat de commande qui contient également l’entité order comme son entité racine, généralement appelée une racine d’agrégat.

Identification des agrégats peut être difficile. Un agrégat est un groupe d’objets qui doivent être cohérentes entre eux, mais vous ne peut pas simplement de sélectionner un groupe d’objets et de les étiqueter un agrégat. Vous devez commencer par un concept de domaine et de réflexion sur les entités qui sont utilisées dans les transactions les plus courantes liées à ce concept. Les entités qui doivent être cohérentes sont ce qui constitue un agrégat. Concernant les opérations de la transaction est probablement la meilleure façon d’identifier des agrégats.

### <a name="the-aggregate-root-or-root-entity-pattern"></a>Le modèle racine d’agrégation ou d’entité racine

Un agrégat est composé d’au moins une entité : la racine d’agrégation, également appelée entité racine ou ientity principal. En outre, il peut avoir plusieurs entités enfants et des objets de valeur, avec toutes les entités et les objets fonctionnent conjointement pour implémenter des transactions et le comportement requis.

Une racine d’agrégat vise à garantir la cohérence de l’agrégat ; Il doit être le seul point d’entrée pour les mises à jour de l’agrégat via les méthodes ou les opérations dans l’agrégat des classe racine. Vous devez apporter des modifications aux entités au sein de l’agrégat uniquement via la racine d’agrégation. Il est guardian de cohérence de l’agrégat, compte tenu de tous les invariants et vous pouvez avoir besoin pour se conformer à votre regroupement de règles de cohérence. Si vous modifiez un objet d’entité ou une valeur enfant indépendamment, la racine d’agrégation ne peut pas garantir que l’agrégat est dans un état valide. Il serait telles qu’une table avec une section libre. Mise à jour de la cohérence est la principale utilité de la racine d’agrégation.

Dans la Figure 9-9, vous pouvez voir des agrégats d’exemple à l’acheteur d’agrégation, qui contient une seule entité (la racine d’agrégation acheteur). L’agrégat de commande contient plusieurs entités et un objet de valeur.

![](./media/image10.png)

**Figure 9-9**. Exemple d’agrégats avec plusieurs ou unique des entités

Notez que l’agrégat de l’acheteur peut avoir des entités enfants supplémentaires, en fonction de votre domaine, comme dans l’ordre de tri microservice dans l’application de référence eShopOnContainers. Figure 9-9 illustre simplement un cas dans lequel l’acheteur dispose d’une entité unique, par exemple, pour un agrégat qui contient uniquement une racine d’agrégat.

Afin de maintenir la séparation des agrégats et conserver des limites claires entre eux, il est conseillé dans un modèle de domaine DDD pour interdire la navigation directe entre les agrégats et uniquement avec le champ de clé étrangère (FK), tel qu’implémenté dans le [ Classement du modèle de domaine microservice](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs) dans eShopOnContainers. L’entité Order a uniquement un champ FK pour l’acheteur, mais pas une propriété de navigation EF Core, comme indiqué dans le code suivant :

```csharp
public class Order : Entity, IAggregateRoot
{
    private DateTime _orderDate;
    public Address Address { get; private set; }
    private int? _buyerId; //FK pointing to a different aggregate root
    public OrderStatus OrderStatus { get; private set; }
}
```

Identification et l’utilisation d’agrégats nécessitent la recherche et l’expérience. Pour plus d’informations, consultez la liste des ressources supplémentaires suivantes.

#### <a name="additional-resources"></a>Ressources supplémentaires

-   **Vaughn Vernon. Conception d’agrégation efficace - partie i : un agrégat unique de modélisation**
    [*https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD\_Communauté\_essai\_ AGRÉGATS\_partie\_pdf de 1.*](https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_1.pdf)

-   **Vaughn Vernon. Conception d’agrégation efficace - la partie II : Fabrication agrégats fonctionnent ensemble**
    *<https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_2.pdf>*

-   **Vaughn Vernon. Conception d’agrégation efficace - partie III : Obtenir des informations via la détection**
    *<https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_3.pdf>*

-   **Sergey Grybniak. Modèles de conception tactiques DDD**
    [*https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part*](https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part)

-   **Chris Richardson. Développement de Microservices transactionnelle à l’aide d’agrégats**
    [*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson)

-   **DevIQ. Le modèle d’agrégation**
    [*http://deviq.com/aggregate-pattern/*](http://deviq.com/aggregate-pattern/)


>[!div class="step-by-step"]
[Précédente] (ddd-orientée-microservice.md) [suivant] (net-core-microservice-domaine-model.md)
