---
title: "Optimisation des performances : tirer parti du matériel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [WPF], performance
- hardware rendering pipeline [WPF]
- rendering tiers [WPF]
- graphics rendering tiers [WPF]
- graphics [WPF], rendering tiers
- software rendering pipeline [WPF]
ms.assetid: bfb89bae-7aab-4cac-a26c-a956eda8fce2
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 55c9482ecb540baab3ddd57ca9350fd7265ac251
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="optimizing-performance-taking-advantage-of-hardware"></a>Optimisation des performances : tirer parti du matériel
L’architecture interne de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a deux pipelines de rendu matériel et logiciel. Cette rubrique fournit des informations sur ces pipelines de rendu pour vous aider à prendre des décisions concernant l’optimisation des performances de vos applications.  
  
## <a name="hardware-rendering-pipeline"></a>Pipeline de rendu matériel  
 Un des facteurs plus importants dans la détermination [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] performances sont sa limite de rendu, les plus de pixels à rendre, plus le coût de performance. Toutefois, les plus de rendu qui peuvent être déchargées sur le [!INCLUDE[TLA#tla_gpu](../../../../includes/tlasharptla-gpu-md.md)], les gains de performance plus, vous pouvez accéder. Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pipeline de rendu matériel application tire pleinement parti de [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] fonctionnalités sur du matériel qui prend en charge un minimum de [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] version 7.0. Les optimisations supplémentaires peuvent être obtenues par le matériel qui prend en charge [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] version 7.0 et les fonctionnalités PixelShader 2.0 +.  
  
## <a name="software-rendering-pipeline"></a>Pipeline de rendu logiciel  
 Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pipeline de rendu logiciel est entièrement liée à l’UC. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tire parti de l’instruction SSE et SSE2 définit dans l’UC pour implémenter un rastériseur logiciel complet optimisé. Le recours au logiciel est transparent chaque fois que fonctionnalité de l’application ne peut pas être restituée à l’aide du pipeline de rendu matériel.  
  
 Le plus gros problème de performances vous rencontrerez lors de rendu en mode logiciel est lié au taux de remplissage, qui est défini comme le nombre de pixels rendus. Si vous êtes inquiet de la performance en mode de rendu logiciel, essayez de réduire le nombre de fois où qu'un pixel est redessiné. Par exemple, si vous avez une application avec un arrière-plan bleu, rendu d’une image légèrement transparente sur celui-ci, vous rendra tous les pixels dans l’application à deux reprises. Par conséquent, il prendra deux fois plus de temps pour le rendu de l’application avec l’image que si vous aviez uniquement l’arrière-plan est bleu.  
  
### <a name="graphics-rendering-tiers"></a>Couches de rendu graphiques  
 Il peut être très difficile à prédire la configuration matérielle qui fonctionnent sur votre application. Toutefois, vous souhaiterez peut-être envisagez une conception qui permet à votre application basculer en toute transparence fonctionnalités lors de l’exécution sur un matériel différent, afin qu’elle puisse tirer pleinement parti de chaque configuration matérielle.  
  
 Pour ce faire, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit les fonctionnalités permettant de déterminer la capacité graphique d’un système lors de l’exécution. Fonctionnalité graphique est déterminée par le classement de la carte vidéo en tant qu’un des trois couches de rendu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]expose un [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] qui permet à une application de demander la couche de capacité de rendu. Votre application peut alors prendre différents chemins de code au moment de l’exécution en fonction de la couche de rendu pris en charge par le matériel.  
  
 Les fonctionnalités du matériel graphique qui ont le plus d’impact sur les niveaux de la couche de rendu sont les suivantes :  
  
-   **RAM vidéo** La quantité de mémoire vidéo sur le matériel graphique détermine la taille et le nombre de mémoires tampon qui peuvent être utilisées pour la composition de graphiques.  
  
-   **Nuanceur de pixels** Un nuanceur de pixels est une fonction de traitement des graphiques qui calcule les effets pixel par pixel. En fonction de la résolution des graphiques affichés, il peut y avoir plusieurs millions de pixels à traiter pour chaque image de l’affichage.  
  
-   **Nuanceur de sommets** Un nuanceur de sommets est une fonction de traitement des graphiques qui effectue des opérations mathématiques sur les données de sommet de l’objet.  
  
-   **Prise en charge de la multitexture** La prise en charge de la multitexture fait référence à la possibilité d’appliquer au moins deux textures distinctes pendant une opération de mélange sur un objet graphique 3D. Le degré de prise en charge de la multitexture est déterminé par le nombre d’unités de multitexture sur le matériel graphique.  
  
 Le nuanceur de pixels, nuanceur de sommets et fonctionnalités de multitexture servent à définir spécifique [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] les niveaux de version, qui, à son tour, sont utilisés pour définir les différentes couches de rendu dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Les fonctionnalités du matériel graphique déterminent la fonction de rendu d’une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Le système [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] définit trois couches de rendu :  
  
-   **Couche de rendu 0** Aucune accélération matérielle graphique. Le [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] niveau de version est inférieure à la version 7.0.  
  
-   **Rendu de niveau 1** l’accélération matérielle graphique partielle. Le [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] niveau de version est supérieure ou égale à la version 7.0, et **moindre** à la version 9.0.  
  
-   **Couche de rendu 2** La plupart des fonctionnalités graphiques utilisent l’accélération matérielle graphique. Le niveau de version [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] est supérieur ou égal à la version 9.0.  
  
 Pour plus d’informations sur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] couches de rendu, consultez [couches de rendu graphiques](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Optimisation des performances des applications WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Planification des performances des applications](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Disposition et conception](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [Graphiques 2D et acquisition d'images](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Comportement de l’objet](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Ressources d'application](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Liaison de données](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Autres recommandations relatives aux performances](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
