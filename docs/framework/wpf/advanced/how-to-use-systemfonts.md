---
title: Guide pratique pour utiliser des SystemFonts
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- system fonts [WPF]
- fonts [WPF], system fonts
- classes [WPF], SystemFonts
ms.assetid: 3f46a4ec-2225-408a-8123-8838a8f7057a
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8ce82724a4e9a547b8441628f43621f29eab6307
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-systemfonts"></a>Guide pratique pour utiliser des SystemFonts
Cet exemple montre comment utiliser les ressources statiques de la <xref:System.Windows.SystemFonts> classe afin d’appliquer un style ou personnaliser un bouton.  
  
## <a name="example"></a>Exemple  
 Les ressources système exposent plusieurs valeurs déterminées par le système en tant que ressources et propriétés pour vous aider à créer des visuels cohérents avec les paramètres système. <xref:System.Windows.SystemFonts>est une classe qui contient les deux valeurs de police système en tant que propriétés statiques et les propriétés qui référencent des clés de ressource qui peuvent être utilisés pour accéder à ces valeurs dynamiquement au moment de l’exécution. Par exemple, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> est un <xref:System.Windows.SystemFonts> valeur, et <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> est une clé de ressource correspondante.  
  
 Dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous pouvez utiliser les membres de <xref:System.Windows.SystemFonts> en tant que propriétés statiques ou références de ressources dynamiques (avec la valeur de propriété statique en tant que la clé). Utilisez une référence de ressource dynamique si vous souhaitez que les métriques de police soient mises à jour automatiquement pendant que l’application s’exécute ; sinon, utilisez une référence de valeur statique.  
  
> [!NOTE]
>  Les clés de ressources ont le suffixe « Key » ajouté au nom de propriété.  
  
 L’exemple suivant montre comment accéder à et utiliser les propriétés de <xref:System.Windows.SystemFonts> en tant que valeurs statiques afin d’appliquer un style ou personnaliser un bouton. Cet exemple de balisage assigne <xref:System.Windows.SystemFonts> valeurs à un bouton.  
  
 [!code-xaml[SystemRes_snip#FontStaticResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 Pour utiliser les valeurs de <xref:System.Windows.SystemFonts> dans le code, vous n’avez pas à utiliser une valeur statique ou une référence de ressource dynamique. Au lieu de cela, utilisez les propriétés non clé de la <xref:System.Windows.SystemFonts> classe. Bien que les propriétés non clé soient apparemment définies en tant que propriétés statiques, le comportement au moment de l’exécution de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hébergé par le système réévaluera les propriétés en temps réel et tiendra compte des modifications apportées utilisateur aux valeurs système. L’exemple suivant montre comment spécifier les paramètres de police d’un bouton.  
  
 [!code-csharp[SystemRes_snip#FontResourcesCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#fontresourcescode)]
 [!code-vb[SystemRes_snip#FontResourcesCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#fontresourcescode)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.SystemFonts>  
 [Peindre une zone avec un pinceau système](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [Utiliser SystemParameters](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)  
 [Utiliser des clés de polices système](../../../../docs/framework/wpf/advanced/how-to-use-system-fonts-keys.md)  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)  
 [x:Static, extension de balisage](../../../../docs/framework/xaml-services/x-static-markup-extension.md)  
 [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Extension de balisage DynamicResource](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)
