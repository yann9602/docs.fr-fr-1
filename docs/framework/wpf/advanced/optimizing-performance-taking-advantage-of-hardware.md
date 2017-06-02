---
title: "Optimisation des performances&#160;: tirer parti du mat&#233;riel | Microsoft Docs"
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
  - "couches de rendu graphiques"
  - "graphiques, performances"
  - "graphiques, couches de rendu"
  - "rendu matériel (pipeline)"
  - "couches de rendu"
  - "rendu logiciel (pipeline)"
ms.assetid: bfb89bae-7aab-4cac-a26c-a956eda8fce2
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Optimisation des performances&#160;: tirer parti du mat&#233;riel
L'architecture interne de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] comprend deux pipelines de rendu, un matériel et un logiciel.  Cette rubrique fournit des informations sur ces pipelines de rendu pour vous aider à prendre des décisions sur l'optimisation des performances de vos applications.  
  
## Pipeline de rendu matériel  
 L'un des principaux facteurs à prendre en compte lors de la détermination des performances de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est l'impact du rendu : plus le nombre de pixels à rendre est élevé, plus le coût des performances est élevé.  Cependant, plus vous pourrez délester le rendu sur [!INCLUDE[TLA#tla_gpu](../../../../includes/tlasharptla-gpu-md.md)], plus les gains en termes de performances seront élevés.  Le pipeline de rendu matériel d'une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tire entièrement parti des fonctionnalités [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] sur un matériel qui prend en charge [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] version 7.0 au minimum.  Les gains d'optimisation peuvent être encore supérieurs sur un matériel prenant en charge [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] version 7.0 et les fonctionnalités PixelShader 2.0\+.  
  
## Pipeline de rendu logiciel  
 Le pipeline de rendu logiciel de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est entièrement lié au processeur.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tire parti des jeux d'instructions SSE et SSE2 du processeur pour implémenter un rastériseur logiciel complet et optimisé.  Le recours au logiciel est transparent chaque fois qu'une fonctionnalité de l'application ne peut être rendue à l'aide du pipeline de rendu matériel.  
  
 Le principal problème de performances que vous pouvez rencontrer en termes de rendu en mode logiciel est lié au taux de remplissage, à savoir le nombre de pixels rendus.  Si vous avez des soucis de performance en mode de rendu logiciel, essayez de minimiser le nombre de fois où un pixel est redessiné.  Par exemple, si vous avez une application avec un fond bleu avec un rendu d'image légèrement transparente sur le dessus, vous rendrez deux fois la totalité des pixels dans l'application.  Par conséquent, le rendu de l'application avec l'image demandera deux fois plus de temps que si vous aviez uniquement le fond bleu.  
  
### Couches de rendu graphiques  
 Il est parfois très difficile de prévoir sur quelle configuration sera exécutée votre application.  Cependant, vous souhaiterez peut\-être concevoir votre application de manière qu'elle puisse basculer les fonctionnalités de manière transparente en cas d'exécution sur un matériel différent, afin de tirer pleinement parti de chaque configuration matérielle.  
  
 Pour ce faire, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit une fonctionnalité permettant de déterminer la capacité graphique d'un système au moment de l'exécution.  La détermination de la capacité graphique se fait en fonction de la catégorie de la carte vidéo qui est l'une des trois couches de rendu.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] expose une [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] qui permet à une application de demander la couche de capacité de rendu.  Votre application peut alors prendre des chemins de code différents au moment de l'exécution selon la couche de rendu prise en charge par le matériel.  
  
 Les fonctionnalités du matériel graphique qui impactent le plus les niveaux de la couche de rendu sont les suivantes :  
  
-   **RAM vidéo** La quantité de mémoire vidéo sur le matériel graphique détermine la taille et le nombre de mémoires tampon qui peuvent être utilisées pour la composition de graphiques.  
  
-   **Nuanceur de pixels** Un nuanceur de pixels est une fonction de traitement des graphiques qui calcule les effets pixel par pixel.  En fonction de la résolution des graphiques affichés, il peut y avoir plusieurs millions de pixels à traiter pour chaque frame d'affichage.  
  
-   **Vertex shader** Un vertex shader est une fonction de traitement des graphiques qui effectue des opérations mathématiques sur les données de vertex de l'objet.  
  
-   **Prise en charge de la multitexture** La prise en charge de la multitexture fait référence à la possibilité d'appliquer au moins deux textures distinctes pendant une opération de mélange sur un objet graphique 3D.  Le degré de prise en charge de la multitexture est déterminé par le nombre d'unités de multitexture sur le matériel graphique.  
  
 Le nuanceur de pixels, le vertex shader et les fonctionnalités de multitexture sont utilisés pour définir des niveaux de version [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] spécifiques qui, à leur tour, servent à définir les différentes couches de rendu dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Les fonctionnalités du matériel graphique déterminent la fonction de rendu d'une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Le système [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] définit trois couches de rendu :  
  
-   **Couche de rendu 0** Aucune accélération du matériel graphique.  Le niveau de version [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] est inférieur à la version 7.0.  
  
-   **Couche de rendu 1** Accélération partielle du matériel graphique.  Le niveau de version [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] est supérieur ou égal à la version 7.0, et **inférieur** à la version 9.0.  
  
-   **Couche de rendu 2** La plupart des caractéristiques graphiques utilisent l'accélération du matériel graphique.  Le niveau de version [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] est supérieur ou égal à la version 9.0.  
  
 Pour plus d'informations sur les couches de rendu de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [Couches de rendu graphiques](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md).  
  
## Voir aussi  
 [Optimisation des performances des applications WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)   
 [Planification des performances des applications](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)   
 [Disposition et conception](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)   
 [Graphiques 2D et acquisition d'images](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [Comportement d'objets](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)   
 [Ressources d'application](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)   
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)   
 [Liaison de données](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [Autres recommandations relatives aux performances](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)