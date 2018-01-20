---
title: Vue d'ensemble de l'info-bulle
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
- ToolTip control [WPF], about ToolTip control
- controls [WPF], ToolTip
ms.assetid: f06c1603-e9cb-4809-8a62-234607fc52f7
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7c945d23def3bbf6284e7e0db95d391066256df6
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="tooltip-overview"></a>Vue d'ensemble de l'info-bulle
Une info-bulle est une petite fenêtre contextuelle qui apparaît lorsqu’un utilisateur place le pointeur de la souris au-dessus d’un élément, tel qu’un <xref:System.Windows.Controls.Button>. Cette rubrique présente l’info-bulle et explique comment créer et personnaliser son contenu.  
  
 
  
<a name="what_is_a_tooltip"></a>   
## <a name="what-is-a-tooltip"></a>Qu’est-ce qu’une info-bulle ?  
 Lorsqu’un utilisateur déplace le pointeur de la souris sur un élément qui contient une info-bulle, une fenêtre qui renferme le contenu de l’info-bulle (par exemple, le contenu texte qui décrit la fonction d’un contrôle) apparaît pendant un laps de temps spécifié. Si l’utilisateur éloigne le pointeur de la souris du contrôle, la fenêtre disparaît car le contenu de l’info-bulle ne peut pas recevoir le focus.  
  
 Une info-bulle peut contenir une ou plusieurs lignes de texte, des images, des formes ou un autre contenu visuel. Pour définir une info-bulle pour un contrôle, vous devez définir l’une des propriétés suivantes pour le contenu de l’info-bulle.  
  
-   <xref:System.Windows.FrameworkContentElement.ToolTip%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>  
  
 Propriété que vous utilisez varie selon que le contrôle qui définit l’info-bulle hérite le <xref:System.Windows.FrameworkContentElement> ou <xref:System.Windows.FrameworkElement> classe.  
  
<a name="create_tooltip"></a>   
## <a name="creating-a-tooltip"></a>Création d’une info-bulle  
 L’exemple suivant montre comment créer une info-bulle simple en définissant le <xref:System.Windows.FrameworkElement.ToolTip%2A> propriété pour un <xref:System.Windows.Controls.Button> contrôle à une chaîne de texte.  
  
 [!code-xaml[GroupBoxSnippet#ToolTipString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipstring)]  
  
 Vous pouvez également définir une info-bulle comme un <xref:System.Windows.Controls.ToolTip> objet. L’exemple suivant utilise [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pour spécifier un <xref:System.Windows.Controls.ToolTip> objet en tant que l’info-bulle d’un <xref:System.Windows.Controls.TextBox> élément. Notez que l’exemple spécifie le <xref:System.Windows.Controls.ToolTip> en définissant le <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType> propriété.  
  
 [!code-xaml[ToolTipSimple#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#tooltip)]  
  
 L’exemple suivant utilise le code pour générer un <xref:System.Windows.Controls.ToolTip> objet. L’exemple crée un <xref:System.Windows.Controls.ToolTip> (`tt`) et l’associe à un <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ToolTipSimple#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ToolTipSimple#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipSimple/VisualBasic/Window1.xaml.vb#2)]  
  
 Vous pouvez également créer le contenu d’info-bulle qui n’est pas défini comme un <xref:System.Windows.Controls.ToolTip> objet en mettant le contenu de l’info-bulle dans un élément de disposition, comme un <xref:System.Windows.Controls.DockPanel>. L’exemple suivant montre comment définir la <xref:System.Windows.FrameworkElement.ToolTip%2A> propriété d’un <xref:System.Windows.Controls.TextBox> au contenu qui est inclu dans un <xref:System.Windows.Controls.DockPanel> contrôle.  
  
 [!code-xaml[GroupBoxSnippet#ToolTipDockPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipdockpanel)]  
  
<a name="Using_the_ToolTip_and_ToolTipService_Properties"></a>   
## <a name="using-the-properties-of-the-tooltip-and-tooltipservice-classes"></a>Utilisation des propriétés de l’info-bulle et des classes ToolTipService  
 Vous pouvez personnaliser le contenu de l’info-bulle en définissant des propriétés visuelles et en appliquant des styles. Si vous définissez l’info-bulle contenu comme un <xref:System.Windows.Controls.ToolTip> de l’objet, vous pouvez définir les propriétés visuelles de la <xref:System.Windows.Controls.ToolTip> objet. Dans le cas contraire, vous devez définir des propriétés jointes équivalentes sur le <xref:System.Windows.Controls.ToolTipService> classe.  
  
 Pour obtenir un exemple montrant comment définir des propriétés pour spécifier la position du contenu de l’info-bulle à l’aide de la <xref:System.Windows.Controls.ToolTip> et <xref:System.Windows.Controls.ToolTipService> propriétés, consultez [positionner une info-bulle](../../../../docs/framework/wpf/controls/how-to-position-a-tooltip.md).  
  
<a name="StylingToolTip"></a>   
## <a name="styling-a-tooltip"></a>Application d’un style à une info-bulle  
 Vous pouvez appliquer un style un <xref:System.Windows.Controls.ToolTip> en définissant une personnalisée <xref:System.Windows.Style>. L’exemple suivant définit un <xref:System.Windows.Style> appelé `Simple` qui montre comment compenser le placement de la <xref:System.Windows.Controls.ToolTip> et modifier son apparence en définissant le <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, et <xref:System.Windows.Controls.Control.FontWeight%2A>.  
  
 [!code-xaml[ToolTipSimple#Style](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#style)]  
  
<a name="UsingtheToolTipServiceTimeIntervalProperties"></a>   
## <a name="using-the-time-interval-properties-of-tooltipservice"></a>Utilisation des propriétés d’intervalle de temps de ToolTipService  
 Le <xref:System.Windows.Controls.ToolTipService> classe fournit les propriétés suivantes pour vous permettre de définir des info-bulle affichent des heures : <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>, <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>, et <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>.  
  
 Utilisez le <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> et <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> propriétés pour spécifier un délai, généralement bref, avant qu’un <xref:System.Windows.Controls.ToolTip> s’affiche et également pour spécifier la durée pendant laquelle un <xref:System.Windows.Controls.ToolTip> reste visible. Pour plus d’informations, consultez la page [Comment : différer l’affichage d’une info-bulle](http://msdn.microsoft.com/library/618e05ef-f2bf-4a53-a0f4-aacb49918bd7).  
  
 Le <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> propriété détermine si les info-bulles des différents contrôles apparaissent sans délai initial lorsque vous déplacez le pointeur de souris rapidement entre eux. Pour plus d’informations sur la <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> propriété, consultez [utiliser la propriété BetweenShowDelay](../../../../docs/framework/wpf/controls/how-to-use-the-betweenshowdelay-property.md).  
  
 L’exemple suivant montre comment définir ces propriétés pour une info-bulle.  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.ToolTipService>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipEventArgs>  
 <xref:System.Windows.Controls.ToolTipEventHandler>  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)
