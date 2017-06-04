---
title: "Planification des performances des applications | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "applications, optimiser"
  - "application WPF, optimiser"
ms.assetid: c91bd0c5-a193-46ff-9da1-eb7a3a76a3b3
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Planification des performances des applications
La réalisation de vos objectifs de performances dépend de la manière dont vous avez élaboré votre stratégie en la matière.  La planification est la première étape du développement de tout produit.  Cette rubrique décrit quelques règles simples qui vous permettront d'élaborer une bonne stratégie de performances.  
  
## Pensez en termes de scénarios  
 Les scénarios vous aident à vous concentrer sur les composants essentiels de votre application.  Les scénarios sont généralement inspirés par vos clients ou par des produits concurrents.  Étudiez vos clients et cherchez à découvrir ce qui les a réellement attirés dans votre produit, et dans ceux de la concurrence.  Les informations fournies par vos clients peuvent vous aider à déterminer le scénario principal de votre application.  Par exemple, si vous concevez un composant qui sera utilisé au démarrage, il ne sera probablement appelé qu'une seule fois, au démarrage de l'application.  Le moment du démarrage devient alors votre scénario clé.  La fréquence d'images des séquences d'animation, ou le jeu de travail maximal autorisé pour l'application sont d'autres exemples de scénarios clé.  
  
## Définissez des objectifs  
 Les objectifs vous permettent de déterminer si une application s'exécute plus ou moins rapidement.  Vous devez définir des objectifs pour tous les scénarios.  Tous les objectifs de performances que vous définissez doivent être fonction des attentes de vos clients.  Il est parfois difficile de définir des objectifs de performances au début du cycle de développement, lorsqu'il reste encore de nombreux problèmes non résolus.  Cependant, il vaut mieux définir un objectif initial et le réviser ensuite que ne pas avoir d'objectif du tout.  
  
## Maîtrisez votre plateforme  
 Répétez toujours le cycle mesure, investigation et ajustement\/correction pendant toute la durée du développement de votre application.  Du début à la fin du cycle de développement, vous devez mesurer les performances de l'application dans un environnement fiable et stable.  Évitez les variations provoquées par des facteurs externes.  Par exemple, lorsque vous faites des tests de performances, il est recommandé de désactiver l'anti\-virus ou toute mise à jour automatique comme SMS, afin de ne pas influencer les résultats des tests.  Une fois les performances de votre application mesurées, vous devez identifier les modifications qui permettront d'apporter les améliorations les plus importantes.  Faites ces modifications, puis recommencez le cycle.  
  
## Le réglage des performances doit être un processus itératif  
 Vous devez connaître le coût relatif de chaque fonctionnalité que vous utilisez.  Par exemple, l'utilisation de la réflexion dans [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] est généralement très gourmande en ressources de traitement et vous devez y recourir judicieusement.  Cela ne signifie pas que vous devez éviter d'utiliser la réflexion, mais que vous devez trouver l'équilibre entre les spécifications de performances de votre application et les exigences en termes de performances des fonctionnalités que vous utilisez.  
  
## Recherche progressive de la richesse graphique  
 Pour aboutir à une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] performante en adoptant une approche évolutive, l'idéal est d'aller progressivement vers la richesse graphique et la complexité.  Commencez toujours par utiliser les ressources les moins gourmandes en performances pour atteindre les objectifs de vous scénarios.  Une fois ces objectifs atteints, recherchez la richesse graphique en utilisant des fonctionnalités plus exigeantes en termes de performances, sans jamais perdre vos objectifs de vue.  Rappelez\-vous que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est une plateforme très riche qui propose de puissantes fonctionnalités graphiques.  L'utilisation inconsidérée de fonctionnalités exigeantes peut avoir un impact négatif sur les performances globales de votre application.  
  
 Les contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont extensibles par nature puisqu'ils autorisent une personnalisation poussée de leur apparence sans modification de leur comportement de contrôle.  En tirant parti des styles, des modèles de données et des modèles de contrôles, vous pouvez créer et faire évoluer une [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] personnalisable qui s'adapte à vos spécifications de performances.  
  
## Voir aussi  
 [Optimisation des performances des applications WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)   
 [Tirer parti du matériel](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)   
 [Disposition et conception](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)   
 [Graphiques 2D et acquisition d'images](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [Comportement d'objets](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)   
 [Ressources d'application](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)   
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)   
 [Liaison de données](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [Autres recommandations relatives aux performances](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)