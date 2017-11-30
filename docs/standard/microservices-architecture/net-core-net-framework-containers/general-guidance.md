---
title: "Conseils généraux"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Conseils généraux"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 22dea926e77079e4f543934613ced13a28b2dae6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="general-guidance"></a>Conseils généraux

Cette section fournit un résumé des choix .NET Core ou .NET Framework. Nous fournir plus de détails sur ces options dans les sections qui suivent.

Vous devez utiliser .NET Core, avec les conteneurs Windows ou Linux pour votre application de serveur Docker en conteneur lorsque :

-   vous avez des besoins multiplateformes ; Par exemple, vous souhaitez utiliser les conteneurs Linux et Windows.

-   Architecture de votre application repose sur microservices.

-   Vous devez démarrer rapide des conteneurs et un faible encombrement mémoire par atteindre une meilleure densité ou les conteneurs plus par unité de matériel afin de réduire les coûts.

En bref, lorsque vous créez des applications .NET en conteneur, vous devez considérer .NET Core comme l’option par défaut. Il présente de nombreux avantages et répond le mieux à la philosophie de conteneurs et le style de travail.

Un autre avantage de l’utilisation de .NET Core est que vous pouvez exécuter des versions côte à côte du .NET pour les applications dans le même ordinateur. Cet avantage est plus important pour les serveurs ou ordinateurs virtuels qui n’utilisent pas de conteneurs, étant donné que les conteneurs d’isoler les versions de .NET dont l’application a besoin. (Tant qu’ils sont compatibles avec le système d’exploitation sous-jacent.)

Vous devez utiliser .NET Framework, les conteneurs Windows pour votre application de serveur Docker en conteneur lorsque :

-   Actuellement, votre application utilise le .NET Framework et a des dépendances fortes sur Windows.

-   Vous devez utiliser les API Windows qui ne sont pas pris en charge par .NET Core.

-   Vous devez utiliser les bibliothèques .NET de tiers ou les packages NuGet qui ne sont pas disponibles pour .NET Core.

À l’aide de .NET Framework sur Docker peut améliorer votre expérience de déploiement en réduisant les problèmes de déploiement. Cela [ *scénario « de courbes d’élévation et MAJ »* ](https://aka.ms/liftandshiftwithcontainersebook) est important pour containerizing les applications héritées qui ont été développées à l’origine avec le .NET Framework classiques, telles que ASP.NET WebForms, MVC web apps ou WCF ( Services Windows Communication Foundation).

### <a name="additional-resources"></a>Ressources supplémentaires

-   **livres : moderniser des applications .NET Framework existantes avec Azure et les conteneurs Windows**
    [*https://aka.ms/liftandshiftwithcontainersebook*](https://aka.ms/liftandshiftwithcontainersebook)

-   **Exemples d’applications : modernisation des applications web ASP.NET héritées à l’aide de conteneurs Windows**
    [*https://aka.ms/eshopmodernizing*](https://aka.ms/eshopmodernizing)


>[!div class="step-by-step"]
[Précédente] (index.md) [suivant] (net-core-conteneur-scenarios.md)
