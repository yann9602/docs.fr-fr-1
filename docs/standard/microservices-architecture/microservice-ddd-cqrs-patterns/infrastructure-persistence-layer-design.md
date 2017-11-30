---
title: "Conception de la couche de persistance d’infrastructure"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Conception de la couche de persistance d’infrastructure"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: ce0f1d608eed909a7707f3c580afc5253f3eef06
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="designing-the-infrastructure-persistence-layer"></a>Conception de la couche de persistance d’infrastructure

Composants de persistance de données fournissent un accès aux données hébergées dans les limites d’un microservice (autrement dit, base de données d’un microservice). Ils contiennent l’implémentation réelle de composants tels que les référentiels et [unité de travail](http://martinfowler.com/eaaCatalog/unitOfWork.html) les classes, comme les DBContexts EF personnalisé.

## <a name="the-repository-pattern"></a>Le modèle de référentiel

Référentiels sont des classes ou des composants qui encapsulent la logique nécessaire pour accéder aux sources de données. Ils centralisent les données access des fonctionnalités communes, en fournissant une meilleure facilité de maintenance et le découplage de l’infrastructure ou la technologie utilisée pour accéder aux bases de données à partir de la couche de modèle de domaine. Si vous utilisez un ORM comme Entity Framework, le code qui doit être implémenté est simplifié grâce à LINQ et un typage fort. Cela vous permet de vous concentrer sur la logique de persistance des données plutôt que sur les données d’accès plomberie.

Le modèle de référentiel est une façon bien documentée de l’utilisation de la source de données. Dans le carnet de [modèles d’Architecture d’Application Enterprise](https://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420/), Martin Fowler décrit un référentiel comme suit :

Un référentiel effectue les tâches d’intermédiaire entre les couches de modèle de domaine et le mappage de données, qui agit de manière similaire à un ensemble d’objets de domaine dans la mémoire. Les objets de client générer des requêtes de façon déclarative et les envoyer vers les référentiels pour obtenir des réponses. Point de vue conceptuel, un référentiel encapsule un ensemble d’objets stockés dans la base de données et les opérations qui peuvent être effectuées sur ces derniers, en fournissant un moyen plus proche de la couche de persistance. Référentiels, également, prend en charge que l’objectif de séparation, clairement et dans un sens, la dépendance entre le domaine de travail et l’allocation de données ou d’un mappage.

### <a name="define-one-repository-per-aggregate"></a>Définir un référentiel par l’agrégat

Pour chaque racine d’agrégation ou d’agrégation, vous devez créer une classe de référentiel. Dans un microservice basée sur des modèles de conception domaine, le canal uniquement, que vous devez utiliser pour mettre à jour la base de données doit être les référentiels. Il s’agit, car ils ont une relation avec la racine d’agrégation, qui contrôle la cohérence transactionnelle et les invariants de l’agrégat. Il est OK interroger la base de données à travers les autres canaux (comme vous pouvez le faire suivant une approche CQRS), car elles ne changent pas l’état de la base de données. Toutefois, la zone transactionnelle, les mises à jour, doivent toujours être contrôlés par les référentiels et les racines d’agrégat.

En fait, un référentiel vous permet de remplir les données dans la mémoire provenant de la base de données sous la forme d’entités de domaine. Une fois les entités en mémoire, elles peuvent être modifiées et puis persistantes dans la base de données à des transactions.

Comme indiqué précédemment, si vous utilisez le modèle architectural CQS/CQRS, les requêtes initiales seront effectuées par les requêtes côté hors du modèle de domaine, effectuées par des instructions SQL simples à l’aide de Dapper. Cette approche est beaucoup plus souple que référentiels, car vous pouvez interroger et joindre des tables que vous devez, et ces requêtes ne sont pas limitées par les règles à partir d’agrégats. Ces données passera à l’application de client ou de la couche présentation.

Si l’utilisateur apporte des modifications, les données à mettre à jour proviendront de la couche d’application ou une présentation de client à la couche application (par exemple, un service Web API). Lorsque vous recevez une commande (avec des données) dans un gestionnaire de commandes, vous utilisez des référentiels pour obtenir les données que vous souhaitez mettre à jour à partir de la base de données. Vous mettre à jour en mémoire avec les informations passées avec les commandes, et vous pouvez ensuite ajouter ou de mettre à jour les données (entités de domaine) dans la base de données via une transaction.

Nous devons mettre en évidence à nouveau que seul référentiel doit être défini pour chaque racine d’agrégat, comme indiqué dans la Figure 9-17. Pour atteindre l’objectif de la racine d’agrégation pour maintenir la cohérence transactionnelle entre tous les objets au sein de l’agrégat, vous ne devez jamais créer un référentiel pour chaque table dans la base de données.

![](./media/image18.png)

**Figure 9-17**. La relation entre les référentiels, les agrégats et les tables de base de données

### <a name="enforcing-one-aggregate-root-per-repository"></a>En appliquant une racine d’agrégation par référentiel

Il peut être utile pour implémenter la conception de votre référentiel de sorte qu’il applique la règle que seules les racines d’agrégation doivent avoir des référentiels. Vous pouvez créer un type générique ou de base de référentiel qui limite le type d’entité associé pour vous assurer qu’ils ont l’interface de marqueur IAggregateRoot.

Par conséquent, chaque classe de référentiel implémenté au niveau de la couche d’infrastructure implémente son propre contrat ou une interface, comme indiqué dans le code suivant :

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class OrderRepository : IOrderRepository
    {
```

Chaque interface du référentiel spécifique implémente l’interface IRepository générique :

```csharp
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);
    // ...
}
```

Toutefois, pour que le code d’appliquer la convention d’assurer un meilleur que chaque référentiel doit être lié à un agrégat unique serait d’implémenter un type de référentiel générique afin qu’il soit explicite que vous utilisez un référentiel pour cibler un regroupement spécifique. Cela peut se faire facilement en implémentant ce générique dans l’interface de base IRepository, comme dans le code suivant :

```csharp
  public interface IRepository<T> where T : IAggregateRoot
```

### <a name="the-repository-pattern-makes-it-easier-to-test-your-application-logic"></a>Le modèle de référentiel rend plus faciles à tester votre logique d’application

Le modèle de référentiel vous permet de tester facilement votre application avec des tests unitaires. N’oubliez pas que les tests unitaires uniquement tester votre code, l’infrastructure pas sorte que les abstractions de référentiel plus faciles à atteindre cet objectif.

Comme indiqué dans la section précédente, il est recommandé que vous définissez et placez les interfaces de référentiel dans la couche de modèle de domaine afin que la couche d’application (par exemple, votre microservice API Web) ne dépend pas directement de la couche d’infrastructure, dans laquelle vous avez mis en œuvre les classes du référentiel réel. Par cette opération et à l’aide de l’Injection de dépendances dans les contrôleurs de votre API Web, vous pouvez implémenter des référentiels fictives qui retournent des données fictives au lieu des données à partir de la base de données. Qu’approche découplée vous permet de créer et de tests unitaires d’exécution qui peuvent tester uniquement la logique de votre application sans nécessiter de connectivité à la base de données.

Connexions aux bases de données peuvent échouer et, plus important, des centaines de tests en cours d’exécution par rapport à une base de données est incorrect pour deux raisons. Tout d’abord, il peut prendre beaucoup de temps en raison du grand nombre de tests. En second lieu, les enregistrements de base de données peuvent modifier et affecter les résultats de vos tests, afin qu’ils ne peuvent pas être cohérents. Test par rapport à la base de données n’est pas une unité de tests, mais que des tests d’une intégration. Vous devez disposer de nombreux tests unitaires en cours d’exécution rapide, mais moins d’intégration des tests sur les bases de données.

En termes de séparation des problèmes pour les tests unitaires, votre logique s’exécute sur les entités de domaine dans la mémoire. Il suppose que la classe du référentiel a livré les. Une fois que votre logique modifie les entités de domaine, il suppose que la classe de référentiel stockera les correctement. Le point important ici consiste à créer des tests unitaires sur votre modèle de domaine et de sa logique de domaine. Racines d’agrégat sont les limites de cohérence principal dans DDD.

### <a name="the-difference-between-the-repository-pattern-and-the-legacy-data-access-class-dal-class-pattern"></a>La différence entre le modèle de référentiel et le modèle de classe (classe de la couche DAL) accès aux données hérité

Un objet d’accès aux données exécute directement des opérations d’accès et la persistance des données sur le stockage. Marques de référentiel les données avec les opérations que vous souhaitez effectuer dans la mémoire d’une unité de l’objet de travail (par exemple, EF lorsque vous utilisez le DbContext), mais ces mises à jour ne seront pas effectuées immédiatement.

Une unité de travail est appelée comme une unique transaction qui implique plusieurs insert, update ou delete operations. En termes simples, cela signifie que, pour une action utilisateur spécifique (par exemple, l’inscription sur un site Web), tous les insert, update et delete transactions sont gérées dans une transaction unique. Cela est plus efficace que la gestion des transactions de base de données multiples d’une manière chattier.

Ces opérations de persistance plusieurs seront effectuées ultérieurement en une seule action lorsque votre code à partir de la couche application commandes il. La décision relative à l’application des modifications en mémoire pour le stockage de base de données est généralement basée sur le [modèle d’unité de travail](http://martinfowler.com/eaaCatalog/unitOfWork.html). Dans EF, le modèle de l’unité de travail est implémenté en tant que le DBContext.

Dans de nombreux cas, ce modèle ou la façon d’appliquer des opérations sur le stockage peut augmenter les performances de l’application et réduire le risque d’incohérences. En outre, elle réduit le blocage dans les tables de base de données, de transaction, car toutes les opérations prévues sont validées dans le cadre d’une transaction. C’est plus efficace, par opposition à l’exécution de nombreuses opérations isolées par rapport à la base de données. Par conséquent, le ORM sélectionné sera optimiser l’exécution par rapport à la base de données en regroupant plusieurs actions de mise à jour dans la même transaction, au lieu de plusieurs exécutions de transaction distincts et de petite taille.

### <a name="repositories-should-not-be-mandatory"></a>Référentiels ne doivent pas être obligatoires

Les dépôts personnalisés sont utiles pour les raisons cités précédemment, et qui est l’approche pour le tri microservice dans eShopOnContainers. Toutefois, il n’est pas un modèle essentiel à implémenter dans une conception orientée ou même en général de développement dans .NET.

Par exemple, Jimmy Bogard, lorsque vous fournissez des commentaires directement dans ce guide, on dit que les éléments suivants :

Cela serez probablement mes commentaires plus grands. Je ne suis vraiment pas un ventilateur de référentiels, principalement car ils masquent les détails importants du mécanisme de persistance sous-jacentes. Son pourquoi passer pour MediatR pour les commandes, trop. Je peux utiliser toute la puissance de la couche de persistance et transmettre des tout comportement de ce domaine à mes racines d’agrégat. Je ne souhaite généralement simuler mes dépôts : j’ai encore besoin d’avoir que l’intégration test avec la réalité. Va CQRS signifiait que nous n’a pas vraiment avez besoin pour les référentiels plus.

Nous trouver référentiels utile, mais nous reconnaissez qu’ils ne sont pas critiques pour votre DDD, dans la façon dont le modèle d’agrégation et le modèle de domaine complet. Par conséquent, utilisez le modèle de référentiel ou non, comme vous le voir s’ajuster.

#### <a name="additional-resources"></a>Ressources supplémentaires

##### <a name="the-repository-pattern"></a>Le modèle de référentiel

-   **Edward Hieatt et Rob me. Modèle de référentiel. ** 
     [ *http://martinfowler.com/eaaCatalog/repository.html*](http://martinfowler.com/eaaCatalog/repository.html)

-   **Le modèle de référentiel**
    [*https://msdn.microsoft.com/en-us/library/ff649690.aspx*](https://msdn.microsoft.com/en-us/library/ff649690.aspx)

-   **Modèle de référentiel : Une persistance abstraction de données**
    [*http://deviq.com/repository-pattern/*](http://deviq.com/repository-pattern/)

-   **Eric Evans. Conception domaine : Tackling Complexity in the Heart of Software.** (Livre et en savoir plus sur le modèle de référentiel) [ *https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

##### <a name="unit-of-work-pattern"></a>Unité de modèle de travail

-   **Martin Fowler. Unité de modèle de travail. ** 
     [ *http://martinfowler.com/eaaCatalog/unitOfWork.html*](http://martinfowler.com/eaaCatalog/unitOfWork.html)

<!-- -->

-   **Implémentation du référentiel et une unité de travail des modèles dans une Application ASP.NET MVC**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/ Implementing-the-Repository-and-Unit-of-Work-Patterns-in-an-ASP-NET-MVC-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)


>[!div class="step-by-step"]
[Précédente] (domaine-événements-design-implementation.md) [suivant] (infrastructure-persistence-layer-implemenation-entity-framework-core.md)
