---
title: Pour choisir le .NET Framework pour les conteneurs Docker
description: Architecture de Microservices .NET pour les Applications .NET en conteneur | Pour choisir le .NET Framework pour les conteneurs Docker
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 1bf1f055f040e7f3dc575b7a04140ebf0c599f98
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a>Pour choisir le .NET Framework pour les conteneurs Docker

Alors que le .NET Core offre des avantages significatifs pour les nouvelles applications et des modèles d’application, .NET Framework continueront à être un bon choix pour de nombreux scénarios existants.

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a>Migration d’applications existant directement vers un conteneur Windows Server

Vous souhaitez utiliser des conteneurs Docker seulement pour simplifier le déploiement, même si vous ne créez pas de microservices. Par exemple, vous pouvez améliorer votre flux de travail DevOps avec Docker, conteneurs peut vous fournir des environnements mieux isolé et pouvez également éliminer les problèmes de déploiement provoqués par les dépendances manquantes lorsque vous déplacez vers un environnement de production. Dans ce cas, même si vous déployez une application monolithique, il est judicieux d’utiliser des conteneurs Windows et Docker pour vos applications .NET Framework en cours.

Dans la plupart des cas pour ce scénario, vous aurez pas à migrer vos applications existantes vers le .NET Core ; Vous pouvez utiliser des conteneurs Docker qui incluent le .NET Framework traditionnelles. Toutefois, une approche recommandée consiste à utiliser le .NET Core que vous étendez une application existante, telles que l’écriture d’un nouveau service dans ASP.NET Core.

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>À l’aide de bibliothèques .NET de tiers ou les packages NuGet non disponibles pour le .NET Core

Des bibliothèques tierces rapidement adoptent le [.NET Standard](https://docs.microsoft.com/dotnet/standard/net-standard), qui permet au code partager entre toutes les versions de .NET, y compris .NET Core. Avec la bibliothèque .NET Standard version 2.0 et au-delà de la surface API compatibilité entre les différentes infrastructures est devenue beaucoup plus important et dans .NET Core 2.0 applications peuvent également faire directement référence les bibliothèques .NET Framework existantes (consultez [compat shim](https://github.com/dotnet/standard/blob/master/docs/faq.md#how-does-net-standard-versioning-work)).

Toutefois, même si cette progression exceptionnelle depuis Standard de .NET 2.0 et .NET Core 2.0, il peut arriver dans lequel certains packages NuGet doivent exécuter Windows et ne peuvent pas prendre en charge .NET Core. Si ces packages sont essentiels pour votre application, vous devez utiliser le .NET Framework sur les conteneurs Windows.

## <a name="usingnet-technologies-not-available-for-net-core"></a>Technologies Using.NET non disponibles pour le .NET Core 

Certaines technologies .NET Framework ne sont pas disponibles dans la version actuelle du .NET Core (version 2.0 à ce jour). Certaines d'entre elles seront disponibles dans les versions ultérieures de .NET Core (.NET Core 2.x), mais d’autres ne s’appliquent pas à la nouvelle application modèles ciblée par le .NET Core et ne peuvent jamais être disponibles.

La liste suivante présente la plupart des technologies qui ne sont pas disponibles dans .NET Core 2.0 :

-   Web Forms ASP.NET. Cette technologie est uniquement disponible sur .NET Framework. Il n’est pas prévu d’intégrer Web Forms ASP.NET à .NET Core.

-   Services WCF. Même lorsqu’une [bibliothèque cliente de WCF](https://github.com/dotnet/wcf) est disponible pour consommer des services WCF à partir de .NET Core. à compter de mid 2017, l’implémentation du serveur WCF est uniquement disponible sur .NET Framework. Ce scénario peut être considéré comme des futures versions du .NET Core.

-   Services liés au workflow. Windows Workflow Foundation (WF), Services de Workflow (WCF + WF dans un seul service) et les Services de données WCF (anciennement appelé ADO.NET Data Services) sont uniquement disponibles sur le .NET Framework. Il n’existe actuellement aucun plan pour les mettre dans .NET Core.

Outre les technologies répertoriées dans officielle [feuille de route pour le .NET Core](https://github.com/aspnet/Home/wiki/Roadmap), autres fonctionnalités peuvent être déplacées vers le .NET Core. Pour obtenir la liste complète, examinez les éléments marqués en tant que [port-cœur](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core) sur le site CoreFX GitHub. Notez que cette liste ne représente pas un engagement de Microsoft pour rétablir les composants .NET Core, les éléments capturent simplement des demandes à partir de la Communauté. Si vous vous souciez tous les composants répertoriés ci-dessus, envisagez de participer aux discussions sur GitHub afin que votre voix puisse être entendue. Et si vous pensez que quelque chose fait défaut, veuillez [enregistrer un nouveau problème dans le dépôt CoreFX](https://github.com/dotnet/corefx/issues/new).

## <a name="using-a-platform-or-api-that-does-not-support-net-core"></a>À l’aide d’une plateforme ou une API qui ne prend pas en charge le .NET Core

Certaines plateformes tierces ou Microsoft ne prennent pas en charge .NET Core. Par exemple, certains services Azure fournissent un kit de développement logiciel qui n’est pas encore disponible pour la consommation sur .NET Core. Cela est temporaire, car tous les services Azure utilise finalement .NET Core. Par exemple, le [Azure DocumentDB SDK pour .NET Core](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core/1.2.1) a été publiée en tant qu’aperçu du 16 novembre 2016, mais il est désormais disponible de manière générale (GA) en tant qu’une version stable.

En attendant, si toute plate-forme ou un service dans Azure encore ne prennent en charge .NET Core avec son API client, vous pouvez utiliser l’API REST équivalent à partir du service Azure ou le client SDK sur .NET Framework.

### <a name="additional-resources"></a>Ressources supplémentaires

-   **Guide de .NET core**
    [*https://docs.microsoft.com/dotnet/core/index*](https://docs.microsoft.com/dotnet/core/index)

-   **Portage de .NET Framework vers le .NET Core**
    [*https://docs.microsoft.com/dotnet/core/porting/index*](https://docs.microsoft.com/dotnet/core/porting/index)

-   **.NET framework sur le Guide de Docker**
    [*https://docs.microsoft.com/dotnet/framework/docker/*](https://docs.microsoft.com/dotnet/framework/docker/)

-   **Vue d’ensemble des composants .NET**
    [*https://docs.microsoft.com/dotnet/standard/components*](https://docs.microsoft.com/dotnet/standard/components)




>[!div class="step-by-step"]
[Précédente] (net-core-conteneur-scenarios.md) [suivant] (conteneur-framework-choix-factors.md)
