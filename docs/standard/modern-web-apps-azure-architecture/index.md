---
title: Architecturer des applications web modernes avec ASP.NET Core et Azure
description: Architecturer des applications web modernes avec ASP.NET Core et Azure | Introduction
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: db9f0ddd875df1f84bcc5681ee1383b0185f8b7e
ms.sourcegitcommit: e2bf8e6bc365bd9a0e86fe81eeae7d14f85f48c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/13/2018
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a>Architecturer des applications web modernes avec ASP.NET Core et Azure

![image de couverture](./media/cover.jpg)


.NET Core et ASP.NET Core offrent plusieurs avantages par rapport au développement .NET classique. Il est recommandé d’utiliser .NET Core pour vos applications serveur si tout ou partie des éléments suivants sont importants pour la réussite de votre application :

-   Prise en charge multiplateforme

-   Utilisation de microservices

-   Utilisation de conteneurs Docker

-   Nécessité de hautes performances et de scalabilité

-   Gestion des versions côte à côte des versions de .NET par application sur le même serveur

Les applications .NET classiques prennent en charge ces spécifications, mais ASP.NET Core et .NET Core ont été optimisés pour offrir une prise en charge améliorée des scénarios ci-dessus.

De plus en plus d’organisations choisissent d’héberger leurs applications web dans le cloud en utilisant des services comme Microsoft Azure. Envisagez d’héberger votre application dans le cloud si les points suivants sont importants pour votre application ou votre organisation :

-   Réduction des investissements dans les coûts des centres de données (matériel, logiciel, espace, utilitaires, etc.)

-   Tarification flexible (paiement basé sur l’utilisation et non pas pour une capacité inactive)

-   Extrême fiabilité

-   Mobilité accrue de l’application ; changement facile de l’endroit et de la façon dont votre application est déployée

-   Capacité flexible ; montée ou descente en puissance en fonction des besoins réels

La création d’applications web avec ASP.NET Core, hébergées dans Microsoft Azure, offre de nombreux avantages concurrentiels par rapport aux alternatives classiques. ASP.NET Core est optimisé pour les pratiques de développement d’applications web modernes et les scénarios d’hébergement cloud. Dans ce guide, vous découvrez comment architecturer vos applications ASP.NET Core pour tirer le meilleur parti de ces fonctionnalités.

## <a name="purpose"></a>Objectif

Ce guide fournit une aide de bout en bout sur la création d’applications web monolithiques avec ASP.NET Core et Azure.

Ce guide vient en complément de « *Architecting and Developing Containerized and Microservice-based Applications with .NET* », qui est davantage consacré à Docker, aux microservices et au déploiement de conteneurs pour héberger des applications d’entreprise.

> ### <a name="architecting-and-developing-containerized-microservice-based-apps-in-net"></a>Architecture et développement d’applications basées sur des microservices en conteneur dans .NET
> - **Livre électronique**  
> <http://aka.ms/MicroservicesEbook>
> - **Exemple d’application**  
> <http://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a>Public visé par ce guide

Le public visé par ce guide est principalement constitué de développeurs, de responsables du développement et d’architectes qui sont intéressés par la création d’applications web modernes avec des technologies et des services Microsoft dans le cloud.

Il s’adresse aussi aux décideurs techniques qui connaissent déjà ASP.NET et/ou Azure, et qui recherchent des informations sur la pertinence d’un passage à ASP.NET Core pour des projets nouveaux ou existants.

## <a name="how-you-can-use-this-guide"></a>Utilisation de ce guide

Ce guide a été condensé en un document relativement court, qui est consacré à la création d’applications web avec des technologies .NET modernes et Microsoft Azure. Il peut ainsi être lu dans sa totalité, et permet de comprendre ces applications et les considérations techniques qui s’y rattachent. Le guide, ainsi que son exemple d’application, peut aussi servir de point de départ ou de référence. Utilisez l’exemple d’application associé comme modèle pour vos propres applications, ou pour voir comment organiser les composants de votre application. Reportez-vous aux principes exposés dans le guide, à la couverture des options d’architecture et de technologie, et aux considérations sur les décisions à prendre quand vous évaluez ces choix pour votre propre application.

N’hésitez pas à faire connaître ce guide pour favoriser une compréhension partagée de ces considérations et de ces opportunités. Le fait que chacun utilise un même ensemble de terminologie et de principes sous-jacents permet d’obtenir plus facilement une application cohérente des modèles et des pratiques en matière d’architecture.

## <a name="references"></a>Références
- **Choix entre .NET Core et .NET Framework pour les applications serveur**  
<https://docs.microsoft.com/dotnet/articles/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
[Suivant] (modern-web-applications-characteristics.md)
