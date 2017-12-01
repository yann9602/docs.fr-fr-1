---
title: "Conception des validations dans la couche de modèle de domaine"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Conception des validations dans la couche de modèle de domaine"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: f4870d0568c3539f296bcb3f577291cb0250cfca
ms.sourcegitcommit: 62d3e3e74c1b7ffa927590012c0b9f87de1b0848
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="designing-validations-in-the-domain-model-layer"></a>Conception des validations dans la couche de modèle de domaine

Dans DDD, les règles de validation peuvent être considérés comme des invariants. La responsabilité principale d’un agrégat est d’appliquer des invariants entre les modifications d’état pour toutes les entités au sein de ce regroupement.

Entités de domaine doivent toujours être entités valides. Il existe un certain nombre d’invariants pour un objet qui doit toujours être true. Par exemple, un objet d’élément order toujours doit avoir une quantité qui doit être un entier positif, ainsi qu’un nom d’article et de prix. Par conséquent, la mise en œuvre des invariants est la responsabilité des entités de domaine (en particulier de la racine d’agrégation) et un objet d’entité doit pouvoir pas exister sans être valide. Invariantes règles sont simplement exprimées en tant que contrats et les exceptions ou les notifications sont déclenchées quand ils sont enfreintes.

Le raisonnement est que le nombre de bogues se produire car les objets sont dans un état, dans qu'ils ne doivent jamais ont été. L’exemple suivant est une bonne explication de Greg Young dans un [discussion en ligne](http://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/):

Nous allons proposer que nous disposons désormais d’un SendUserCreationEmailService qui accepte un UserProfile... Comment pouvons nous rationaliser dans ce service de nom n’est pas null ? Effectuer la vérification il à nouveau ? Ou le plus probable... vous simplement inutile pour vérifier et « espérons que pour une meilleure » — vous espérez toutefois que quelqu'un dérangé pour le valider avant de les envoyer à vous. Bien entendu, à l’aide de TDD un des premiers tests, que nous devons écrire est que si un client avec un nom null envoyer qu’il doit déclencher une erreur. Mais une fois que nous allons commencer l’écriture de ces types de tests indéfiniment que nous sommes conscients... « attendre si nous jamais autorisé nom devienne null nous n’aurions tous ces tests »

## <a name="implementing-validations-in-the-domain-model-layer"></a>Implémentation des validations dans la couche de modèle de domaine

Validations sont généralement implémentées dans les constructeurs d’entité de domaine ou dans des méthodes qui peuvent de mettre à jour l’entité. Il existe plusieurs façons d’implémenter les validations, telles que la vérification des données et le déclenchement d’exceptions si la validation échoue. Il existe également des modèles plus avancées telles que l’utilisation du modèle de spécification pour les validations et que le modèle de Notification pour retourner une collection d’erreurs au lieu de retourner une exception pour chaque validation lorsqu’il se produit.

### <a name="validating-conditions-and-throwing-exceptions"></a>Validation des conditions et levée des exceptions

L’exemple de code suivant montre l’approche la plus simple de validation dans une entité de domaine en levant une exception. Dans la table de références à la fin de cette section, vous pouvez voir des liens vers des implémentations plus avancées basées sur les modèles que nous avons indiqué précédemment.

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

Un exemple d’une meilleure serait montrent la nécessité d’assurer que l’état interne n’a pas changé, ou que tous les mutations pour une méthode qui s’est produite. Par exemple, l’implémentation suivante continuent de l’objet dans un état non valide :

```csharp
public void SetAddress(string line1, string line2,
    string city, string state, int zip)
{
    _shipingAddress.line1 = line1 ?? throw new ...
    _shippingAddress.line2 = line2;
    _shippingAddress.city = city ?? throw new ...
    _shippingAddress.state = (IsValid(state) ? state : throw new …);
}
```

Si la valeur de l’état n’est pas valide, la première ligne d’adresse et la ville ont déjà été modifiés. Qui peut rendre l’adresse non valide.

Une approche similaire peut être utilisée dans le constructeur de l’entité, le déclenchement d’une exception pour vous assurer que l’entité est valide dès sa création.

### <a name="using-validation-attributes-in-the-model-based-on-data-annotations"></a>L’utilisation d’attributs de validation dans le modèle basé sur les annotations de données

Une autre approche consiste à utiliser les attributs de validation basées sur les annotations de données. Attributs de validation permettent de configurer la validation du modèle, qui est similaire sur le plan conceptuel à la validation des champs dans les tables de base de données. Cela inclut les contraintes telles que l’affectation de types de données ou les champs obligatoires. Autres types de validation incluent l’application de modèles de données pour appliquer des règles d’entreprise, telles qu’un numéro de carte de crédit, numéro de téléphone, ou l’adresse de messagerie. Attributs de validation permettent de facilement appliquer la configuration requise.

Toutefois, comme indiqué dans le code suivant, cette approche peut être trop contraignant dans un modèle DDD, car il prend une dépendance ModelState.IsValid de Microsoft.AspNetCore.Mvc.ModelState, que vous devez appeler à partir de vos contrôleurs MVC. La validation du modèle se produit avant chaque action du contrôleur qui est appelée, et il incombe de la méthode du contrôleur à inspecter le résultat de l’appel ModelState.IsValid et réagir de façon appropriée. La décision d’utiliser dépend étroitement vous souhaitez que le modèle avec cette infrastructure.

```csharp
using System.ComponentModel.DataAnnotations;
// Other using statements ...
// Entity is a custom base class which has the ID
public class Product : Entity
{
    [Required]
    [StringLength(100)]
    public string Title { get; private set; }

    [Required]
    [Range(0, 999.99)]
    public decimal Price { get; private set; }

    [Required]
    [VintageProduct(1970)]
    [DataType(DataType.Date)]
    public DateTime ReleaseDate { get; private set; }

    [Required]
    [StringLength(1000)]
    public string Description { get; private set; }

    // Constructor...
    // Additional methods for entity logic and constructor...
}
```

Toutefois, à partir d’un point de vue DDD, le modèle de domaine est préférable de conserver lean avec l’utilisation d’exceptions dans les méthodes de comportement de votre entité, ou en implémentant les modèles de spécification et de Notification pour appliquer des règles de validation. Infrastructures de validation comme des annotations de données dans ASP.NET Core ou toutes les autres infrastructures de validation comme FluentValidation comportent une exigence pour appeler l’infrastructure d’application. Par exemple, lorsque vous appelez la méthode ModelState.IsValid dans les annotations de données, vous devez appeler les contrôleurs de ASP.NET.

Il peut être judicieux d’utiliser des annotations de données au niveau de la couche application dans les classes ViewModel (au lieu des entités de domaine) qui accepte les entrées, pour permettre la validation des modèles dans la couche d’interface utilisateur. Toutefois, cela ne doit pas être réalisée à l’exclusion de validation dans le modèle de domaine.

### <a name="validating-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a>Validation des entités en implémentant le modèle de spécification et le modèle de Notification

Enfin, une approche plus élaborée pour implémenter des validations dans le modèle de domaine est en implémentant le modèle de spécification conjointement avec le modèle de Notification, comme expliqué dans certaines des ressources supplémentaires répertoriés ultérieurement.

Il est important de mentionner que vous pouvez également utiliser un seul de ces modèles, par exemple, validation manuellement avec les instructions de contrôle, mais à l’aide du modèle de Notification de la pile et retourner une liste des erreurs de validation.

### <a name="using-deferred-validation-in-the-domain"></a>À l’aide de la validation différée dans le domaine

Il existe différentes approches pour traiter les validations différées dans le domaine. Dans son livre [Implementing Domain-Driven conception](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon décrit dans la section sur la validation.

### <a name="two-step-validation"></a>Validation en deux étapes

Envisagez également la validation en deux étapes. Utilisez la validation au niveau du champ sur vos données transférer les objets de commande (DTO) et la validation au niveau du domaine à l’intérieur de vos entités. Pour cela, vous pouvez retourner un objet de résultat à la place des exceptions pour le rendre plus facile à gérer les erreurs de validation.

À l’aide de la validation de champ et annotations de données, par exemple, vous ne dupliquez pas la définition de la validation. L’exécution, il peut toutefois se côté serveur et côté client dans le cas de DTO (commandes et ViewModel, par exemple).

## <a name="additional-resources"></a>Ressources supplémentaires

-   **Rachel Appel. Introduction à la validation de modèle dans ASP.NET MVC de base**
    [*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)

-   **Rick Anderson. Ajout d’une validation**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)

-   **Martin Fowler. Remplacement de lever des Exceptions avec Notification dans les Validations**
    [*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)

-   **Spécification et les modèles de Notification**
    [*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)

-   **Lev Gorodinski. Validation de la conception domaine (DDD)**
    [*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)

-   **Colin prise. Validation de modèle de domaine**
    [*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)

-   **Jimmy Bogard. La validation dans un monde DDD**
    [*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)


>[!div class="step-by-step"]
[Précédente] (énumération-classes-over-enum-types.md) [suivant] (côté-client-validation.md)
