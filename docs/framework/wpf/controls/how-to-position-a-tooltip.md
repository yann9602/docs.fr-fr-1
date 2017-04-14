---
title: "Comment&#160;: positionner une info-bulle | Microsoft Docs"
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
  - "positionner des contrôles ToolTip"
  - "ToolTip (contrôle), positionner"
ms.assetid: cddf3757-9e5f-4ce3-a6eb-44489cf3804a
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: positionner une info-bulle
Cet exemple montre comment spécifier la position d'une info\-bulle sur l'écran.  
  
## Exemple  
 Vous pouvez positionner une info\-bulle à l'aide d'un jeu de cinq propriétés définies dans les classes <xref:System.Windows.Controls.ToolTip> et <xref:System.Windows.Controls.ToolTipService>.  Le tableau suivant montre ces deux jeux de cinq propriétés et fournit des liens vers leur documentation de référence selon la classe.  
  
### Propriétés des info\-bulles correspondantes selon la classe  
  
|Propriétés de classe <xref:System.Windows.Controls.ToolTip?displayProperty=fullName>|Propriétés de classe <xref:System.Windows.Controls.ToolTipService?displayProperty=fullName>|  
|------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=fullName>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=fullName>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=fullName>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=fullName>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=fullName>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=fullName>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=fullName>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=fullName>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=fullName>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=fullName>|  
  
 Si vous définissez le contenu d'une info\-bulle à l'aide d'un objet <xref:System.Windows.Controls.ToolTip>, vous pouvez utiliser les propriétés de l'une ou l'autre des classes ; toutefois, les propriétés <xref:System.Windows.Controls.ToolTipService> sont prioritaires.  Utilisez les propriétés <xref:System.Windows.Controls.ToolTipService> pour les info\-bulles qui ne sont pas définies en tant qu'objets <xref:System.Windows.Controls.ToolTip>.  
  
 Les illustrations suivantes montrent comment positionner une info\-bulle à l'aide de ces propriétés.  Bien que les exemples [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] de ces illustrations montrent comment définir les propriétés définies par la classe <xref:System.Windows.Controls.ToolTip>, les propriétés correspondantes de la classe <xref:System.Windows.Controls.ToolTipService> suivent les mêmes règles de disposition.  Pour plus d'informations sur les valeurs possibles de la propriété Placement, consultez [Comportement de positionnement de Popup](../../../../docs/framework/wpf/controls/popup-placement-behavior.md).  
  
 ![Positionnement de ToolTip](../../../../docs/framework/wpf/controls/media/tooltipplacement.png "ToolTipPlacement")  
Positionnement d'une info\-bulle à l'aide de la propriété Placement  
  
 ![Positionnement d'un ToolTip à l'aide d'un rectangle de positionnement](../../../../docs/framework/wpf/controls/media/tooltipplacementrectangle.png "ToolTipPlacementRectangle")  
Positionnement d'une info\-bulle à l'aide des propriétés Placement et PlacementRectangle  
  
 ![Diagramme de positionnement de ToolTip](../../../../docs/framework/wpf/controls/media/tooltipplacementprhv.png "ToolTipPlacementPRHV")  
Positionnement d'une info\-bulle à l'aide des propriétés Placement, PlacementRectangle et Offset  
  
 L'exemple suivant montre comment utiliser les propriétés <xref:System.Windows.Controls.ToolTip> pour spécifier la position d'une info\-bulle dont le contenu est un objet <xref:System.Windows.Controls.ToolTip>.  
  
 [!code-xml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 L'exemple suivant montre comment utiliser les propriétés <xref:System.Windows.Controls.ToolTipService> pour spécifier la position d'une info\-bulle dont le contenu n'est pas un objet <xref:System.Windows.Controls.ToolTip>.  
  
 [!code-xml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.ToolTip>   
 <xref:System.Windows.Controls.ToolTipService>   
 [Rubriques Comment](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)   
 [Vue d'ensemble de l'info\-bulle](../../../../docs/framework/wpf/controls/tooltip-overview.md)   
 [Use the ContextMenuService and ToolTipService](http://msdn.microsoft.com/fr-fr/809b0e9c-d612-4cda-b8af-1a698c68f4d1)