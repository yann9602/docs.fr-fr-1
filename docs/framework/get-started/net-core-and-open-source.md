---
title: ".NET Core et Open-Source | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 6
---
# .NET Core et Open-Source
Le .NET Core est une version modulaire du .NET Framework portable sur plusieurs plateformes pour optimiser le partage et la réutilisation du code. En outre, le .NET Core est open source et accepte les contributions de la Communauté. Cette rubrique répond aux questions courantes sur le .NET Core. En outre, elle indique comment accéder et contribuer aux packages open source.  
  
<a name="BKMK_WhatisNETCore"></a>   
## Qu'est\-ce que le .NET Core ?  
 Comme indiqué précédemment, le .NET Core est une version modulaire du .NET Framework portable sur plusieurs plateformes.  
  
 Le .NET Core est portable sur plusieurs plateformes, car, bien qu'il s'agisse d'un sous\-ensemble du .NET Framework, il fournit des fonctionnalités clés pour implémenter les fonctionnalités d'application dont vous avez besoin, et pour réutiliser ce code quelle que soit la cible de votre plateforme. Dans le passé, les différentes versions de .NET pour les différentes plateformes n'offraient pas de fonctionnalités partagées pour les tâches clés telles que la lecture des fichiers locaux. Les plateformes Microsoft que vous pouvez cibler avec le .NET Core incluent les versions classiques de Windows, ainsi que les versions de Windows pour appareils et téléphones. Quand des outils tiers tels que Xamarin sont utilisés, le .NET Core doit pouvoir être porté sur les appareils IOS et Android. En outre, le .NET Core sera bientôt disponible pour les systèmes d'exploitation Mac et Linux, ce qui permettra d'exécuter des applications web sur ces systèmes.  
  
 Le .NET Core est modulaire, car il est publié via NuGet dans des packages d'assembly de taille réduite. Au lieu d'un assembly volumineux contenant la plupart des fonctionnalités principales, le .NET Core est disponible sous forme de petits packages axés sur les fonctionnalités. Cela nous permet de disposer d'un modèle de développement plus agile, et cela vous permet de choisir les fonctionnalités précises dont vous avez besoin pour vos applications et bibliothèques. Pour plus d’informations sur les packages .NET publiés sur NuGet, consultez [Versions finales hors plage de .NET Framework](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md).  
  
 Voici certaines questions fréquentes relatives au .NET Core.  
  
### Comment tirer le meilleur parti du .NET Core ?  
 Pour les applications existantes, l'utilisation de bibliothèques de classes portables \(PCL\), l'utilisation de projets d'application universelle et la séparation de la logique métier du code spécifique à la plateforme sont la meilleure façon de tirer parti du .NET Core, et d'optimiser la réutilisation du code. Pour les applications, les modèles MVC \(Model\-View\-Controller\) ou MVVM \(Model View\-ViewModel\) sont de bons choix pour faciliter la migration de vos applications vers le .NET Core.  
  
### Comment le .NET Core affecte\-t\-il la compatibilité et le déploiement ?  
 Il existe différents scénarios en matière de déploiement, mais ce dernier reste facile à mener. Le .NET Framework est distribué avec Windows et mis à jour via Microsoft Update, comme c'est le cas actuellement. Dans certains cas, votre application dépend de ce déploiement sur disque du .NET Framework. Dans d'autres cas, votre application dépend des assemblys .NET déployés avec le package d'application. En outre, la compatibilité entre les versions est toujours une priorité pour le .NET Framework. Ainsi, si votre application s'exécute sur une version plus récente d'un assembly à partir duquel elle a été compilée, son comportement doit rester le même.  
  
|Scénario|Déploiement|  
|--------------|-----------------|  
|Applications de bureau Windows et applications ASP.NET qui s'exécutent sur des ordinateurs Windows|Le déploiement est le même qu'actuellement. Une application s'appuie sur l'installation du .NET Framework sur le serveur ou sur l'ordinateur de l'utilisateur. Si le .NET Framework n'est pas installé, l'utilisateur sera invité à l'installer. Vous pouvez également chaîner une installation .NET avec l'application. Quand vous utilisez des assemblys du .NET Core qui ne sont pas inclus dans le .NET Framework, ces assemblys sont inclus dans le package d'application. En outre, si deux versions du même assembly sont référencées par la même application, cette dernière effectue une redirection vers l'assembly le plus récent. Pour plus d'informations, consultez [Redirection des versions d’assemblys au niveau de l’application](../../../docs/framework/configure-apps/redirect-assembly-versions.md#BKMK_Redirectingassemblyversionsattheapplevel) et [Comment : activer et désactiver la redirection de liaison automatique](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md).<br /><br /> Pour plus d’informations sur le déploiement de .NET, consultez le [Guide de déploiement pour les développeurs](../../../docs/framework/deployment/deployment-guide-for-developers.md).|  
|Applications Windows et Windows Phone disponibles via le Windows Store et le Windows Phone Store|Le déploiement est le même qu'actuellement. Par ailleurs, les applications utilisent les assemblys du .NET Framework inclus dans le système d'exploitation. Si votre application utilise une fonctionnalité publiée dans un assembly du .NET Core mais qui est absente du .NET Framework, l'assembly est inclus dans le package d'application. Si plusieurs versions du même assembly sont référencées par l'application, ces applications utilisent automatiquement la version la plus récente de l'assembly.|  
|Applications ASP.NET Core 5.0|Les assemblys .NET Core sont app\-local, ce qui signifie que les assemblys nécessaires sont déployés avec le package d'application. Pour plus d’informations sur ASP.NET Core 5.0, consultez [Vue d’ensemble d’ASP.NET 5](http://www.asp.net/vnext/overview/aspnet-vnext/aspnet-5-overview).|  
|Applications générées avec des outils Xamarin qui s'exécutent sur d'autres plateformes|Actuellement, ces applications sont déployées avec un ensemble simplifié d'assemblys Mono livrés avec le package d'application. Cela risque de changer, car davantage d'assemblys .NET Core sont open source.|  
  
<a name="BKMK_NETCoreOpenSourcePackages"></a>   
## Packages .NET Core open source  
 Outre la modularisation du .NET Framework, Microsoft fournit en open source les packages .NET Core sur [GitHub](https://github.com/), sous licence du [MIT](https://github.com/dotnet/corefx/blob/master/LICENSE). Cela signifie que vous pouvez cloner le référentiel Git, lire et compiler le code, et soumettre des requêtes d'extraction comme pour tout autre package open source sur GitHub. En raison de notre engagement en matière de qualité et de compatibilité, chaque requête d'extraction est soigneusement évaluée avant d'être acceptée. Voici certaines questions récurrentes.  
  
### Comment obtenir le code et le générer ?  
 Les packages sources du .NET Core sont stockés sur `GitHub`, qui utilise `Git` comme système de contrôle de code source. Pour accéder au code et le générer, vous devez avoir certaines notions de base concernant [Git](http://git-scm.com/), [GitHub](https://github.com/dotnet/corefx) et [Visual Studio](http://msdn.microsoft.com/vstudio/aa718325.aspx). Toutefois, les étapes suivantes fournissent des informations et des liens pour vous aider à démarrer.  
  
 Pour configurer Git et GitHub, consultez [Configurer Git](https://help.github.com/articles/set-up-git/) sur le site GitHub.  
  
 Pour accéder au code du .NET Framework, vous devez créer un branchement au niveau du référentiel Git qui le contient, puis le cloner sur votre ordinateur de développement. Vous pouvez créer un branchement au niveau du code en accédant au référentiel, puis en cliquant sur **Branchement** dans le coin supérieur droit de votre navigateur. Vous pouvez cloner le branchement à l'aide de l'application GitHub ou sur la ligne de commande du shell GitHub. Pour cloner le référentiel dans le shell GitHub, exécutez la commande suivante :  
  
```  
git clone https://github.com/dotnet/corefx  
```  
  
 Pour générer le code, vous devez disposer d'une installation de Visual Studio 2013. Vous pouvez soit ouvrir et générer les solutions avec Visual Studio 2013, en appuyant sur F5, soit générer les solutions sur la ligne de commande à l'aide de l'invite de commandes développeur. Pour générer l'invite de commandes, ouvrez une invite de commandes développeur, puis accédez au dossier où vous avez cloné le code source. Tapez ensuite :  
  
```  
build.cmd  
  
```  
  
 Pour plus d’informations sur la façon d’accéder à l’invite de commandes développeur, consultez [Invites de commandes](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
### Quelles sont les recommandations pour la soumission de code ?  
 Pour que nous puissions intégrer votre travail dans la branche principale, vous devez signer un [contrat de licence de collaborateur \(CLA\)](https://cla.dotnetfoundation.org/).  
  
 Nous acceptons les contributions de la communauté via le modèle de branchement et d'extraction. Vous devez effectuer un branchement et un clonage du code, puis soumettre une requête d'extraction à la branche principale du .NET Framework. Pour plus d’informations sur les requêtes d’extraction, consultez [Utilisation de requêtes d’extraction](https://help.github.com/articles/using-pull-requests/). Pour obtenir des instructions détaillées sur la soumission d’une requête d’extraction, consultez le [Guide de contribution au .NET Core](https://github.com/dotnet/corefx/wiki/Contributing).  
  
### Pourquoi n'avez\-vous pas accepté ma requête d'extraction ?  
 Si nous refusons votre requête, nous vous en donnons la raison. Toutefois, sachez qu'en général, Microsoft s'engage à respecter la qualité et la compatibilité du code. Si votre requête d'extraction n'a pas été acceptée, cela est peut\-être dû au fait que vous n'avez pas respecté nos recommandations de codage, que les tests relatifs à la soumission de votre code sont insuffisants, ou que vous avez provoqué une incompatibilité d'API. En outre, vos modifications du code doivent être en phase avec notre feuille de route pour le .NET Framework. Pour consulter les recommandations en matière de codage et plus d’informations, reportez\-vous au [Guide de contribution au .NET Core](https://github.com/dotnet/corefx/wiki/Contributing).  
  
## Voir aussi  
 [.NET est disponible en open source](http://blogs.msdn.com/b/dotnet/archive/2014/11/12/net-core-is-open-source.aspx)   
 [.NET Open Source Curah](https://curah.microsoft.com/254870/net-core-open-source)   
 [Vue d’ensemble d’ASP.NET 5](http://www.asp.net/vnext/overview/aspnet-vnext/aspnet-5-overview)