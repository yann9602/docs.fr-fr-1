---
title: "Optimisation des performances : ressources d'application"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application resources [WPF], performance
- resources [WPF], performance
- static resources [WPF]
- sharing resources [WPF]
- brushes [WPF], performance
- sharing brushes without copying [WPF]
ms.assetid: 62b88488-c08e-4804-b7de-a1c34fbe929c
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c0a7c9920b321f15f3f01a64fbfc80693042a025
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="optimizing-performance-application-resources"></a>Optimisation des performances : ressources d'application
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]vous permet de partager des ressources d’application afin que vous pouvez prendre en charge une apparence cohérente ou un comportement sur les éléments de type semblables. Cette rubrique fournit quelques recommandations dans ce domaine qui peuvent vous aider à améliorent les performances de vos applications.  
  
 Pour plus d’informations sur les ressources, consultez la page [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
## <a name="sharing-resources"></a>Partage de ressources  
 Si votre application utilise des contrôles personnalisés et définit des ressources dans un <xref:System.Windows.ResourceDictionary> (ou nœud de ressources XAML), il est recommandé que vous définissiez les ressources situées sur le <xref:System.Windows.Application> ou <xref:System.Windows.Window> au niveau de l’objet, ou les définir dans le thème par défaut pour le contrôles personnalisés. Définition des ressources dans un contrôle personnalisé <xref:System.Windows.ResourceDictionary> impose un impact sur les performances pour chaque instance de ce contrôle. Par exemple, si vous avez les opérations exigeantes en performances pinceau définies dans le cadre de la définition de ressource d’un contrôle personnalisé et de nombreuses instances du contrôle personnalisé, plage de travail de l’application augmente considérablement.  
  
 Pour illustrer ce point, considérez les points suivants. Supposons que vous développez un jeu de carte à l’aide [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Pour la plupart des jeux de cartes, vous devez 52 cartes avec 52 faces différentes. Vous décidez d’implémenter un contrôle personnalisé de carte et que vous définissez 52 pinceaux (chacun représentant une face de carte) dans les ressources de votre carte de contrôle personnalisé. Dans votre application principale, vous créez initialement 52 instances de cette carte de contrôle personnalisé. Chaque instance de la carte de contrôle personnalisé génère 52 instances de <xref:System.Windows.Media.Brush> objets, ce qui vous donne un total de 52 * 52 <xref:System.Windows.Media.Brush> objets dans votre application. En déplaçant les pinceaux hors des ressources de contrôle personnalisé de carte à la <xref:System.Windows.Application> ou <xref:System.Windows.Window> niveau de l’objet, ou en les définissant dans le thème par défaut pour le contrôle personnalisé, vous réduisez la plage de travail de l’application, puisque vous partagez maintenant les 52 pinceaux parmi 52 d’instances de la carte de contrôle.  
  
## <a name="sharing-a-brush-without-copying"></a>Partage d’un pinceau sans copier  
 Si vous avez plusieurs éléments à l’aide de la même <xref:System.Windows.Media.Brush> de l’objet, définissez le pinceau comme une ressource et référencez-le, plutôt que de définir le pinceau inline dans [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]. Cette méthode crée une instance et la réutiliser, tandis que la définition de pinceaux inline dans [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] crée une nouvelle instance pour chaque élément.  
  
 Le balisage suivant illustre ce point :  
  
 [!code-xaml[Performance#PerformanceSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/BrushResource.xaml#performancesnippet7)]  
  
## <a name="use-static-resources-when-possible"></a>Utilisez les ressources statiques lorsque cela est Possible  
 Une ressource statique fournit une valeur pour tout attribut de propriété XAML en recherchant une référence à une ressource déjà définie. Comportement de recherche de cette ressource est analogue à la recherche au moment de la compilation.  
  
 Une ressource dynamique, quant à lui, est une expression temporaire pendant la compilation initiale et donc déférer recherche des ressources jusqu'à ce que la valeur de la ressource demandée est réellement nécessaire afin de construire un objet. Comportement de recherche de cette ressource est analogue à la recherche au moment de l’exécution, qui impose un impact sur les performances. Utilisez les ressources statiques autant que possible dans votre application, à l’aide de ressources dynamiques uniquement lorsque cela est nécessaire.  
  
 L’exemple de balise suivant illustre l’utilisation de ces deux types de ressources :  
  
 [!code-xaml[Performance#PerformanceSnippet8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/DynamicResource.xaml#performancesnippet8)]  
  
## <a name="see-also"></a>Voir aussi  
 [Optimisation des performances des applications WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Planification des performances des applications](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Tirer parti du matériel](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Disposition et conception](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [Graphiques 2D et acquisition d'images](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Comportement de l’objet](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Liaison de données](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Autres recommandations relatives aux performances](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
