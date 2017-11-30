---
title: "Validation côté client (validation dans les couches de présentation)"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Validation côté client (validation dans les couches de présentation)"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: db88a3b5c95afdc8d5a20094105f1f5991483ed6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a><span data-ttu-id="b948c-104">Validation côté client (validation dans les couches de présentation)</span><span class="sxs-lookup"><span data-stu-id="b948c-104">Client-side validation (validation in the presentation layers)</span></span>

<span data-ttu-id="b948c-105">Même lorsque la source de vérité est le modèle de domaine, et enfin, vous devez avoir validation au niveau du modèle de domaine, la validation peut toujours être gérée au niveau du modèle de domaine (côté serveur) et le côté client.</span><span class="sxs-lookup"><span data-stu-id="b948c-105">Even when the source of truth is the domain model and ultimately you must have validation at the domain model level, validation can still be handled at both the domain model level (server side) and the client side.</span></span>

<span data-ttu-id="b948c-106">La validation côté client est très pratique pour les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="b948c-106">Client-side validation is a great convenience for users.</span></span> <span data-ttu-id="b948c-107">Il enregistre à temps serait sinon attend un aller-retour sur le serveur qui peut-être retourner des erreurs de validation.</span><span class="sxs-lookup"><span data-stu-id="b948c-107">It saves time they would otherwise spend waiting for a round trip to the server that might return validation errors.</span></span> <span data-ttu-id="b948c-108">En termes de l’entreprise, même quelques fractions de secondes multipliés des centaines de fois par jour additionne une grande quantité de temps, des frais et frustration.</span><span class="sxs-lookup"><span data-stu-id="b948c-108">In business terms, even a few fractions of seconds multiplied hundreds of times each day adds up to a lot of time, expense, and frustration.</span></span> <span data-ttu-id="b948c-109">Validation simple et immédiate permet aux utilisateurs de travailler plus efficacement et de produire une meilleure qualité d’entrée et sortie.</span><span class="sxs-lookup"><span data-stu-id="b948c-109">Straightforward and immediate validation enables users to work more efficiently and produce better quality input and output.</span></span>

<span data-ttu-id="b948c-110">Tout comme le modèle d’affichage et le modèle de domaine sont différents, validation de modèle d’affichage et validation de modèle de domaine peuvent être semblable, mais servent un objectif différent.</span><span class="sxs-lookup"><span data-stu-id="b948c-110">Just as the view model and the domain model are different, view model validation and domain model validation might be similar but serve a different purpose.</span></span> <span data-ttu-id="b948c-111">Si vous êtes concerné sur sec (ne pas se répéter principe), envisagez de réutilisation du code dans ce cas peut également signifier que couplage que dans les applications d’entreprise, il est plus important de ne pas associer le côté serveur vers le côté client que pour suivez le principe sec.</span><span class="sxs-lookup"><span data-stu-id="b948c-111">If you are concerned about DRY (the Don’t Repeat Yourself principle), consider that in this case code reuse might also mean coupling, and in enterprise applications it is more important not to couple the server side to the client side than to follow the DRY principle.</span></span>

<span data-ttu-id="b948c-112">Même lorsque vous utilisez la validation côté client, vous devez toujours valider vos commandes ou d’entrée DTO dans le code serveur, car les API du serveur sont un vecteur d’attaque possibles.</span><span class="sxs-lookup"><span data-stu-id="b948c-112">Even when using client-side validation, you should always validate your commands or input DTOs in server code, because the server APIs are a possible attack vector.</span></span> <span data-ttu-id="b948c-113">En règle générale, cela est la meilleure solution, car si vous avez une application cliente, du point de vue de l’expérience utilisateur, il est recommandé d’être proactive et n’autorise pas l’utilisateur à entrer des informations non valides.</span><span class="sxs-lookup"><span data-stu-id="b948c-113">Usually, doing both is your best bet because if you have a client application, from a UX perspective, it is best to be proactive and not allow the user to enter invalid information.</span></span>

<span data-ttu-id="b948c-114">Par conséquent, dans le code côté client il vous généralement de valider les ViewModel.</span><span class="sxs-lookup"><span data-stu-id="b948c-114">Therefore, in client-side code you typically validate the ViewModels.</span></span> <span data-ttu-id="b948c-115">Vous pourriez valider également le client DTO ou des commandes de sortie avant de les envoyer aux services.</span><span class="sxs-lookup"><span data-stu-id="b948c-115">You could also validate the client output DTOs or commands before you send them to the services.</span></span>

<span data-ttu-id="b948c-116">L’implémentation de la validation côté client dépend de quel type d’application cliente que vous créez.</span><span class="sxs-lookup"><span data-stu-id="b948c-116">The implementation of client-side validation depends on what kind of client application you are building.</span></span> <span data-ttu-id="b948c-117">Il sera différente si vous validez des données dans une application web MVC web avec la plupart du code dans .NET, une application web SPA avec cette validation qui est codée en JavaScript ou TypeScript, ou une application mobile codé avec Xamarin et C\#.</span><span class="sxs-lookup"><span data-stu-id="b948c-117">It will be different if you are validating data in a web MVC web application with most of the code in .NET, an SPA web application with that validation being coded in JavaScript or TypeScript, or a mobile app coded with Xamarin and C\#.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="b948c-118">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="b948c-118">Additional resources</span></span>

### <a name="validation-in-xamarin-mobile-apps"></a><span data-ttu-id="b948c-119">Validation dans les applications mobiles Xamarin</span><span class="sxs-lookup"><span data-stu-id="b948c-119">Validation in Xamarin mobile apps</span></span>

-   <span data-ttu-id="b948c-120">**Valider le texte d’entrée et afficher les erreurs**
    [*https://developer.xamarin.com/recipes/ios/standard\_contrôles/texte\_/valider le champ\_d’entrée /*](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)</span><span class="sxs-lookup"><span data-stu-id="b948c-120">**Validate Text Input and Show Errors**
[*https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/*](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)</span></span>

-   <span data-ttu-id="b948c-121">**Rappel de validation**
    [*https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/*](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)</span><span class="sxs-lookup"><span data-stu-id="b948c-121">**Validation Callback**
[*https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/*](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)</span></span>

### <a name="validation-in-aspnet-core-apps"></a><span data-ttu-id="b948c-122">Validation dans les applications ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b948c-122">Validation in ASP.NET Core apps</span></span>

-   <span data-ttu-id="b948c-123">**Rick Anderson. Ajout d’une validation**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span><span class="sxs-lookup"><span data-stu-id="b948c-123">**Rick Anderson. Adding validation**
[*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span></span>

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a><span data-ttu-id="b948c-124">Validation de SPA Web Applications (2 angulaire, TypeScript, JavaScript)</span><span class="sxs-lookup"><span data-stu-id="b948c-124">Validation in SPA Web apps (Angular 2, TypeScript, JavaScript)</span></span>

-   <span data-ttu-id="b948c-125">**ADO Kukic. La Validation du formulaire 2 angulaire** **
     ** [ *https://scotch.io/tutorials/angular-2-form-validation*](https://scotch.io/tutorials/angular-2-form-validation)</span><span class="sxs-lookup"><span data-stu-id="b948c-125">**Ado Kukic. Angular 2 Form Validation** **
**[*https://scotch.io/tutorials/angular-2-form-validation*](https://scotch.io/tutorials/angular-2-form-validation)</span></span>

-   <span data-ttu-id="b948c-126">**La Validation du formulaire**
    [*https://angular.io/docs/ts/latest/cookbook/form-validation.html*](https://angular.io/docs/ts/latest/cookbook/form-validation.html)</span><span class="sxs-lookup"><span data-stu-id="b948c-126">**Form Validation**
[*https://angular.io/docs/ts/latest/cookbook/form-validation.html*](https://angular.io/docs/ts/latest/cookbook/form-validation.html)</span></span>

-   <span data-ttu-id="b948c-127">**Validation.**</span><span class="sxs-lookup"><span data-stu-id="b948c-127">**Validation.**</span></span> <span data-ttu-id="b948c-128">Documentation est très simple.</span><span class="sxs-lookup"><span data-stu-id="b948c-128">Breeze documentation.</span></span>
    [<span data-ttu-id="b948c-129">*http://Breeze.github.IO/doc-js/validation.HTML*</span><span class="sxs-lookup"><span data-stu-id="b948c-129">*http://breeze.github.io/doc-js/validation.html*</span></span>](http://breeze.github.io/doc-js/validation.html)

<span data-ttu-id="b948c-130">En résumé, il s’agit des concepts les plus importants en ce qui concerne la validation :</span><span class="sxs-lookup"><span data-stu-id="b948c-130">In summary, these are the most important concepts in regards to validation:</span></span>

-   <span data-ttu-id="b948c-131">Entités et des agrégats doivent appliquer leur propre cohérence et être « toujours valide ».</span><span class="sxs-lookup"><span data-stu-id="b948c-131">Entities and aggregates should enforce their own consistency and be "always valid”.</span></span> <span data-ttu-id="b948c-132">Racines d’agrégat sont responsables de la cohérence de plusieurs entitée dans le même regroupement.</span><span class="sxs-lookup"><span data-stu-id="b948c-132">Aggregate roots are responsible for multi-entity consistency within the same aggregate.</span></span>

-   <span data-ttu-id="b948c-133">Si vous pensez qu’une entité doit entrer dans un état non valide, envisagez d’utiliser un modèle d’objet différent, par exemple, à l’aide de DTO temporaire jusqu'à ce que vous créez l’entité de domaine final.</span><span class="sxs-lookup"><span data-stu-id="b948c-133">If you think that an entity needs to enter an invalid state, consider using a different object model—for example, using a temporary DTO until you create the final domain entity.</span></span>

-   <span data-ttu-id="b948c-134">Si vous devez créer plusieurs objets connexes, comme un agrégat, et ils sont uniquement valides une fois que tous les ont été créés, envisagez d’utiliser le modèle de fabrique.</span><span class="sxs-lookup"><span data-stu-id="b948c-134">If you need to create several related objects, such as an aggregate, and they are only valid once all of them have been created, consider using the Factory pattern.</span></span>

-   <span data-ttu-id="b948c-135">Infrastructures de validation sont préférable d’utiliser dans des couches spécifiques, telles que la couche de présentation ou de la couche de service ou application, mais généralement pas dans la couche de modèle de domaine, car vous devez prendre une dépendance fort sur une infrastructure de l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="b948c-135">Validation frameworks are best used in specific layers, such as the presentation layer or the application/service layer, but usually not in the domain model layer, because you would need to take a strong dependency on an infrastructure framework.</span></span>

-   <span data-ttu-id="b948c-136">Dans la plupart des cas, un redondant validation côté client n’est correct, car l’application peut être proactive.</span><span class="sxs-lookup"><span data-stu-id="b948c-136">In most of the cases, having redundant validation in the client side is good, because the application can be proactive.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="b948c-137">[Précédente] (domaine-modèle-layer-validations.md) [suivant] (domaine-événements-design-implementation.md)</span><span class="sxs-lookup"><span data-stu-id="b948c-137">[Previous] (domain-model-layer-validations.md) [Next] (domain-events-design-implementation.md)</span></span>
