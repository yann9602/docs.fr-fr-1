---
title: "Implémentation d’un modèle de domaine microservice avec le .NET Core"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Implémentation d’un modèle de domaine microservice avec le .NET Core"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 26c480a82ad7bb806734decebdfbe5b4a07998e6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-a-microservice-domain-model-with-net-core"></a>Implémentation d’un modèle de domaine microservice avec le .NET Core 

Dans la section précédente, les principes fondamentaux et les modèles de conception d’un modèle de domaine ont été expliqués. Il est temps d’Explorer des méthodes possibles pour implémenter le modèle de domaine à l’aide de .NET Core (C brut\# code) et EF Core. Notez que votre modèle de domaine sera composé simplement de votre code. Il a seulement les spécifications de modèle de base de EF, mais pas réels dépendances sur EF. Vous devez pas dépendances dures ou des références à EF Core ou n’importe quel autre ORM dans votre modèle de domaine.

## <a name="domain-model-structure-in-a-custom-net-standard-library"></a>Structure de modèle de domaine dans une bibliothèque .NET Standard personnalisée

L’organisation du dossier utilisée pour l’application de référence eShopOnContainers montre le modèle DDD pour l’application. Vous constaterez peut-être qu’une organisation de l’autre dossier plus clairement les choix de conception pour votre application. Comme vous pouvez le voir dans la Figure 9 et 10, dans le modèle de domaine tri il existe deux agrégats, l’agrégat de commande et l’agrégation de l’acheteur. Chaque agrégat est un groupe d’entités de domaine et les objets de valeur, bien que vous pourriez avoir un agrégat composé ainsi d’une entité de domaine unique (la racine d’agrégat ou une entité racine).

![](./media/image11.png)

**Figure 9-10**. Structure de modèle de domaine pour le tri microservice dans eShopOnContainers

En outre, la couche de modèle de domaine inclut les contrats de référentiel (interfaces) sont les exigences de l’infrastructure de votre modèle de domaine. En d’autres termes, ces interfaces express les référentiels de la couche d’infrastructure doit implémenter et comment. Il est essentiel que l’implémentation des dépôts placées en dehors de la couche de modèle de domaine, dans la bibliothèque de couche d’infrastructure, afin de la couche de modèle de domaine n'est pas « contamination » par l’API ou les classes de technologies d’infrastructure, telles que Entity Framework.

Vous pouvez également voir un [SeedWork](https://martinfowler.com/bliki/Seedwork.html) dossier qui contient les classes de base personnalisées que vous pouvez utiliser comme base pour vos entités de domaine et la valeur des objets, donc vous n’avez pas de code redondant dans la classe d’objet de chaque domaine.

## <a name="structuring-aggregates-in-a-custom-net-standard-library"></a>Structuration des agrégats dans une bibliothèque .NET Standard personnalisée

Un agrégat fait référence à un cluster d’objets domaine regroupés pour faire correspondre la cohérence transactionnelle. Ces objets peuvent être des instances des entités (y compris la racine d’agrégat ou une entité racine) ainsi que tous les objets de valeur supplémentaire.

La cohérence transactionnelle signifie qu’un agrégat est garanti être cohérentes et à jour à la fin d’une action d’entreprise. Par exemple, l’agrégat de la commande à partir de l’eShopOnContainers classement du modèle de domaine microservice est composé comme indiqué dans la Figure 9-11.

![](./media/image12.png)

**Figure 9-11**. L’ordre d’agrégation dans une solution Visual Studio

Si vous ouvrez les fichiers dans un dossier d’agrégation, vous pouvez voir comment il est marqué comme une classe de base personnalisée ou une interface, comme les objets entité ou une valeur, tel qu’implémenté dans le [Seedwork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) dossier.

## <a name="implementing-domain-entities-as-poco-classes"></a>Implémentation des entités de domaine en tant que classes POCO

Vous implémentez un modèle de domaine dans .NET en créant des classes POCO qui implémentent les entités de votre domaine. Dans l’exemple suivant, la classe de commande est définie comme une entité et également en tant que racine d’une agrégat. Étant donné que la classe Order dérive de la classe de base d’entité, il peut réutiliser le code courantes lié aux entités. N’oubliez pas que ces classes de base et les interfaces sont définies par vous dans le projet de modèle de domaine, il s’agit de votre code, le code d’infrastructure pas à partir d’un ORM comme EF.

```csharp
// COMPATIBLE WITH ENTITY FRAMEWORK CORE 1.0
// Entity is a custom base class with the ID
public class Order : Entity, IAggregateRoot
{
    public int BuyerId { get; private set; }
    public DateTime OrderDate { get; private set; }
    public int StatusId { get; private set; }
    public ICollection<OrderItem> OrderItems { get; private set; }
    public Address ShippingAddress { get; private set; }
    public int PaymentId { get; private set; }
    protected Order() { } //Design constraint needed only by EF Core
    public Order(int buyerId, int paymentId)
    {
        BuyerId = buyerId;
        PaymentId = paymentId;
        StatusId = OrderStatus.InProcess.Id;
        OrderDate = DateTime.UtcNow;
        OrderItems = new List<OrderItem>();
    }

    public void AddOrderItem(productName,
        pictureUrl,
        unitPrice,
        discount,
        units)
    {
        //...
        // Domain rules/logic for adding the OrderItem to the order
        // ...
        OrderItem item = new OrderItem(this.Id, ProductId, productName,
            pictureUrl, unitPrice, discount, units);
  
        OrderItems.Add(item);
    }
    // ...
    // Additional methods with domain rules/logic related to the Order aggregate
    // ...
}
```

Il est important de noter qu’il s’agit d’une entité de domaine implémentée comme une classe POCO. Il n’a pas de dépendance directe avec Entity Framework Core ou toute autre infrastructure de l’infrastructure. Cette implémentation est qu’elle doit être simplement C\# code implémentant un modèle de domaine.

En outre, la classe est décorée avec une interface nommée IAggregateRoot. Cette interface est une interface vide, parfois appelée un *interface de marqueurs*, qui est utilisé uniquement pour indiquer que cette classe d’entité est également une racine d’agrégat.

Une interface de marqueur est parfois considérée comme un anti-modèle ; Toutefois, il est également un moyen adéquat pour marquer une classe, en particulier lorsque cette interface peut évoluer. Un attribut peut être le choix pour le marqueur, mais il est plus rapide afficher la classe de base (entité) en regard de l’interface IAggregate au lieu de mettre un marqueur d’attribut d’agrégation au-dessus de la classe. Il est un metter des préférences, dans tous les cas.

Avoir un moyen de racine d’agrégation que la plupart du code liées à la cohérence et d’entités de l’agrégat règles d’entreprise doivent être implémentées en tant que méthodes dans la classe de racine d’agrégation Order (par exemple, AddOrderItem lors de l’ajout d’un objet OrderItem à l’agrégat) . Vous ne devez pas créer ou mettre à jour les objets OrderItems indépendamment ou directement. la classe AggregateRoot doit conserver la cohérence de toutes les opérations de mise à jour par rapport à ses entités enfants et de contrôle.

Par exemple, vous devez *pas* effectuer les opérations suivantes à partir de toute classe de couche commande Gestionnaire méthode ou d’une application :

```csharp
// WRONG ACCORDING TO DDD PATTERNS – CODE AT THE APPLICATION LAYER OR
// COMMAND HANDLERS
// Code in command handler methods or Web API controllers
//... (WRONG) Some code with business logic out of the domain classes ...
OrderItem myNewOrderItem = new OrderItem(orderId, productId, productName,
    pictureUrl, unitPrice, discount, units);

//... (WRONG) Accessing the OrderItems colletion directly from the application layer // or command handlers
myOrder.OrderItems.Add(myNewOrderItem);
//...
```

Dans ce cas, la méthode Add est purement une opération pour ajouter des données, avec un accès direct à la collection OrderItems. Par conséquent, la plupart de la logique de domaine, les règles ou les validations liées pour que l’opération avec les entités enfants est répartie sur la couche d’application (gestionnaires de commandes et contrôleurs de l’API Web).

Si vous accédez autour de la racine d’agrégation, la racine d’agrégation ne peut pas garantir son invariants, sa validité ou sa cohérence. Vous aurez éventuellement spaghetti code ou script transactionnel.

Pour suivre les modèles DDD, les entités ne doivent pas avoir de méthodes setter public dans n’importe quelle propriété d’entité. Modifications apportées à une entité doivent être pilotées par les méthodes explicites avec un langage omniprésent explicite sur la modification, qu'elles exécutent dans l’entité.

En outre, les collections dans l’entité (par exemple, les éléments de la commande) doivent être des propriétés en lecture seule (la méthode AsReadOnly abordées plus loin). Vous devez pouvoir mettre à jour uniquement à partir de dans les méthodes de classe racine d’agrégation ou les méthodes d’entité enfant.

Comme vous pouvez le voir dans le code de la racine d’agrégation de commande, toutes les méthodes setter doit être privés ou au moins en lecture seule en externe, afin que toute opération sur les données de l’entité ou de ses entités enfants doit être effectuée via les méthodes dans la classe d’entité. Cela maintient la cohérence d’une manière contrôlée et orienté objet au lieu d’implémenter le code de script transactionnel.

L’extrait de code suivant montre la façon correcte de la tâche d’ajout d’un objet OrderItem à l’agrégat de l’ordre de code.

```csharp
// RIGHT ACCORDING TO DDD--CODE AT THE APPLICATION LAYER OR COMMAND HANDLERS
// The code in command handlers or WebAPI controllers, related only to application stuff
// There is NO code here related to OrderItem object’s business logic
myOrder.AddOrderItem(productId, productName, pictureUrl, unitPrice, discount, units);

// The code related to OrderItem params validations or domain rules should
// be WITHIN the AddOrderItem method.

//...
```

Dans cet extrait de code, la plupart des validations ou logique relatives à la création d’un objet OrderItem seront sous le contrôle de la racine d’agrégation ordre, dans la méthode AddOrderItem, en particulier les validations et logique liées à d’autres éléments dans l’agrégat. Par exemple, vous pouvez obtenir le même élément de produit comme résultat de plusieurs appels à AddOrderItem. Dans cette méthode, vous pourriez examiner les éléments de produit et consolider les mêmes éléments de produit dans un seul objet OrderItem avec plusieurs unités. En outre, si des montants de remises différents, mais l’ID de produit est le même, vous devez probablement appliquer la remise la plus élevée. Ce principe s’applique à toute autre logique de domaine pour l’objet OrderItem.

En outre, la nouvelle opération OrderItem(params) sera également être contrôlée et effectuée par la méthode AddOrderItem à partir de la racine d’agrégation de commande. Par conséquent, la plupart de la logique ou les validations liées pour que l’opération (en particulier tout ce qui a un impact sur la cohérence entre les autres entités enfants) seront dans un endroit unique au sein de la racine d’agrégation. C’est l’objectif ultime du modèle racine d’agrégation.

Lorsque vous utilisez Entity Framework 1.1, une entité DDD peut mieux exprimée, car une des nouvelles fonctionnalités d’Entity Framework Core 1.1 est qu’il permet [mapper à des champs](https://docs.microsoft.com/ef/core/modeling/backing-field) en plus des propriétés. Cela est utile lorsque vous protégez des collections d’entités enfants ou des objets de valeur. Avec cette amélioration, vous pouvez utiliser des champs privés simples au lieu des propriétés, et vous pouvez implémenter une mise à jour à la collection de champs dans les méthodes publiques et fournir un accès en lecture seule via la méthode AsReadOnly.

Dans DDD à mettre à jour l’entité uniquement par le biais de méthodes dans l’entité (ou le constructeur) afin de contrôler n’importe quel nom invariant et la cohérence des données, par conséquent, les propriétés sont définies uniquement avec un accesseur get. Les propriétés sont soutenues par les champs privés. Les membres privés uniquement accessibles à partir de la classe. Toutefois, les exceptions là un : EF Core doit définir ces champs ainsi.

```csharp
// ENTITY FRAMEWORK CORE 1.1 OR LATER
// Entity is a custom base class with the ID
public class Order : Entity, IAggregateRoot
{
    // DDD Patterns comment
    // Using private fields, allowed since EF Core 1.1, is a much better
    // encapsulation aligned with DDD aggregates and domain entities (instead of
    // properties and property collections)
    private bool _someOrderInternalState;
    private DateTime _orderDate;
    public Address Address { get; private set; }
    public Buyer Buyer { get; private set; }
    private int _buyerId;
    public OrderStatus OrderStatus { get; private set; }
    private int _orderStatusId;

    // DDD patterns comment
    // Using a private collection field is better for DDD aggregate encapsulation.
    // OrderItem objects cannot be added from outside the aggregate root
    // directly to the collection, but only through the
    // OrderAggrergateRoot.AddOrderItem method, which includes behavior.
    private readonly List<OrderItem> _orderItems;
    public IEnumerable<OrderItem> OrderItems => _orderItems.AsReadOnly();
    // Using List<>.AsReadOnly()
    // This will create a read-only wrapper around the private list so it is
    // protected against external updates. It's much cheaper than .ToList(),
    // because it will not have to copy all items in a new collection.
    // (Just one heap alloc for the wrapper instance)
    // https://msdn.microsoft.com/en-us/library/e78dcd75(v=vs.110).aspx
    public PaymentMethod PaymentMethod { get; private set; }
    private int _paymentMethodId;

    protected Order() { }

    public Order(int buyerId, int paymentMethodId, Address address)
    {
        _orderItems = new List<OrderItem>();
        _buyerId = buyerId;
        _paymentMethodId = paymentMethodId;
        _orderStatusId = OrderStatus.InProcess.Id;
        _orderDate = DateTime.UtcNow;
        Address = address;
    }

    // DDD patterns comment
    // The Order aggregate root method AddOrderitem() should be the only way
    // to add items to the Order object, so that any behavior (discounts, etc.)
    // and validations are controlled by the aggregate root in order to
    // maintain consistency within the whole aggregate.
    public void AddOrderItem(int productId, string productName, decimal unitPrice,
        decimal discount, string pictureUrl, int units = 1)
    {
        // ...
        // Domain rules/logic here for adding OrderItem objects to the order
        // ...
        OrderItem item = new OrderItem(this.Id, productId, productName,
            pictureUrl, unitPrice, discount, units);
        OrderItems.Add(item);
    }

    // ...
    // Additional methods with domain rules/logic related to the Order aggregate
    // ...
}
```

### <a name="mapping-properties-with-only-get-accessors-to-the-fields-in-the-database-table"></a>Accesseurs get de mappage de propriétés avec uniquement pour les champs de la table de base de données

Mappage de propriétés pour les colonnes de table de base de données n’est pas une responsabilité de domaine, mais la partie de la couche d’infrastructure et de persistance. Nous signaler ce ici simplement afin de connaître les nouvelles fonctionnalités dans la version 1.1 de EF liées à la façon dont vous pouvez modéliser des entités. Plus d’informations sur cette rubrique sont expliquées dans la section de l’infrastructure et de persistance.

Lorsque vous utilisez EF 1.0, vous devez mapper les propriétés qui sont définies uniquement avec des accesseurs Get aux champs dans la table de base de données réelles dans le DbContext. Cela est fait avec la méthode HasField de la classe PropertyBuilder.

### <a name="mapping-fields-without-properties"></a>Mappage de champs sans propriétés

Avec la nouvelle fonctionnalité dans la version 1.1 de noyaux EF pour mapper des colonnes aux champs, il est également possible de ne pas utiliser les propriétés. Au lieu de cela, vous pouvez uniquement mapper des colonnes d’une table aux champs. Un cas d’usage courants pour ce est champs privés pour un état interne qui ne doivent pas être accessible de l’extérieur de l’entité.

Par exemple, dans l’exemple de code précédent, le \_someOrderInternalState champ n’a aucune propriété connexe pour une méthode setter ou getter. Ce champ est également calculé au sein de la logique métier de la commande et utilisé dans les méthodes de la commande, mais il doit être rendue persistante dans la base de données. Par conséquent, dans la version 1.1 de EF est permet de mapper un champ sans une propriété associée à une colonne dans la base de données. Cela est également indiqué dans le [couche d’Infrastructure](#the-infrastructure-layer) section de ce guide.

### <a name="additional-resources"></a>Ressources supplémentaires

-   **Vaughn Vernon. Modélisation des agrégats avec DDD et Entity Framework.** Notez que cela est *pas* Entity Framework Core.
    [*https://vaughnvernon.co/?p=879*](https://vaughnvernon.co/?p=879)

-   **Julie Lerman. Codage de conception domaine : conseils pour les développeurs d’axée sur les données**
    [*https://msdn.microsoft.com/en-us/magazine/dn342868.aspx*](https://msdn.microsoft.com/en-us/magazine/dn342868.aspx)

-   **UDI Dahan. Comment créer entièrement encapsulé les modèles de domaine**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)


>[!div class="step-by-step"]
[Précédente] (microservice-domaine-model.md) [suivant] (seedwork-domain-model-base-classes-interfaces.md)
