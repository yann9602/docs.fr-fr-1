---
title: "Caractéristiques des applications web modernes"
description: "Architecture des Applications Web avec ASP.NET Core et Azure | caractéristiques des applications web modernes"
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ecef23870ac547f4b4066628da71f8af98c91b27
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="characteristics-of-modern-web-applications"></a>Caractéristiques des Applications Web modernes

> "… avec la conception, les fonctionnalités sont évidemment. Cette approche est compliquée, mais continue à réussir. »  
> _\- Dennis Ritchie_

## <a name="summary"></a>Récapitulatif

Les applications web modernes ont supérieurs attentes des utilisateurs et les demandes plus que jamais auparavant. Les applications web actuelles sont censées être 24 x 7 à partir de n’importe où dans le monde et utilisables à partir de pratiquement n’importe quel appareil ou la taille de l’écran. Les applications Web doivent être sécurisée, flexible et évolutive pour répondre aux pics de la demande. De plus en plus des scénarios complexes doivent être gérés par des expériences utilisateur générées sur le client à l’aide de JavaScript et pour communiquer efficacement via l’API web.

ASP.NET Core est optimisé pour des applications web et les scénarios d’hébergement sur le cloud. Sa conception modulaire permet aux applications dépendent uniquement les fonctionnalités qu’ils utilisent en fait, amélioration des performances tout en réduisant les besoins en ressources hébergement et sécurité de l’application.

## <a name="reference-application-eshoponweb"></a>Référence d’Application : eShopOnWeb

Ce guide inclut une application de référence, *eShopOnWeb*, qui illustre certains principes et recommandations. L’application est un magasin en ligne simple qui prend en charge la navigation au sein d’un catalogue de shirts tasses de café et autres éléments de marketing. L’application de référence est délibérément simple pour le rendre facile à comprendre.

**Figure 2-1.** eShopOnWeb

![](./media/image2-1.png)

> ### <a name="reference-application"></a>Application de référence
> - **eShopOnWeb**  
> <https://github.com/dotnet/eShopOnWeb>

## <a name="cloud-hosted-and-scalable"></a>Hébergé dans le cloud et évolutive

ASP.NET Core est optimisé pour le nuage (cloud public, cloud privé, n’importe quel cloud), car il est suffisamment de mémoire et à débit élevé. L’encombrement des applications de ASP.NET Core signifie que vous pouvez héberger plusieurs d'entre eux sur le même matériel, et vous ne payez pour moins de ressources lors de la paie-sous-vous accédez aux services d’hébergement cloud. Le débit signifie que vous pouvez servir davantage de clients à partir d’une application, étant donné le même matériel, réduisant ainsi la nécessité d’investir dans les serveurs et l’infrastructure d’hébergement.

## <a name="cross-platform"></a>Multiplateforme

ASP.NET Core est interplateforme et peut s’exécuter sur Linux et MacOS, ainsi que Windows. Plusieurs nouvelles options pour le développement et déploiement d’applications générées avec ASP.NET Core s’ouvre. Les conteneurs docker, qui sont généralement exécutent Linux aujourd'hui, peuvent héberger des applications ASP.NET Core, ce qui leur permet de tirer parti des avantages de [conteneurs et microservices](../microservices-architecture/index.md).

## <a name="modular-and-loosely-coupled"></a>Faiblement couplée et modulaire

Les packages NuGet sont des citoyens dans .NET Core, et les applications ASP.NET Core sont composées de plusieurs bibliothèques via NuGet. Ce niveau de granularité des fonctionnalités garantit applications dépendent uniquement et déploiement des fonctionnalités qu’ils ont réellement besoin, en réduisant leur la surface d’exposition de vulnérabilité encombrement et de sécurité.

ASP.NET Core également prend totalement en charge l’injection de dépendances, à la fois en interne au niveau de l’application. Interfaces peuvent avoir plusieurs implémentations qui ne peuvent être transférées en fonction des besoins. Injection de dépendances permet aux applications faiblement couple à ces interfaces, ce qui les rend plus faciles à étendre, mettre à jour et de test.

## <a name="easily-tested-with-automated-tests"></a>Facilement testés avec des Tests automatisés

Les applications ASP.NET Core prennent en charge les tests unitaires et leurs un couplage faible et une prise en charge des injections de dépendance facilite la permutation des problèmes d’infrastructure avec des implémentations de fausses à des fins de test. ASP.NET Core est également fourni une TestServer qui peut être utilisé pour les applications d’hôte dans la mémoire. Les tests fonctionnels peuvent ensuite effectuer des demandes à ce serveur en mémoire, en testant la pile de l’application complète (y compris l’intergiciel (middleware), le routage, la liaison du modèle, filtres, etc.) et de recevoir une réponse, dans une fraction du temps nécessaire pour héberger l’application sur un serveur réel et faire des demandes via la couche réseau. Ces tests sont particulièrement simple à écrire et utile, pour les API qui sont plus en plus important dans les applications web modernes.

## <a name="traditional-and-spa-behaviors-supported"></a>Traditionnelles et les comportements SPA pris en charge

Les applications web traditionnelles ont impliqué peu le comportement côté client, mais au lieu de cela reposait sur le serveur pour la navigation, les requêtes et les mises à jour de que l’application devront peut-être effectuer toutes les. Chaque nouvelle opération effectuée par l’utilisateur se traduirait en une nouvelle requête web, avec le résultat est un rechargement complet de page dans le navigateur de l’utilisateur final. Les infrastructures Model-View-Controller (MVC) classiques suivent généralement cette approche, à chaque nouvelle demande correspondant à une action de l’autre contrôleur, qui à son tour fonctionne avec un modèle et retourner une vue. Certaines opérations individuelles dans une page donnée peuvent être améliorées avec des fonctionnalités AJAX (Asynchronous JavaScript and XML), mais l’architecture globale de l’application utilisée de différentes vues MVC et les points de terminaison URL.

Applications à Page unique (ZPS), impliquent en revanche, très peu de charges de page côté serveur générée dynamiquement (le cas échéant). Nombreux SPAs sont initialisés dans un fichier HTML statique, qui charge les bibliothèques JavaScript nécessaires pour démarrer et exécuter l’application. Ces applications apporter une utilisation importante d’API web pour leurs besoins en données et peuvent fournir que des expériences utilisateur plus riche.

De nombreuses applications web impliquent une combinaison de comportement de l’application web classique (en général pour le contenu) et SPAs (pour l’interactivité). ASP.NET Core prend en charge MVC et API web dans la même application, à l’aide du même ensemble d’outils et sous-jacent de bibliothèques d’infrastructure.

## <a name="simple-development-and-deployment"></a>Déploiement et développement simple

Les applications ASP.NET Core peuvent être écrits à l’aide d’éditeurs de texte simple et interfaces de ligne de commande ou les environnements de développement complet comme Visual Studio. Applications monolithiques sont généralement déployées sur un seul point de terminaison. Déploiements peuvent facilement être automatisés pour se produire dans le cadre d’une intégration continue (CI) et le pipeline de livraison continue (CD). En plus des outils de l’élément de configuration/CD traditionnelles, Windows Azure prend en charge pour les référentiels git et peut déployer automatiquement les mises à jour qu’elles sont faites à une branche git spécifié ou de la balise.

## <a name="traditional-aspnet-and-web-forms"></a>ASP.NET traditionnel et les Web Forms

En plus de ASP.NET Core, ASP.NET traditionnel 4.x continue à être une plateforme robuste et fiable pour la création d’applications web. ASP.NET prend en charge les modèles de développement MVC et les API Web, ainsi que des Web Forms, qui convient parfaitement au développement d’applications basé sur la page de riches et des fonctionnalités d’un écosystème complet composant tiers. Windows Azure a soutien commune pour les applications ASP.NET 4.x, et de nombreux développeurs sont familiarisés avec cette plateforme.

> ### <a name="references--modern-web-applications"></a>Références à des Applications Web
> - **Présentation d’ASP.NET Core**  
> <https://docs.microsoft.com/aspnet/core/>
> - **Six clé avantages d’ASP.NET Core qui rendent différentes et mieux**  
> <https://blog.trigent.com/six-key-benefits-of-asp-net-core-1-0-which-make-it-different-better/>
> - **Les tests dans ASP.NET Core**  
> <https://docs.microsoft.com/aspnet/core/testing/>

>[!div class="step-by-step"]
[Précédente] (index.md) [suivant] (choose-between-traditional-web-and-single-page-apps.md)
