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
# <a name="designing-validations-in-the-domain-model-layer"></a><span data-ttu-id="d39c6-104">Conception des validations dans la couche de modèle de domaine</span><span class="sxs-lookup"><span data-stu-id="d39c6-104">Designing validations in the domain model layer</span></span>

<span data-ttu-id="d39c6-105">Dans DDD, les règles de validation peuvent être considérés comme des invariants.</span><span class="sxs-lookup"><span data-stu-id="d39c6-105">In DDD, validation rules can be thought as invariants.</span></span> <span data-ttu-id="d39c6-106">La responsabilité principale d’un agrégat est d’appliquer des invariants entre les modifications d’état pour toutes les entités au sein de ce regroupement.</span><span class="sxs-lookup"><span data-stu-id="d39c6-106">The main responsibility of an aggregate is to enforce invariants across state changes for all the entities within that aggregate.</span></span>

<span data-ttu-id="d39c6-107">Entités de domaine doivent toujours être entités valides.</span><span class="sxs-lookup"><span data-stu-id="d39c6-107">Domain entities should always be valid entities.</span></span> <span data-ttu-id="d39c6-108">Il existe un certain nombre d’invariants pour un objet qui doit toujours être true.</span><span class="sxs-lookup"><span data-stu-id="d39c6-108">There are a certain number of invariants for an object that should always be true.</span></span> <span data-ttu-id="d39c6-109">Par exemple, un objet d’élément order toujours doit avoir une quantité qui doit être un entier positif, ainsi qu’un nom d’article et de prix.</span><span class="sxs-lookup"><span data-stu-id="d39c6-109">For example, an order item object always has to have a quantity that must be a positive integer, plus an article name and price.</span></span> <span data-ttu-id="d39c6-110">Par conséquent, la mise en œuvre des invariants est la responsabilité des entités de domaine (en particulier de la racine d’agrégation) et un objet d’entité doit pouvoir pas exister sans être valide.</span><span class="sxs-lookup"><span data-stu-id="d39c6-110">Therefore, invariants enforcement is the responsibility of the domain entities (especially of the aggregate root) and an entity object should not be able to exist without being valid.</span></span> <span data-ttu-id="d39c6-111">Invariantes règles sont simplement exprimées en tant que contrats et les exceptions ou les notifications sont déclenchées quand ils sont enfreintes.</span><span class="sxs-lookup"><span data-stu-id="d39c6-111">Invariant rules are simply expressed as contracts, and exceptions or notifications are raised when they are violated.</span></span>

<span data-ttu-id="d39c6-112">Le raisonnement est que le nombre de bogues se produire car les objets sont dans un état, dans qu'ils ne doivent jamais ont été.</span><span class="sxs-lookup"><span data-stu-id="d39c6-112">The reasoning behind this is that many bugs occur because objects are in a state they should never have been in.</span></span> <span data-ttu-id="d39c6-113">L’exemple suivant est une bonne explication de Greg Young dans un [discussion en ligne](http://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/):</span><span class="sxs-lookup"><span data-stu-id="d39c6-113">The following is a good explanation from Greg Young in an [online discussion](http://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/):</span></span>

<span data-ttu-id="d39c6-114">Nous allons proposer que nous disposons désormais d’un SendUserCreationEmailService qui accepte un UserProfile... Comment pouvons nous rationaliser dans ce service de nom n’est pas null ?</span><span class="sxs-lookup"><span data-stu-id="d39c6-114">Let's propose we now have a SendUserCreationEmailService that takes a UserProfile ... how can we rationalize in that service that Name is not null?</span></span> <span data-ttu-id="d39c6-115">Effectuer la vérification il à nouveau ?</span><span class="sxs-lookup"><span data-stu-id="d39c6-115">Do we check it again?</span></span> <span data-ttu-id="d39c6-116">Ou le plus probable... vous simplement inutile pour vérifier et « espérons que pour une meilleure » — vous espérez toutefois que quelqu'un dérangé pour le valider avant de les envoyer à vous.</span><span class="sxs-lookup"><span data-stu-id="d39c6-116">Or more likely ... you just don't bother to check and "hope for the best"—you hope that someone bothered to validate it before sending it to you.</span></span> <span data-ttu-id="d39c6-117">Bien entendu, à l’aide de TDD un des premiers tests, que nous devons écrire est que si un client avec un nom null envoyer qu’il doit déclencher une erreur.</span><span class="sxs-lookup"><span data-stu-id="d39c6-117">Of course, using TDD one of the first tests we should be writing is that if I send a customer with a null name that it should raise an error.</span></span> <span data-ttu-id="d39c6-118">Mais une fois que nous allons commencer l’écriture de ces types de tests indéfiniment que nous sommes conscients... « attendre si nous jamais autorisé nom devienne null nous n’aurions tous ces tests »</span><span class="sxs-lookup"><span data-stu-id="d39c6-118">But once we start writing these kinds of tests over and over again we realize ... "wait if we never allowed name to become null we wouldn't have all of these tests"</span></span>

## <a name="implementing-validations-in-the-domain-model-layer"></a><span data-ttu-id="d39c6-119">Implémentation des validations dans la couche de modèle de domaine</span><span class="sxs-lookup"><span data-stu-id="d39c6-119">Implementing validations in the domain model layer</span></span>

<span data-ttu-id="d39c6-120">Validations sont généralement implémentées dans les constructeurs d’entité de domaine ou dans des méthodes qui peuvent de mettre à jour l’entité.</span><span class="sxs-lookup"><span data-stu-id="d39c6-120">Validations are usually implemented in domain entity constructors or in methods that can update the entity.</span></span> <span data-ttu-id="d39c6-121">Il existe plusieurs façons d’implémenter les validations, telles que la vérification des données et le déclenchement d’exceptions si la validation échoue.</span><span class="sxs-lookup"><span data-stu-id="d39c6-121">There are multiple ways to implement validations, such as verifying data and raising exceptions if the validation fails.</span></span> <span data-ttu-id="d39c6-122">Il existe également des modèles plus avancées telles que l’utilisation du modèle de spécification pour les validations et que le modèle de Notification pour retourner une collection d’erreurs au lieu de retourner une exception pour chaque validation lorsqu’il se produit.</span><span class="sxs-lookup"><span data-stu-id="d39c6-122">There are also more advanced patterns such as using the Specification pattern for validations, and the Notification pattern to return a collection of errors instead of returning an exception for each validation as it occurs.</span></span>

### <a name="validating-conditions-and-throwing-exceptions"></a><span data-ttu-id="d39c6-123">Validation des conditions et levée des exceptions</span><span class="sxs-lookup"><span data-stu-id="d39c6-123">Validating conditions and throwing exceptions</span></span>

<span data-ttu-id="d39c6-124">L’exemple de code suivant montre l’approche la plus simple de validation dans une entité de domaine en levant une exception.</span><span class="sxs-lookup"><span data-stu-id="d39c6-124">The following code example shows the simplest approach to validation in a domain entity by raising an exception.</span></span> <span data-ttu-id="d39c6-125">Dans la table de références à la fin de cette section, vous pouvez voir des liens vers des implémentations plus avancées basées sur les modèles que nous avons indiqué précédemment.</span><span class="sxs-lookup"><span data-stu-id="d39c6-125">In the references table at the end of this section you can see links to more advanced implementations based on the patterns we have discussed previously.</span></span>

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

<span data-ttu-id="d39c6-126">Un exemple d’une meilleure serait montrent la nécessité d’assurer que l’état interne n’a pas changé, ou que tous les mutations pour une méthode qui s’est produite.</span><span class="sxs-lookup"><span data-stu-id="d39c6-126">A better example would demonstrate the need to ensure that either the internal state did not change, or that all the mutations for a method occurred.</span></span> <span data-ttu-id="d39c6-127">Par exemple, l’implémentation suivante continuent de l’objet dans un état non valide :</span><span class="sxs-lookup"><span data-stu-id="d39c6-127">For example, the following implementation would leave the object in an invalid state:</span></span>

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

<span data-ttu-id="d39c6-128">Si la valeur de l’état n’est pas valide, la première ligne d’adresse et la ville ont déjà été modifiés.</span><span class="sxs-lookup"><span data-stu-id="d39c6-128">If the value of the state is invalid, the first address line and the city have already been changed.</span></span> <span data-ttu-id="d39c6-129">Qui peut rendre l’adresse non valide.</span><span class="sxs-lookup"><span data-stu-id="d39c6-129">That might make the address invalid.</span></span>

<span data-ttu-id="d39c6-130">Une approche similaire peut être utilisée dans le constructeur de l’entité, le déclenchement d’une exception pour vous assurer que l’entité est valide dès sa création.</span><span class="sxs-lookup"><span data-stu-id="d39c6-130">A similar approach can be used in the entity’s constructor, raising an exception to make sure that the entity is valid once it is created.</span></span>

### <a name="using-validation-attributes-in-the-model-based-on-data-annotations"></a><span data-ttu-id="d39c6-131">L’utilisation d’attributs de validation dans le modèle basé sur les annotations de données</span><span class="sxs-lookup"><span data-stu-id="d39c6-131">Using validation attributes in the model based on data annotations</span></span>

<span data-ttu-id="d39c6-132">Une autre approche consiste à utiliser les attributs de validation basées sur les annotations de données.</span><span class="sxs-lookup"><span data-stu-id="d39c6-132">Another approach is to use validation attributes based on data annotations.</span></span> <span data-ttu-id="d39c6-133">Attributs de validation permettent de configurer la validation du modèle, qui est similaire sur le plan conceptuel à la validation des champs dans les tables de base de données.</span><span class="sxs-lookup"><span data-stu-id="d39c6-133">Validation attributes provide a way to configure model validation, which is similar conceptually to validation on fields in database tables.</span></span> <span data-ttu-id="d39c6-134">Cela inclut les contraintes telles que l’affectation de types de données ou les champs obligatoires.</span><span class="sxs-lookup"><span data-stu-id="d39c6-134">This includes constraints such as assigning data types or required fields.</span></span> <span data-ttu-id="d39c6-135">Autres types de validation incluent l’application de modèles de données pour appliquer des règles d’entreprise, telles qu’un numéro de carte de crédit, numéro de téléphone, ou l’adresse de messagerie.</span><span class="sxs-lookup"><span data-stu-id="d39c6-135">Other types of validation include applying patterns to data to enforce business rules, such as a credit card number, phone number, or email address.</span></span> <span data-ttu-id="d39c6-136">Attributs de validation permettent de facilement appliquer la configuration requise.</span><span class="sxs-lookup"><span data-stu-id="d39c6-136">Validation attributes make it easy to enforce requirements.</span></span>

<span data-ttu-id="d39c6-137">Toutefois, comme indiqué dans le code suivant, cette approche peut être trop contraignant dans un modèle DDD, car il prend une dépendance ModelState.IsValid de Microsoft.AspNetCore.Mvc.ModelState, que vous devez appeler à partir de vos contrôleurs MVC.</span><span class="sxs-lookup"><span data-stu-id="d39c6-137">However, as shown in the following code, this approach might be too intrusive in a DDD model, because it takes a dependency on ModelState.IsValid from Microsoft.AspNetCore.Mvc.ModelState, which you must call from your MVC controllers.</span></span> <span data-ttu-id="d39c6-138">La validation du modèle se produit avant chaque action du contrôleur qui est appelée, et il incombe de la méthode du contrôleur à inspecter le résultat de l’appel ModelState.IsValid et réagir de façon appropriée.</span><span class="sxs-lookup"><span data-stu-id="d39c6-138">The model validation occurs prior to each controller action being invoked, and it is the controller method’s responsibility to inspect the result of calling ModelState.IsValid and react appropriately.</span></span> <span data-ttu-id="d39c6-139">La décision d’utiliser dépend étroitement vous souhaitez que le modèle avec cette infrastructure.</span><span class="sxs-lookup"><span data-stu-id="d39c6-139">The decision to use it depends on how tightly coupled you want the model to be with that infrastructure.</span></span>

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

<span data-ttu-id="d39c6-140">Toutefois, à partir d’un point de vue DDD, le modèle de domaine est préférable de conserver lean avec l’utilisation d’exceptions dans les méthodes de comportement de votre entité, ou en implémentant les modèles de spécification et de Notification pour appliquer des règles de validation.</span><span class="sxs-lookup"><span data-stu-id="d39c6-140">However, from a DDD point of view, the domain model is best kept lean with the use of exceptions in your entity’s behavior methods, or by implementing the Specification and Notification patterns to enforce validation rules.</span></span> <span data-ttu-id="d39c6-141">Infrastructures de validation comme des annotations de données dans ASP.NET Core ou toutes les autres infrastructures de validation comme FluentValidation comportent une exigence pour appeler l’infrastructure d’application.</span><span class="sxs-lookup"><span data-stu-id="d39c6-141">Validation frameworks like data annotations in ASP.NET Core or any other validation frameworks like FluentValidation carry a requirement to invoke the application framework.</span></span> <span data-ttu-id="d39c6-142">Par exemple, lorsque vous appelez la méthode ModelState.IsValid dans les annotations de données, vous devez appeler les contrôleurs de ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d39c6-142">For example, when calling the ModelState.IsValid method in data annotations, you need to invoke ASP.NET controllers.</span></span>

<span data-ttu-id="d39c6-143">Il peut être judicieux d’utiliser des annotations de données au niveau de la couche application dans les classes ViewModel (au lieu des entités de domaine) qui accepte les entrées, pour permettre la validation des modèles dans la couche d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d39c6-143">It can make sense to use data annotations at the application layer in ViewModel classes (instead of domain entities) that will accept input, to allow for model validation within the UI layer.</span></span> <span data-ttu-id="d39c6-144">Toutefois, cela ne doit pas être réalisée à l’exclusion de validation dans le modèle de domaine.</span><span class="sxs-lookup"><span data-stu-id="d39c6-144">However, this should not be done at the exclusion of validation within the domain model.</span></span>

### <a name="validating-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a><span data-ttu-id="d39c6-145">Validation des entités en implémentant le modèle de spécification et le modèle de Notification</span><span class="sxs-lookup"><span data-stu-id="d39c6-145">Validating entities by implementing the Specification pattern and the Notification pattern</span></span>

<span data-ttu-id="d39c6-146">Enfin, une approche plus élaborée pour implémenter des validations dans le modèle de domaine est en implémentant le modèle de spécification conjointement avec le modèle de Notification, comme expliqué dans certaines des ressources supplémentaires répertoriés ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="d39c6-146">Finally, a more elaborate approach to implementing validations in the domain model is by implementing the Specification pattern in conjunction with the Notification pattern, as explained in some of the additional resources listed later.</span></span>

<span data-ttu-id="d39c6-147">Il est important de mentionner que vous pouvez également utiliser un seul de ces modèles, par exemple, validation manuellement avec les instructions de contrôle, mais à l’aide du modèle de Notification de la pile et retourner une liste des erreurs de validation.</span><span class="sxs-lookup"><span data-stu-id="d39c6-147">It is worth mentioning that you can also use just one of those patterns—for example, validating manually with control statements, but using the Notification pattern to stack and return a list of validation errors.</span></span>

### <a name="using-deferred-validation-in-the-domain"></a><span data-ttu-id="d39c6-148">À l’aide de la validation différée dans le domaine</span><span class="sxs-lookup"><span data-stu-id="d39c6-148">Using deferred validation in the domain</span></span>

<span data-ttu-id="d39c6-149">Il existe différentes approches pour traiter les validations différées dans le domaine.</span><span class="sxs-lookup"><span data-stu-id="d39c6-149">There are various approaches to deal with deferred validations in the domain.</span></span> <span data-ttu-id="d39c6-150">Dans son livre [Implementing Domain-Driven conception](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon décrit dans la section sur la validation.</span><span class="sxs-lookup"><span data-stu-id="d39c6-150">In his book [Implementing Domain-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon discusses these in the section on validation.</span></span>

### <a name="two-step-validation"></a><span data-ttu-id="d39c6-151">Validation en deux étapes</span><span class="sxs-lookup"><span data-stu-id="d39c6-151">Two-step validation</span></span>

<span data-ttu-id="d39c6-152">Envisagez également la validation en deux étapes.</span><span class="sxs-lookup"><span data-stu-id="d39c6-152">Also consider two-step validation.</span></span> <span data-ttu-id="d39c6-153">Utilisez la validation au niveau du champ sur vos données transférer les objets de commande (DTO) et la validation au niveau du domaine à l’intérieur de vos entités.</span><span class="sxs-lookup"><span data-stu-id="d39c6-153">Use field-level validation on your command Data Transfer Objects (DTOs) and domain-level validation inside your entities.</span></span> <span data-ttu-id="d39c6-154">Pour cela, vous pouvez retourner un objet de résultat à la place des exceptions pour le rendre plus facile à gérer les erreurs de validation.</span><span class="sxs-lookup"><span data-stu-id="d39c6-154">You can do this by returning a result object instead exceptions in order to make it easier to deal with the validation errors.</span></span>

<span data-ttu-id="d39c6-155">À l’aide de la validation de champ et annotations de données, par exemple, vous ne dupliquez pas la définition de la validation.</span><span class="sxs-lookup"><span data-stu-id="d39c6-155">Using field validation with data annotations, for example, you do not duplicate the validation definition.</span></span> <span data-ttu-id="d39c6-156">L’exécution, il peut toutefois se côté serveur et côté client dans le cas de DTO (commandes et ViewModel, par exemple).</span><span class="sxs-lookup"><span data-stu-id="d39c6-156">The execution, though, can be both server-side and client-side in the case of DTOs (commands and ViewModels, for instance).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="d39c6-157">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="d39c6-157">Additional resources</span></span>

-   <span data-ttu-id="d39c6-158">**Rachel Appel. Introduction à la validation de modèle dans ASP.NET MVC de base**
    [*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)</span><span class="sxs-lookup"><span data-stu-id="d39c6-158">**Rachel Appel. Introduction to model validation in ASP.NET Core MVC**
[*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)</span></span>

-   <span data-ttu-id="d39c6-159">**Rick Anderson. Ajout d’une validation**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span><span class="sxs-lookup"><span data-stu-id="d39c6-159">**Rick Anderson. Adding validation**
[*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span></span>

-   <span data-ttu-id="d39c6-160">**Martin Fowler. Remplacement de lever des Exceptions avec Notification dans les Validations**
    [*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)</span><span class="sxs-lookup"><span data-stu-id="d39c6-160">**Martin Fowler. Replacing Throwing Exceptions with Notification in Validations**
[*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)</span></span>

-   <span data-ttu-id="d39c6-161">**Spécification et les modèles de Notification**
    [*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)</span><span class="sxs-lookup"><span data-stu-id="d39c6-161">**Specification and Notification Patterns**
[*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)</span></span>

-   <span data-ttu-id="d39c6-162">**Lev Gorodinski. Validation de la conception domaine (DDD)**
    [*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)</span><span class="sxs-lookup"><span data-stu-id="d39c6-162">**Lev Gorodinski. Validation in Domain-Driven Design (DDD)**
[*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)</span></span>

-   <span data-ttu-id="d39c6-163">**Colin prise. Validation de modèle de domaine**
    [*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)</span><span class="sxs-lookup"><span data-stu-id="d39c6-163">**Colin Jack. Domain Model Validation**
[*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)</span></span>

-   <span data-ttu-id="d39c6-164">**Jimmy Bogard. La validation dans un monde DDD**
    [*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)</span><span class="sxs-lookup"><span data-stu-id="d39c6-164">**Jimmy Bogard. Validation in a DDD world**
[*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="d39c6-165">[Précédente] (énumération-classes-over-enum-types.md) [suivant] (côté-client-validation.md)</span><span class="sxs-lookup"><span data-stu-id="d39c6-165">[Previous] (enumeration-classes-over-enum-types.md) [Next] (client-side-validation.md)</span></span>
