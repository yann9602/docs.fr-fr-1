---
title: Choix entre .NET Core et .NET Framework pour les applications serveur
description: "Guide sur la version de .NET à envisager pour générer une application serveur dans .NET."
keywords: .NET, .NET Core, .NET Framework
author: cartermp
manager: wpickett
ms.author: phcart
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 155553e4-89a2-418d-be88-4e75f6c3cc69
translationtype: Human Translation
ms.sourcegitcommit: d6ce9e3dd3c1189f35d147d140bb45095b3d77a5
ms.openlocfilehash: a0563f7437711ddbee309803e97ab653aa160337

---

# <a name="choosing-between-net-core-and-net-framework-for-server-apps"></a>Choix entre .NET Core et .NET Framework pour les applications serveur

Il existe deux options de runtime pour générer des applications serveur avec .NET : .NET Framework et .NET Core. Toutes deux partagent un grand nombre de composants de plateforme .NET et vous permettent de partager du code entre les deux. Toutefois, il existe des différences fondamentales entre les deux et votre choix dépend de ce que vous souhaitez accomplir.  Cet article fournit des conseils sur l’utilisation de chacune.

Vous devez utiliser .NET Core pour votre application serveur quand :

* vous avez des besoins multiplateformes ;
* vous ciblez des microservices ;
* vous utilisez des conteneurs Docker ;
* vous avez besoin de systèmes scalables et hautes performances ;
* vous avez besoin d’une installation côte à côte de versions .NET par application.

Vous devez utiliser .NET Framework pour votre application serveur quand :

* votre application utilise .NET Framework (nous vous recommandons de privilégier l’extension à la migration) ;
* vous devez utiliser des packages NuGet ou des bibliothèques .NET tiers non disponibles pour .NET Core ;
* vous devez utiliser des technologies .NET non disponibles pour .NET Core ;
* vous devez utiliser une plateforme qui ne prend pas en charge .NET Core.

## <a name="when-to-choose-net-core"></a>Quand choisir .NET Core

Voici une explication plus détaillée des raisons indiquées précédemment justifiant le choix de .NET Core.

### <a name="cross-platform-needs"></a>Besoins multiplateformes

De toute évidence, si votre objectif est d’avoir une application (web/service) qui peut s’exécuter sur plusieurs plateformes (Windows, Linux et macOS), le meilleur choix est d’utiliser .NET Core.

En outre, .NET Core prend en charge les systèmes d’exploitation précédemment mentionnés comme station de travail de développement. Visual Studio fournit un environnement de développement intégré (IDE) pour Windows.  Vous pouvez également utiliser Visual Studio Code sur macOS, Linux et Windows, qui prennent entièrement en charge .NET Core, y compris IntelliSense et le débogage. Vous pouvez cibler .NET Core avec la plupart des éditeurs tiers comme Sublime, Emacs, VI, et profiter de la fonctionnalité d’édition IntelliSense à l’aide du projet [Omnisharp](http://www.omnisharp.net/) open source. Vous pouvez aussi vous affranchir des éditeurs de code et utiliser directement les outils en ligne de commande .NET Core, disponibles pour toutes les plateformes prises en charge.

### <a name="microservices-architecture"></a>Architecture en microservices

.NET Core est la meilleure solution dans le cadre d’un système orienté microservices composé de plusieurs microservices indépendants, dynamiquement scalables, avec ou sans état. .NET Core est léger et la surface de son API peut être réduite à l’étendue du microservice. Grâce à une architecture en microservices, vous pouvez combiner des technologies au-delà de la limite d’un service, permettant ainsi une prise en charge progressive de .NET Core pour de nouveaux microservices qui côtoient d’autres microservices ou services développés avec .NET Framework, Java, Ruby ou d’autres technologies monolithiques.

Vous pouvez utiliser de nombreuses plateformes d’infrastructure. Pour les systèmes de microservice volumineux et complexes, vous pouvez utiliser [Azure Service Fabric](https://azure.microsoft.com/en-us/services/service-fabric/). Pour les microservices sans état, vous pouvez également utiliser d’autres produits tels qu’[Azure App Service](https://azure.microsoft.com/en-us/services/app-service/). Les alternatives aux microservices basées sur Docker s’intègrent aussi à tout type d’approche des microservices, comme expliqué ci-après. Toutes ces plateformes prennent en charge .NET Core et s’avèrent idéales pour l’hébergement de vos microservices.

### <a name="containers"></a>Conteneurs

Les conteneurs sont couramment utilisés avec une architecture en microservices, même s’ils peuvent également servir à organiser en conteneurs les services ou applications web qui suivent un modèle architectural. Vous pouvez utiliser .NET Framework pour les conteneurs Windows, mais par sa modularité et sa légèreté, .NET Core est parfait pour les conteneurs.  Quand vous créez et déployez un conteneur, la taille de son image est beaucoup plus petite avec .NET Core qu’avec .NET Framework.  Grâce à sa nature multiplateforme, vous pouvez déployer des applications serveur sur des conteneurs Docker Linux, par exemple.

Vous pouvez ensuite héberger vos conteneurs Docker dans votre propre infrastructure Linux ou Windows, ou utiliser un service cloud tel qu’[Azure Container Service](https://azure.microsoft.com/en-us/services/container-service/) qui peut gérer, orchestrer et mettre à l’échelle votre application conteneur dans le cloud.

### <a name="a-need-for-high-performance-and-scalable-systems"></a>Besoin de systèmes scalables et hautes performances

Quand votre système a besoin de performances et d’une scalabilité optimales, .NET Core et ASP.NET Core sont vos meilleures options. ASP.NET Core surpasse ASP.NET d’un facteur de 10 et devance les autres technologies courantes pour les microservices telles que les servlets Java, Go et node.js.

Cela est particulièrement vrai pour les architectures en microservices qui peuvent compter des centaines de microservices en cours d’exécution. Avec ASP.NET Core, vous pouvez exécuter votre système avec un nombre de serveurs/machines virtuelles largement inférieur, économisant ainsi des coûts en infrastructure et hébergement.

### <a name="a-need-for-side-by-side-of-net-versions-per-application-level"></a>Besoin d’une installation côte à côte de versions .NET par niveau d’application

Pour installer des applications avec des dépendances sur différentes versions de frameworks dans .NET, vous devez utiliser .NET Core, qui permet une installation 100 % côte à côte. Grâce à une installation côte à côte facile de différentes versions de .NET Core sur le même ordinateur, vous disposez de plusieurs services sur le même serveur, chacun d’eux sur sa propre version de .NET Core, éliminant ainsi les risques et réduisant les coûts des opérations informatiques et des mises à niveau des applications.

## <a name="when-to-choose-net-framework"></a>Quand choisir .NET Framework

Si .NET Core offre des avantages significatifs pour les nouvelles applications et les modèles d’application, .NET Framework demeure le choix naturel pour de nombreux scénarios existants et n’est donc pas remplacé par .NET Core pour toutes les applications serveur.

### <a name="current-net-framework-applications"></a>Applications .NET Framework actuelles

Dans la plupart des cas, vous ne devez pas migrer vos applications existantes vers .NET Core. Il est plutôt recommandé d’utiliser .NET Core quand vous étendez une application existante, telle que l’écriture d’un service web dans ASP.NET Core.

### <a name="a-need-to-use-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Besoin d’utiliser des packages NuGet ou des bibliothèques .NET tiers non disponibles pour .NET Core

Les bibliothèques adoptent rapidement .NET Standard qui permet le partage du code entre toutes les versions de .NET, notamment .NET Core. Avec .NET 2.0 Standard, c’est encore plus facile car la surface de l’API de .NET Core s’étend considérablement et les applications .NET Core peuvent utiliser directement les bibliothèques .NET Framework existantes. Toutefois, cette transition ne sera pas immédiate. Nous vous recommandons donc de vérifier les bibliothèques dont a besoin votre application avant de prendre une décision.

### <a name="a-need-to-use-net-technologies-not-available-for-net-core"></a>Besoin d’utiliser des technologies .NET non disponibles pour .NET Core

Certaines technologies .NET Framework ne sont pas disponibles dans .NET Core. Certaines d’entre elles seront disponibles dans les prochaines versions Release de .NET Core, tandis que d’autres, qui ne s’appliquent pas aux nouveaux modèles d’application ciblés par .NET Core, risquent de ne jamais l’être. La liste suivante présente les technologies les plus courantes absentes dans .NET Core 1.0 :

* Applications Web Forms ASP.NET : Web Forms ASP.NET n’étant disponible que sur .NET Framework, vous ne pouvez pas utiliser ASP.NET Core/.NET Core pour ce scénario. Il n’est pas prévu d’intégrer Web Forms ASP.NET à .NET Core.

* Applications ASP.NET Web Pages : la technologie ASP.NET Web Pages n’est pas incluse dans ASP.NET Core 1.0. Il est cependant prévu de l’inclure dans une prochaine version Release, comme expliqué dans la [feuille de route de .NET Core](https://github.com/aspnet/Home/wiki/Roadmap).

* Implémentation client/serveur SignalR ASP.NET. Le calendrier de la version Release de .NET Core 1.0 (juin 2016) ne prévoit pas la disponibilité de SignalR ASP.NET pour ASP.NET Core (client ou serveur), mais il est prévu de l’inclure dans une prochaine version, comme expliqué dans la [feuille de route .NET Core](https://github.com/aspnet/Home/wiki/Roadmap). L’état en préversion est disponible dans les dépôts GitHub [côté serveur](https://github.com/aspnet/SignalR-Server) et de la [bibliothèque cliente](https://github.com/aspnet/SignalR-Client-Net).

* Implémentation des services WCF. Même s’il existe une [bibliothèque cliente WCF](https://github.com/dotnet/wcf) pour utiliser des services WCF à partir de .NET Core, à compter de juin 2016, l’implémentation serveur WCF est disponible uniquement sur .NET Framework. Ce scénario ne fait pas partie du plan actuel pour .NET Core, mais il est envisagé pour l’avenir.

* Services liés aux flux de travail : Windows Workflow Foundation (WF), les services de flux de travail (WCF + WF dans un seul service) et les services de données WCF (anciennement « ADO.NET Data Services ») sont disponibles uniquement sur .NET Framework et il n’est pas prévu de les intégrer à .NET Core.

* Prise en charge linguistique : Visual Basic et F# ne bénéficient pas des outils dans .NET Core, mais seront pris en charge dans Visual Studio versions 2017 et ultérieures.

En plus de la feuille de route officielle, d’autres frameworks doivent être portés vers .NET Core. Pour obtenir une liste complète, consultez les problèmes CoreFX portant l’étiquette [port-to-core](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core). Veuillez noter que cette liste ne constitue pas un engagement de Microsoft à intégrer ces composants à .NET Core, elle reflète simplement la volonté de la communauté en ce sens. Cela étant dit, si vous vous intéressez à l’un des composants indiqués ci-dessus, pensez à participer aux discussions sur GitHub pour faire entendre votre voix. Et si vous pensez que quelque chose fait défaut, veuillez [enregistrer un nouveau problème dans le dépôt CoreFX](https://github.com/dotnet/corefx/issues/new).

### <a name="a-need-to-use-a-platform-that-doesnt-support-net-core"></a>Besoin d’utiliser une plateforme qui ne prend pas en charge .NET Core

Certaines plateformes Microsoft ou tierces ne prennent pas en charge .NET Core. Par exemple, certains services Azure, tels que Service Fabric Stateful Reliable Services et Service Fabric Reliable Actors, exigent .NET Framework. D’autres services fournissent un SDK qui n’est pas encore utilisable sur .NET Core. Il s’agit d’une circonstance transitoire, car tous les services Azure utilisent .NET Core. En attendant, vous pouvez toujours utiliser l’API REST équivalente au lieu du SDK client.

## <a name="further-resources"></a>Ressources supplémentaires

* [Guide .NET Core](../core/index.md)
* [Portage depuis .NET Framework vers .NET Core](../core/porting/index.md)
* [Guide de .NET Framework sur Docker](../framework/index.md)
* [Vue d’ensemble des composants .NET](components.md)


<!--HONumber=Nov16_HO3-->


