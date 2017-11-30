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
# <a name="client-side-validation-validation-in-the-presentation-layers"></a>Validation côté client (validation dans les couches de présentation)

Même lorsque la source de vérité est le modèle de domaine, et enfin, vous devez avoir validation au niveau du modèle de domaine, la validation peut toujours être gérée au niveau du modèle de domaine (côté serveur) et le côté client.

La validation côté client est très pratique pour les utilisateurs. Il enregistre à temps serait sinon attend un aller-retour sur le serveur qui peut-être retourner des erreurs de validation. En termes de l’entreprise, même quelques fractions de secondes multipliés des centaines de fois par jour additionne une grande quantité de temps, des frais et frustration. Validation simple et immédiate permet aux utilisateurs de travailler plus efficacement et de produire une meilleure qualité d’entrée et sortie.

Tout comme le modèle d’affichage et le modèle de domaine sont différents, validation de modèle d’affichage et validation de modèle de domaine peuvent être semblable, mais servent un objectif différent. Si vous êtes concerné sur sec (ne pas se répéter principe), envisagez de réutilisation du code dans ce cas peut également signifier que couplage que dans les applications d’entreprise, il est plus important de ne pas associer le côté serveur vers le côté client que pour suivez le principe sec.

Même lorsque vous utilisez la validation côté client, vous devez toujours valider vos commandes ou d’entrée DTO dans le code serveur, car les API du serveur sont un vecteur d’attaque possibles. En règle générale, cela est la meilleure solution, car si vous avez une application cliente, du point de vue de l’expérience utilisateur, il est recommandé d’être proactive et n’autorise pas l’utilisateur à entrer des informations non valides.

Par conséquent, dans le code côté client il vous généralement de valider les ViewModel. Vous pourriez valider également le client DTO ou des commandes de sortie avant de les envoyer aux services.

L’implémentation de la validation côté client dépend de quel type d’application cliente que vous créez. Il sera différente si vous validez des données dans une application web MVC web avec la plupart du code dans .NET, une application web SPA avec cette validation qui est codée en JavaScript ou TypeScript, ou une application mobile codé avec Xamarin et C\#.

## <a name="additional-resources"></a>Ressources supplémentaires

### <a name="validation-in-xamarin-mobile-apps"></a>Validation dans les applications mobiles Xamarin

-   **Valider le texte d’entrée et afficher les erreurs**
    [*https://developer.xamarin.com/recipes/ios/standard\_contrôles/texte\_/valider le champ\_d’entrée /*](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)

-   **Rappel de validation**
    [*https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/*](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)

### <a name="validation-in-aspnet-core-apps"></a>Validation dans les applications ASP.NET Core

-   **Rick Anderson. Ajout d’une validation**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a>Validation de SPA Web Applications (2 angulaire, TypeScript, JavaScript)

-   **ADO Kukic. La Validation du formulaire 2 angulaire** **
     ** [ *https://scotch.io/tutorials/angular-2-form-validation*](https://scotch.io/tutorials/angular-2-form-validation)

-   **La Validation du formulaire**
    [*https://angular.io/docs/ts/latest/cookbook/form-validation.html*](https://angular.io/docs/ts/latest/cookbook/form-validation.html)

-   **Validation.** Documentation est très simple.
    [*http://Breeze.github.IO/doc-js/validation.HTML*](http://breeze.github.io/doc-js/validation.html)

En résumé, il s’agit des concepts les plus importants en ce qui concerne la validation :

-   Entités et des agrégats doivent appliquer leur propre cohérence et être « toujours valide ». Racines d’agrégat sont responsables de la cohérence de plusieurs entitée dans le même regroupement.

-   Si vous pensez qu’une entité doit entrer dans un état non valide, envisagez d’utiliser un modèle d’objet différent, par exemple, à l’aide de DTO temporaire jusqu'à ce que vous créez l’entité de domaine final.

-   Si vous devez créer plusieurs objets connexes, comme un agrégat, et ils sont uniquement valides une fois que tous les ont été créés, envisagez d’utiliser le modèle de fabrique.

-   Infrastructures de validation sont préférable d’utiliser dans des couches spécifiques, telles que la couche de présentation ou de la couche de service ou application, mais généralement pas dans la couche de modèle de domaine, car vous devez prendre une dépendance fort sur une infrastructure de l’infrastructure.

-   Dans la plupart des cas, un redondant validation côté client n’est correct, car l’application peut être proactive.


>[!div class="step-by-step"]
[Précédente] (domaine-modèle-layer-validations.md) [suivant] (domaine-événements-design-implementation.md)
