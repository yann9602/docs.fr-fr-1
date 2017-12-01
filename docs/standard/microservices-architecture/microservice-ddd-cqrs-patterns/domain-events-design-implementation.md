---
title: "Événements de domaine. Conception et implémentation"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Événements de domaine, de conception et implémentation"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 2d98b302be4ee72d8225526944fc3e41cbadcb5f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="domain-events-design-and-implementation"></a>Événements de domaine : conception et implémentation

Événements de domaine permet d’implémenter explicitement des effets des modifications de votre domaine. Dans d’autres mots et à l’aide de la terminologie DDD, utilisez les événements de domaine d’implémenter explicitement des effets secondaires sur plusieurs regroupements. Si vous le souhaitez, pour une meilleure évolutivité et moins d’impact sur les verrous de base de données, utilisez la cohérence éventuelle entre les agrégats au sein du même domaine.

## <a name="what-is-a-domain-event"></a>Qu’est un événement de domaine ?

Un événement est un élément qui s’est produite dans le passé. Un événement de domaine est logiquement, quelque chose qui s’est produite dans un domaine particulier, et quelque chose vous souhaitez d’autres parties du même domaine (-process) pour connaître et potentiellement réagir à.

Un avantage important d’événements de domaine est que les effets secondaires après qu’un problème est survenu dans un domaine peut être exprimés explicitement au lieu de manière implicite. Ces effets doivent être cohérentes pour soit toutes les opérations relatives à la tâche d’entreprise se produisent de côté, ou aucun d'entre eux. En outre, les événements de domaine permettent une meilleure séparation nette entre les classes dans le même domaine.

Par exemple, si vous utilisez simplement simplement les Entity Framework et les entités ou les agrégats de même, s’il faut effets causées par un cas d’usage, celles seront implémentées comme un concept implicit dans le code couplé après qu’un problème est survenu. Toutefois, si vous voyez uniquement ce code, vous ne savez pas si ce code (comme effet secondaire) fait partie de l’opération principale ou s’il s’agit réellement d’un effet secondaire. En revanche, à l’aide d’événements de domaine rend le concept explicite et dans le cadre du langage omniprésent. Par exemple, dans l’application eShopOnContainers, création d’une commande n’est pas simplement sur la commande. Il met à jour ou crée un acheteur d’agrégation en fonction de l’utilisateur d’origine, car l’utilisateur n’est pas un acheteur jusqu'à ce qu’il existe une commande en vigueur. Si vous utilisez des événements de domaine, vous pouvez exprimer explicitement cette règle de domaine dans le langage omniprésent fournie par les experts de domaine.

Événements de domaine sont quelque peu similaires aux événements de style de messagerie, avec une différence importante. Avec messagerie réel, message queuing, brokers de message ou un bus de service à l’aide de AMPQ, un message est toujours envoyé de manière asynchrone et communiqué à travers des processus et des ordinateurs. Cela est utile pour l’intégration de plusieurs contextes de délimitée, microservices ou même différentes applications. Toutefois, avec les événements de domaine, vous souhaitez déclencher un événement à partir de l’opération de domaine en cours d’exécution, mais que vous souhaitez que les effets secondaires se produisent dans le même domaine.

Les événements de domaine et leurs effets secondaires (les actions déclenchées par la suite qui sont gérées par les gestionnaires d’événements) doit se produire presque immédiatement, généralement in-process et dans le même domaine. Par conséquent, les événements de domaine peuvent être synchrone ou asynchrone. Événements d’intégration, toutefois, doivent toujours être asynchrones.

## <a name="domain-events-versus-integration-events"></a>Événements de domaine par rapport aux événements d’intégration

Sémantiquement, les événements de domaine et d’intégration sont la même chose : des notifications sur un élément qui vient de se produire. Toutefois, leur implémentation doit être différente. Événements de domaine sont des messages uniquement vers un répartiteur d’événements de domaine, qui peut être implémenté comme un médiateur en mémoire basé sur un conteneur inversion de contrôle ou toute autre méthode.

En revanche, des événements d’intégration vise à propager les transactions validées et mises à jour des sous-systèmes supplémentaires, qu’ils soient autres microservices, les contextes de limitées ou les applications externes même. Par conséquent, ils doivent se produire uniquement si l’entité est rendue persistante avec succès, depuis dans de nombreux scénarios en cas d’échec, l’opération entière jamais s’est produite.

En outre et comme indiquée, intégration événements doivent être basés sur la communication asynchrone entre plusieurs microservices (autres contextes délimitée) ou systèmes externes même et d’applications. Par conséquent, l’interface de bus d’événements a besoin de certaines infrastructure qui permet de processus entre et distribués de communication entre services potentiellement à distance. Il peut reposer sur un bus des services commerciaux, les files d’attente, une base de données partagée utilisée comme une boîte aux lettres ou n’importe quel autre distribué et push dans l’idéal, de système de messagerie basée sur.

## <a name="domain-events-as-a-preferred-way-to-trigger-side-effects-across-multiple-aggregates-within-the-same-domain"></a>Événements de domaine par défaut afin de déclencher des effets secondaires sur plusieurs regroupements au sein du même domaine

Si l’exécution d’une commande liée à une instance d’agrégation requiert des règles de domaine supplémentaire à exécuter sur un ou plusieurs agrégats supplémentaires, vous devez concevoir et implémenter ces effets secondaires doit être déclenchée par les événements de domaine. Comme indiqué dans la Figure 9-14 et comme l’un des principaux cas d’utilisation, un événement de domaine doit être utilisé pour propager les modifications d’état entre plusieurs agrégats dans le même modèle de domaine.

![](./media/image15.png)

**Figure 9-14**. Événements de domaine pour appliquer la cohérence entre plusieurs agrégats dans le même domaine

Dans l’illustration, lorsque l’utilisateur lance une commande, l’événement de domaine OrderStarted déclenche la création d’un objet de l’acheteur dans l’ordre de tri microservice, selon les informations utilisateur d’origine à partir de l’identité de microservice (avec les informations fournies dans la commande CreateOrder). L’événement de domaine est généré par l’agrégat de la commande lorsqu’elle est créée en premier lieu.

Vous pouvez également avoir la racine d’agrégation inscrit pour les événements déclenchés par les membres de son agrégats (entités enfants). Par exemple, chaque entité d’enfant OrderItem peut déclencher un événement lorsque le prix est supérieur à une quantité spécifique, ou lorsque le montant de l’élément est trop élevé. La racine d’agrégation peut ensuite recevoir ces événements et effectuer un calcul global ou une agrégation.

Il est important de comprendre que cette communication basée sur les événements n’est pas implémentée directement dans les fonctions d’agrégation ; Vous devez implémenter des gestionnaires d’événements de domaine. Gestion des événements de domaine sont un problème d’application. La couche de modèle de domaine doit se concentrer uniquement sur la logique de domaine, les éléments par un expert du domaine, pas infrastructure d’application telles que les gestionnaires et les actions de persistance de l’effet secondaire à l’aide de référentiels. Par conséquent, le niveau de la couche application est où vous devez avoir des gestionnaires d’événements de domaine déclenchent des actions lorsqu’un événement de domaine est déclenché.

Événements de domaine peuvent également servir à déclencher des actions de l’application, et ce qui est plus important, doit être ouvert pour augmenter ce nombre dans le futur d’une manière découplée. Par exemple, l’ordre de démarrage, vous souhaiterez publier un événement de domaine pour propager ces informations à d’autres fonctions d’agrégation ou même à déclencher des actions telles que les notifications.

Le point essentiel est le nombre ouvrir des actions à exécuter lorsqu’un événement de domaine se produit. Finalement, les actions et les règles dans le domaine et l’application augmente. La complexité ou le nombre d’actions d’effet lorsque quelque chose se produit augmente, mais si votre code a été couplé avec le type « glue » (autrement dit, simplement l’instanciation d’objets avec le mot clé new dans C\#), vous devez à chaque fois que vous avez besoin d’ajouter une nouvelle action modifier le code d’origine. Cela peut entraîner nouveaux bogues, étant donné que chaque nouvelle exigence, vous devez modifier le flux de code d’origine. Cela va à l’encontre du [principe ouvert/fermé](https://en.wikipedia.org/wiki/Open/closed_principle) de [solide](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design)). N’est pas la classe d’origine qui a été orchestrer les opérations serait croître et croître, ce qui va à l’encontre du [principe de responsabilité unique (SRP)](https://en.wikipedia.org/wiki/Single_responsibility_principle).

En revanche, si vous utilisez des événements de domaine, vous pouvez créer une implémentation affinée et découplée en séparant les responsabilités à l’aide de cette approche :

1.  Envoyer une commande (par exemple, CreateOrder).
2.  Recevoir la commande dans un gestionnaire de commandes.
    -   Exécuter les transactions d’un agrégat unique.
    -   (Facultatif) Déclencher des événements de domaine pour les effets secondaires (par exemple, OrderStartedDomainDvent).
1.  Handle de domaine (dans le processus en cours), les événements thast s’exécute un nombre ouvert d’effets secondaires dans plusieurs agrégats ou des actions de l’application. Exemple :
    -   Vérifiez ou créez la méthode acheteur et de paiement.
    -   Créer et envoyer un événement d’intégration connexes pour le bus d’événements se propager les États sur microservices ou un déclencheur actions externes telles qu’envoyant un e-mail à l’acheteur.
    -   Gérer d’autres effets secondaires.

Comme indiqué dans la Figure 9-15, en commençant à partir du même événement de domaine, vous pouvez gérer plusieurs actions liées à d’autres fonctions d’agrégation dans le domaine ou les actions d’application supplémentaires que vous devez effectuer sur la connexion avec le bus d’événements et les événements d’intégration de microservices.

![](./media/image16.png)

**Figure 9-15**. Gestion de plusieurs actions par domaine

Les gestionnaires d’événements sont en général dans la couche application, car vous allez utiliser les objets d’infrastructure comme référentiels ou une API d’application pour le comportement de la microservice. Dans ce sens, les gestionnaires d’événements sont similaires aux gestionnaires de commandes, pour que tous deux partie de la couche application. La principale différence est qu’une commande doit être traitée une seule fois. Un événement de domaine peut être traité de zéro ou  *n*  délai d’attente, car si peut être reçu par plusieurs récepteurs ou des gestionnaires d’événements avec un objectif différent pour chaque gestionnaire.

La possibilité d’un nombre ouvert de gestionnaires par événement de domaine vous permet d’ajouter plusieurs règles de domaine plus sans affecter votre code en cours. Par exemple, la mise en œuvre de la règle d’entreprise suivant qui doit se produire droite après un événement peut être aussi simple que l’ajout de plusieurs gestionnaires d’événements (ou même un seul) :

Lorsque le montant total acheté par un client dans le magasin, sur n’importe quel nombre de commandes, dépasse 6 000 $, appliquer une remise de 10 % à chaque nouvelle commande et avertir le client avec une adresse de messagerie sur cette remise pour les commandes futures.

## <a name="implementing-domain-events"></a>Implémenter des événements de domaine

En c#, un événement de domaine est simplement une structure de données-exploitation ou classe, comme un DTO, toutes les informations relatives à ce que simplement s’est produite dans le domaine, comme indiqué dans l’exemple suivant :

```csharp
public class OrderStartedDomainEvent : IAsyncNotification
{
    public int CardTypeId { get; private set; }
    public string CardNumber { get; private set; }
    public string CardSecurityNumber { get; private set; }
    public string CardHolderName { get; private set; }
    public DateTime CardExpiration { get; private set; }
    public Order Order { get; private set; }

    public OrderStartedDomainEvent(Order order,
        int cardTypeId, string cardNumber,
        string cardSecurityNumber, string cardHolderName,
        DateTime cardExpiration)
    {
        Order = order;
        CardTypeId = cardTypeId;
        CardNumber = cardNumber;
        CardSecurityNumber = cardSecurityNumber;
        CardHolderName = cardHolderName;
        CardExpiration = cardExpiration;
    }
}
```

Il s’agit essentiellement d’une classe qui conserve toutes les données associées à l’événement OrderStarted.

En termes de langage omniprésent du domaine, dans la mesure où un événement est quelque chose qui se sont produits dans le passé, le nom de classe de l’événement doit être représenté comme un verbe passé, tels que OrderStartedDomainEvent ou OrderShippedDomainEvent. Qui est l’implémentation de l’événement de domaine dans l’ordre de tri microservice dans eShopOnContainers.

Comme nous l’avons indiqué, une caractéristique importante d’événements qui est dans la mesure où un événement est quelque chose qui se sont produits dans le passé, il ne doit pas modifier. Par conséquent, il doit être une classe immuable. Vous pouvez voir dans le code précédent qui a les propriétés sont en lecture seule à partir d’en dehors de l’objet. La seule façon de mettre à jour de l’objet est via le constructeur lorsque vous créez l’objet d’événement.

### <a name="raising-domain-events"></a>Le déclenchement d’événements de domaine

La question suivante consiste à déclencher un événement de domaine afin qu’il atteint ses gestionnaires d’événements connexes. Vous pouvez utiliser plusieurs approches.

UDI Dahan proposée à l’origine (par exemple, dans plusieurs liées billets, tel que [domaine événements – prendre 2](http://udidahan.com/2008/08/25/domain-events-take-2/)) à l’aide d’une classe statique pour la gestion et le déclenchement d’événements. Cela peut inclure une classe statique nommée DomainEvents qui déclenche des événements de domaine immédiatement lorsqu’elle est appelée, à l’aide de la syntaxe comme DomainEvents.Raise (événement myEvent). Jimmy Bogard a écrit un billet de blog ([renforcer votre domaine : événements de domaine](https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/)) qui recommande une approche similaire.

Toutefois, lorsque la classe d’événements de domaine est statique, il également distribue aux gestionnaires immédiatement. Cela, test et de débogage plus difficile, car les gestionnaires d’événements avec une logique des effets secondaires sont exécutées immédiatement après que l’événement est déclenché. Test et de débogage, vous souhaitez le focus sur uniquement ce qui se passe dans les classes d’agrégation en cours ; Vous ne souhaitez pas soudainement redirigé vers d’autres gestionnaires d’événements pour les effets liés à d’autres agrégats ou de la logique d’application. Il s’agit de raison pour laquelle les autres approches ont évolué, comme expliqué dans la section suivante.

#### <a name="the-deferred-approach-for-raising-and-dispatching-events"></a>L’approche différée pour déclencher et la distribution des événements

Au lieu de la distribution à un gestionnaire d’événements de domaine immédiatement, une meilleure approche consiste à ajouter les événements de domaine à une collection, puis à distribuer les événements de domaine *juste avant* ou *droit*  *une fois* validé la transaction (comme avec SaveChanges dans EF). (Cette approche a été décrit par Jimmy Bogard dans ce billet [un modèle d’événements domaine mieux](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/).)

Décider si vous envoyer les événements de domaine droite avant ou vers la droite après avoir validé la transaction est important, car il détermine si vous allez inclure les effets secondaires dans le cadre de la même transaction ou dans différentes transactions. Dans ce cas, vous devez traiter avec cohérence éventuelle entre plusieurs agrégats. Cette rubrique est décrite dans la section suivante.

L’approche différée est quel eShopOnContainers utilise. Tout d’abord, vous ajoutez les événements survenant dans vos entités dans une liste d’événements par l’entité ou la collection. Cette liste doit être la partie de l’objet entité, ou mieux encore, une partie de votre classe d’entité de base, comme indiqué dans l’exemple suivant :

```csharp
public abstract class Entity
{
    private List<IAsyncNotification> _domainEvents;

    public List<IAsyncNotification> DomainEvents => _domainEvents;

    public void AddDomainEvent(IAsyncNotification eventItem)
    {
        _domainEvents = _domainEvents ?? new List<IAsyncNotification>();
        _domainEvents.Add(eventItem);
    }

    public void RemoveDomainEvent(IAsyncNotification eventItem)
    {
        if (_domainEvents is null) return;
        _domainEvents.Remove(eventItem);
    }
    // ...
}
```

Lorsque vous souhaitez déclencher un événement, vous l’ajoutez simplement à la collection d’événements doit être placé dans une méthode d’agrégation d’entité, comme le montre le code suivant :

```csharp
var orderStartedDomainEvent = new OrderStartedDomainEvent(this, //Order object
    cardTypeId,
    cardNumber,
    cardSecurityNumber,
    cardHolderName,
    cardExpiration);
this.AddDomainEvent(orderStartedDomainEvent);
```

Notez que la seule chose qui effectue la méthode AddDomainEvent ajoute un événement à la liste. Aucun événement n’est encore déclenché et aucun gestionnaire d’événements n’est appelé encore.

En fait, vous souhaitez distribuer les événements plus tard, lorsque vous validez la transaction à la base de données. Si vous utilisez Entity Framework Core, cela signifie que dans la méthode SaveChanges de votre DbContext EF, comme dans le code suivant :

```csharp
// EF Core DbContext
public class OrderingContext : DbContext, IUnitOfWork
{
    // ...
    public async Task<int> SaveEntitiesAsync()
    {
        // Dispatch Domain Events collection.
        // Choices:
        // A) Right BEFORE committing data (EF SaveChanges) into the DB. This makes
        // a single transaction including side effects from the domain event
        // handlers that are using the same DbContext with Scope lifetime
        // B) Right AFTER committing data (EF SaveChanges) into the DB. This makes
        // multiple transactions. You will need to handle eventual consistency and
        // compensatory actions in case of failures.
        await _mediator.DispatchDomainEventsAsync(this);
        // After this line runs, all the changes (from the Command Handler and Domain
        // event handlers) performed through the DbContext will be commited
        var result = await base.SaveChangesAsync();
    }
}
```

Avec ce code, vous expédiez les événements de l’entité à leurs gestionnaires d’événements respectif.

Le résultat global est que vous avez séparé le déclenchement d’un événement de domaine (un simple ajouter dans une liste en mémoire) à partir de sa distribution à un gestionnaire d’événements. En outre, selon le type de l’expéditeur que vous utilisez, vous pourriez distribuer les événements de façon synchrone ou asynchrone.

N’oubliez pas que les limites transactionnelles entrent en important lire ici. Si votre unité de travail et de la transaction peut s’étendre sur plusieurs agrégats (comme lorsque vous utilisez EF Core et une base de données relationnelle), cela peut fonctionner correctement. Toutefois, si la transaction ne peut pas couvrir les agrégats, tels que lorsque vous utilisez une base de données NoSQL comme Azure DocumentDB, vous devrez implémenter des étapes supplémentaires pour garantir la cohérence. Il s’agit d’une autre raison pour laquelle ignorant la persistance n'est pas universelle ; il dépend du système de stockage que vous utilisez.

### <a name="single-transaction-across-aggregates-versus-eventual-consistency-across-aggregates"></a>Transaction unique entre les agrégats et la cohérence éventuelle des agrégats

La question s’il faut effectuer une transaction unique entre les agrégats par rapport à la partie de confiance entre les agrégats sur la cohérence éventuelle est controversé. Nombreux auteurs DDD comme Eric Evans et Vaughn Vernon préconisent la règle une transaction = un seul agrégat et par conséquent prétendent pour la cohérence éventuelle entre les agrégats. Par exemple, dans son livre *la conception*, Eric Evans indique cela :

Une règle qui s’étend sur des agrégats ne sera pas censée être à jour en permanence. Via le traitement des événements, le traitement par lots ou d’autres mécanismes de mise à jour, les autres dépendances peuvent être résolues dans le temps spécifique. (groupe de protection. 128)

Vaughn Vernon affiche le message suivant dans [efficaces de conception d’agrégation. Partie II : Fabrication travail agrège ensemble](http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf):

Par conséquent, si l’exécution d’une commande sur une instance d’agrégation requiert que les autres règles d’entreprise s’exécuter sur un ou plusieurs agrégats, utilisez la cohérence éventuelle \[...\] Il existe un moyen pratique pour prendre en charge de la cohérence éventuelle dans un modèle DDD. Une méthode d’agrégation publie un événement de domaine qui est remis à un ou plusieurs abonnés asynchrones.

Cette logique est basée sur adoption affinées transactions plutôt que de nombreux agrégats ou des entités de fractionnement des transactions. L’idée est que dans le deuxième cas, le nombre de verrous de base de données sera important dans les applications à grande échelle avec les besoins de haute évolutivité. Adoption du fait que les applications évolutives haute doivent n’a ne pas la cohérence transactionnelle instantanée entre plusieurs agrégats aide à accepter le concept de cohérence éventuelle. Modifications atomiques ne sont généralement pas nécessaires à l’activité, et il est dans tous les cas la responsabilité des experts de domaine pour vous si certaines opérations besoin des transactions atomiques ou non. Si une opération toujours a besoin d’une transaction atomique entre plusieurs agrégats, vous pouvez demander si votre regroupement doit être supérieure ou n’a pas été conçue correctement.

Toutefois, les autres développeurs et les architectes de Jimmy Bogard sont OK lorsque la répartition d’une transaction unique entre plusieurs agrégats, mais uniquement lorsque les agrégats supplémentaires associés aux effets de la même commande d’origine. Par exemple, dans [un modèle d’événements domaine mieux](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/), Bogard indique cela :

En règle générale, je veux les effets d’un événement de domaine dans la même transaction logique, mais pas nécessairement dans la même étendue de déclencher l’événement domaine \[...\] Juste avant que nous commit transaction, nous distribuer notre événements à leurs gestionnaires respectifs.

Si vous expédiez le droit d’événements de domaine *avant* validé la transaction d’origine, il est, car vous souhaitez que les effets de ces événements à inclure dans la même transaction. Par exemple, si la méthode SaveChanges de DbContext EF échoue, la transaction annule toutes les modifications, le résultat de toutes les opérations de l’effet secondaire implémentée par les gestionnaires d’événements de domaine connexes. Cela est, car l’étendue de la durée de vie DbContext est par défaut défini comme « limitée. » Par conséquent, l’objet DbContext est partagé entre plusieurs objets du référentiel en cours d’instanciation au sein de la même étendue ou un graphique d’objets. Ceci coïncide avec l’étendue HttpRequest lors du développement d’applications Web API ou MVC.

En réalité, ces deux approches (transaction atomique unique et la cohérence éventuelle) peuvent être appropriées. Il dépend vraiment les besoins de votre entreprise ou de domaine et ce que les experts de domaine vous dire. Il dépend également de l’évolutivité que vous devez le service doit être (transactions plus granulaires ont moins d’impact en ce qui concerne les verrous de base de données). Et dépend de la quantité investissement vous êtes prêt à effectuer dans votre code, étant donné que la cohérence éventuelle nécessite un code plus complexe afin de détecter les éventuelles incohérences entre les agrégats et la nécessité d’implémenter des actions de compensation. Prendre en compte si vous validez des modifications à l’agrégat d’origine et par la suite, lorsque les événements sont distribués, il existe un problème et les gestionnaires d’événements ne peut pas valider leurs effets secondaires, vous devez les incohérences entre des agrégats.

Est un moyen d’autoriser des actions de compensation pour stocker les événements de domaine dans les tables de base de données supplémentaires afin qu’ils peuvent faire partie de la transaction d’origine. Ensuite, vous pourriez avoir un traitement par lots qui détecte des incohérences et exécute des actions de compensation en comparant la liste des événements avec l’état actuel des agrégats. Les actions de compensation font partie d’un sujet complexe qui nécessite une analyse approfondie de votre côté, ce qui inclut discuter avec l’utilisateur des activités et les experts de domaine.

Dans tous les cas, vous pouvez choisir l’approche que vous avez besoin. Mais initial différée approche, le déclenchement d’événements avant de valider, afin d’utiliser d’une transaction unique, est l’approche la plus simple lorsque vous utilisez EF Core et une base de données relationnelle. Il est plus facile à implémenter et valide dans de nombreux cas. Il est également l’approche utilisée dans l’ordre de tri microservice dans eShopOnContainers.

Mais comment réellement répartition ces événements à leurs gestionnaires d’événements respectif ? Quelle est la \_objet médiateur que vous voyez dans l’exemple précédent ? Qui doit faire avec les techniques et les artefacts que vous pouvez utiliser pour le mappage entre les événements et leurs gestionnaires d’événements.

### <a name="the-domain-event-dispatcher-mapping-from-events-to-event-handlers"></a>Le répartiteur d’événements de domaine : mappage à partir d’événements aux gestionnaires d’événements

Une fois que vous êtes en mesure de distribuer ou publier les événements, vous avez besoin d’un type d’artefact qui publiera l’événement afin que chaque gestionnaire associé peut l’obtenir et les effets de processus basé sur l’événement.

Une approche consiste à un système de messagerie réel ou même un bus d’événements, éventuellement en fonction d’un service bus par opposition aux événements de mémoire. Toutefois, pour le premier cas, messagerie réels serait excessifs pour le traitement des événements de domaine, car il vous suffit de traiter ces événements dans le même processus (autrement dit, dans la même couche de domaine et d’application).

Une autre façon de mapper des événements sur plusieurs gestionnaires d’événements est à l’aide de l’inscription des types dans un conteneur inversion de contrôle afin que vous pouvez déduire dynamiquement vers où distribuer les événements. En d’autres termes, vous devez connaître les gestionnaires d’événements permettant d’obtenir un événement spécifique. Figure 9-16 montre une approche simplifiée pour cela.

![](./media/image17.png)

**Figure 9-16**. Répartiteur d’événements de domaine à l’aide d’inversion de contrôle

Vous pouvez créer tous les éléments et artefacts pour implémenter cette approche par vous-même. Toutefois, vous pouvez également utiliser les bibliothèques disponibles comme [MediatR](https://github.com/jbogard/MediatR), qui les coulisses utilise votre conteneur IoT. Vous pouvez donc directement utiliser les interfaces prédéfinies et des méthodes de publication/distribution de l’objet médiateur.

Dans le code, vous devez d’abord inscrire les types de gestionnaires d’événements dans votre conteneur inversion de contrôle, comme indiqué dans l’exemple suivant :

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        // Other registrations ...
        // Register the DomainEventHandler classes (they implement
        // IAsyncNotificationHandler<>) in assembly holding the Domain Events
        builder.RegisterAssemblyTypes(
            typeof(ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler)
            .GetTypeInfo().Assembly)
            .Where(t => t.IsClosedTypeOf(typeof(IAsyncNotificationHandler<>)))
            .AsImplementedInterfaces();
        // Other registrations ...
    }
}
```

Le code identifie tout d’abord l’assembly qui contient les gestionnaires d’événements de domaine en recherchant l’assembly qui contient un des gestionnaires (à l’aide de typeof(ValidateOrAddBuyerAggregateWhenXxxx), mais vous auriez pu choisir n’importe quel autre gestionnaire d’événements pour rechercher l’assembly). Étant donné que tous les gestionnaires d’événements implémentent l’interface IAsyncNotificationHandler, le code, puis recherche uniquement les types et enregistre tous les gestionnaires d’événements.

### <a name="how-to-subscribe-to-domain-events"></a>Comment s’abonner aux événements de domaine

Lorsque vous utilisez MediatR, chaque gestionnaire d’événements doit utiliser un type d’événement qui est fourni sur le paramètre générique de l’interface IAsyncNotificationHandler, comme vous pouvez le voir dans le code suivant :

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
  : IAsyncNotificationHandler<OrderStartedDomainEvent>
```

En fonction de la relation entre l’événement et le Gestionnaire d’événements qui peut être considérées comme l’abonnement, l’artefact MediatR peut détecter tous les gestionnaires d’événements pour chaque événement et déclencher chacun de ces gestionnaires d’événements.

### <a name="how-to-handle-domain-events"></a>Comment gérer les événements de domaine

Enfin, le Gestionnaire d’événements implémente généralement code de couche application qui utilise des référentiels de l’infrastructure pour obtenir les fonctions d’agrégation supplémentaires requises et exécuter la logique de domaine de l’effet. Le code suivant fournit un exemple.

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
    : IAsyncNotificationHandler<OrderStartedDomainEvent>
{
    private readonly ILoggerFactory _logger;
    private readonly IBuyerRepository<Buyer> _buyerRepository;
    private readonly IIdentityService _identityService;
    public ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler(
        ILoggerFactory logger,
        IBuyerRepository<Buyer> buyerRepository,
        IIdentityService identityService)
    {
        // Parameter validations
        //...
    }

    public async Task Handle(OrderStartedDomainEvent orderStartedEvent)
    {
        var cardTypeId = (orderStartedEvent.CardTypeId != 0) ?
            orderStartedEvent.CardTypeId : 1;
        var userGuid = _identityService.GetUserIdentity();
        var buyer = await _buyerRepository.FindAsync(userGuid);
        bool buyerOriginallyExisted = (buyer == null) ? false : true;
        if (!buyerOriginallyExisted)
        {
            buyer = new Buyer(userGuid);
        }
        buyer.VerifyOrAddPaymentMethod(cardTypeId,
            $"Payment Method on {DateTime.UtcNow}",
            orderStartedEvent.CardNumber,
            orderStartedEvent.CardSecurityNumber,
            orderStartedEvent.CardHolderName,
            orderStartedEvent.CardExpiration,
            orderStartedEvent.Order.Id);
        var buyerUpdated = buyerOriginallyExisted ? _buyerRepository.Update(buyer) :
        _buyerRepository.Add(buyer);
        await _buyerRepository.UnitOfWork.SaveEntitiesAsync();
        // Logging code using buyerUpdated info, etc.
    }
}
```

Ce code de gestionnaire d’événements est considéré comme code de couche application, car elle utilise des référentiels de l’infrastructure, comme expliqué dans la section suivante sur la couche de persistance de l’infrastructure. Gestionnaires d’événements peuvent également utiliser d’autres composants d’infrastructure.

#### <a name="domain-events-can-generate-integration-events-to-be-published-outside-of-the-microservice-boundaries"></a>Événements de domaine peuvent générer des événements d’intégration à publier en dehors des limites de microservice

Enfin, il est important de mentionner que vous souhaiterez parfois propager des événements sur plusieurs microservices. Qui est considéré comme un événement d’intégration, et elle peut être publiée via un bus d’événements à partir de n’importe quel gestionnaire d’événements de domaine spécifique.

## <a name="conclusions-on-domain-events"></a>Conclusions sur les événements de domaine 

Comme indiqué, utilisez les événements de domaine d’implémenter explicitement des effets des modifications de votre domaine. Pour utiliser la terminologie DDD, utilisez les événements de domaine d’implémenter explicitement des effets secondaires sur un ou plusieurs agrégats. En outre et pour une meilleure évolutivité et moins d’impact sur les verrous de base de données, utilisez cohérence éventuelle entre les agrégats au sein du même domaine.

#### <a name="additional-resources"></a>Ressources supplémentaires

-   **Greg Young. Qu’est un événement de domaine ? ** 
     [ *http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/*](http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/)

-   **Jan Stenberg. Événements de domaine et de la cohérence éventuelle**
    [*https://www.infoq.com/news/2015/09/domain-events-consistency*](https://www.infoq.com/news/2015/09/domain-events-consistency)

-   **Jimmy Bogard. Un modèle d’événements domaine mieux**
    [*https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/*](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)

-   **Vaughn Vernon. Efficace d’agrégation conception partie II : Effectue le travail agrégats ensemble**
    [*http://dddcommunity.org/wp-content/uploads/files/pdf\_articles/Vernon\_2011\_ 2. fichier pdf de*](http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)

-   **Jimmy Bogard. Renforcement de votre domaine : événements de domaine**
    *<https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/>*

-   **Tony Truong. Exemple de modèle de domaine événements**
    [*http://www.tonytruong.net/domain-events-pattern-example/*](http://www.tonytruong.net/domain-events-pattern-example/)

-   **UDI Dahan. Comment créer entièrement encapsulé les modèles de domaine**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)

-   **UDI Dahan. Événements de domaine – prendre 2**
    [*http://udidahan.com/2008/08/25/domain-events-take-2/*](http://udidahan.com/2008/08/25/domain-events-take-2/%20)

-   **UDI Dahan. Événements de domaine – Salvation**
    [*http://udidahan.com/2009/06/14/domain-events-salvation/*](http://udidahan.com/2009/06/14/domain-events-salvation/)

-   **Jan Kronquist. Ne pas publier des événements de domaine, les retourner ! ** 
     [ *https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/*](https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/)

-   **Cesar de la Torre. Événements de domaine Visual Studio. Événements d’intégration dans les architectures DDD et microservices**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/)


>[!div class="step-by-step"]
[Précédente] (client-côté-validation.md) [suivant] (infrastructure-persistance-layer-design.md)
