---
title: Planification des performances des applications
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: c91bd0c5-a193-46ff-9da1-eb7a3a76a3b3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6bdb140d90de02fa817c55a05f40e57fcd0d636c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="planning-for-application-performance"></a>Planification des performances des applications
La réussite d’atteindre vos objectifs de performances dépend du degré de l’élaboration de votre stratégie de performances. La planification est la première étape du développement d’un produit. Cette rubrique décrit quelques règles simples pour le développement d’une stratégie de bonnes performances.  
  
## <a name="think-in-terms-of-scenarios"></a>Pensez en termes de scénarios  
 Scénarios peuvent vous aider à vous concentrer sur les composants essentiels de votre application. Les scénarios sont généralement dérivées de vos clients, ainsi que les produits concurrents. Toujours étudiez vos clients et découvrez vraiment pourquoi les heureux sur votre produit et les produits de vos concurrents. Les commentaires de vos clients peuvent vous aider à déterminer le scénario principal de votre application. Par exemple, si vous concevez un composant qui sera utilisé au démarrage, il est probable que le composant sera appelé une seule fois, au démarrage de l’application. Temps de démarrage devient votre scénario clé. Autres exemples de scénarios clés peut être la fréquence d’images pour les séquences d’animation, ou la valeur maximale autorisée pour l’application de jeu de travail.  
  
## <a name="define-goals"></a>Définir des objectifs  
 Objectifs de vous aident à déterminer si une application s’exécute plus rapidement ou plus lentement. Vous devez définir des objectifs de tous les scénarios. Tous les objectifs de performances que vous définissez doivent être basées sur les attentes de vos clients. Il peut être difficile de cycle des objectifs très tôt dans le développement d’applications, lorsque de nombreux problèmes non résolus sont toujours les performances. Toutefois, il est préférable de définir un objectif initial et le réviser plus tard ne pas avoir d’objectif du tout.  
  
## <a name="understand-your-platform"></a>Comprendre votre plateforme  
 Toujours conserver le cycle de mesure, investigation et ajustement/correction pendant votre cycle de développement d’applications. À partir du début à la fin du cycle de développement, vous devez mesurer les performances de votre application dans un environnement fiable et stable. Vous devez éviter les variations provoquées par des facteurs externes. Par exemple, lorsque vous testez les performances, vous devez désactiver un antivirus ou une mise à jour automatique, telles que SMS, pour ne pas affecter les performances des résultats de tests. Une fois que vous avez mesuré les performances de votre application, vous devez identifier les modifications qui seront traduiront améliorations les plus importantes. Une fois que vous avez modifié votre application, démarrez le cycle.  
  
## <a name="make-performance-tuning-an-iterative-process"></a>Un processus itératif de réglage des performances  
 Vous devez connaître le coût relatif de chaque fonctionnalité que vous utilisez. Par exemple, l’utilisation de la réflexion dans [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] est généralement très gourmande en termes de ressources informatiques, vous pouvez utiliser judicieusement. Cela ne signifie pas éviter l’utilisation de la réflexion, uniquement que vous devez être prudent à équilibrer les besoins de performances de votre application avec les exigences de performance de fonctionnalités que vous utilisez.  
  
## <a name="build-towards-graphical-richness"></a>La richesse graphique  
 Une technique de clé pour la création d’une approche évolutive vers la réalisation des [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] des performances des applications consiste à générer richesse graphique et la complexité. Commencez toujours par utiliser les ressources les moins gourmandes en performances pour atteindre vos objectifs de scénario. Une fois que vous atteindre ces objectifs, richesse graphique à l’aide de plus de fonctionnalités exigeantes, toujours vos objectifs en n’oubliant pas. N’oubliez pas, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est une plateforme très riche et propose de puissantes fonctionnalités de graphique. À l’aide de fonctionnalités exigeantes sans prendre en considération peut avoir un impact négatif sur les performances de votre application globale.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]les contrôles sont par nature extensibles en permettant la personnalisation de la poussée de leur apparence sans modification de leur comportement de contrôle. En tirant parti des styles, les modèles de données et les modèles de contrôle, vous pouvez créer et évoluer une personnalisable [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] qui s’adapte à vos besoins.  
  
## <a name="see-also"></a>Voir aussi  
 [Optimisation des performances des applications WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Tirer parti du matériel](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Disposition et conception](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [Graphiques 2D et acquisition d'images](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Comportement de l’objet](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Ressources d'application](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Liaison de données](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Autres recommandations relatives aux performances](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
