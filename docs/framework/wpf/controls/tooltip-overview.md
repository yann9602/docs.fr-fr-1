---
title: "Vue d&#39;ensemble de l&#39;info-bulle | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contrôles, Info-bulle"
  - "ToolTip (contrôle), à propos du contrôle ToolTip"
ms.assetid: f06c1603-e9cb-4809-8a62-234607fc52f7
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# Vue d&#39;ensemble de l&#39;info-bulle
Une info\-bulle est une petite fenêtre indépendante qui apparaît lorsqu'un utilisateur place le pointeur de la souris sur un élément, tel qu'un <xref:System.Windows.Controls.Button>.  Cette rubrique présente l'info\-bulle et explique comment créer et personnaliser son contenu.  
  
   
  
<a name="what_is_a_tooltip"></a>   
## Qu'est\-ce qu'une info\-bulle ?  
 Lorsqu'un utilisateur déplace le pointeur de la souris sur un élément doté d'une info\-bulle, une fenêtre comprenant le contenu de l'info\-bulle \(par exemple, contenu de texte qui décrit la fonction d'un contrôle\) apparaît pendant une période spécifiée.  Si l'utilisateur éloigne le pointeur de la souris du contrôle, la fenêtre disparaît car le contenu de l'info\-bulle ne peut pas recevoir le focus.  
  
 Le contenu d'une info\-bulle peut contenir une ou plusieurs lignes de texte, images, formes ou autre contenu visuel.  Vous définissez une info\-bulle pour un contrôle en affectant à l'une des propriétés suivantes le contenu de l'info\-bulle.  
  
-   <xref:System.Windows.FrameworkContentElement.ToolTip%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=fullName>  
  
 La propriété que vous utilisez varie selon que le contrôle qui définit l'info\-bulle hérite de la classe <xref:System.Windows.FrameworkContentElement> ou <xref:System.Windows.FrameworkElement>.  
  
<a name="create_tooltip"></a>   
## Création d'une info\-bulle  
 L'exemple suivant montre comment créer une info\-bulle simple en affectant une chaîne de texte à la propriété <xref:System.Windows.FrameworkElement.ToolTip%2A> pour un contrôle <xref:System.Windows.Controls.Button>.  
  
 [!code-xml[GroupBoxSnippet#ToolTipString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipstring)]  
  
 Vous pouvez également définir une info\-bulle comme un objet <xref:System.Windows.Controls.ToolTip>.  L'exemple suivant utilise [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pour spécifier un objet <xref:System.Windows.Controls.ToolTip> comme info\-bulle d'un élément <xref:System.Windows.Controls.TextBox>.  Notez que l'exemple spécifie le <xref:System.Windows.Controls.ToolTip> en définissant la propriété <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=fullName>.  
  
 [!code-xml[ToolTipSimple#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#tooltip)]  
  
 L'exemple suivant utilise du code pour générer un objet <xref:System.Windows.Controls.ToolTip>.  L'exemple crée un <xref:System.Windows.Controls.ToolTip> \(`tt`\) et l'associe à un <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ToolTipSimple#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ToolTipSimple#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipSimple/VisualBasic/Window1.xaml.vb#2)]  
  
 Vous pouvez également créer un contenu d'info\-bulle qui n'est pas défini comme un objet <xref:System.Windows.Controls.ToolTip> en englobant le contenu d'info\-bulle dans un élément de disposition, tel qu'un <xref:System.Windows.Controls.DockPanel>.  L'exemple suivant montre comment affecter à la propriété <xref:System.Windows.FrameworkElement.ToolTip%2A> d'un <xref:System.Windows.Controls.TextBox> le contenu qui est englobé dans un contrôle <xref:System.Windows.Controls.DockPanel>.  
  
 [!code-xml[GroupBoxSnippet#ToolTipDockPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipdockpanel)]  
  
<a name="Using_the_ToolTip_and_ToolTipService_Properties"></a>   
## Utilisation des propriétés de l'info\-bulle et des classes ToolTipService  
 Vous pouvez personnaliser le contenu d'info\-bulle en définissant des propriétés visuelles et en appliquant des styles.  Si vous définissez le contenu d'info\-bulle comme un objet <xref:System.Windows.Controls.ToolTip>, vous pouvez définir les propriétés visuelles de l'objet <xref:System.Windows.Controls.ToolTip>.  Dans le cas contraire, vous devez définir des [propriétés attachées](GTMT) équivalentes sur la classe <xref:System.Windows.Controls.ToolTipService>.  
  
 Pour obtenir un exemple de définition des propriétés pour spécifier la position du contenu d'info\-bulle à l'aide des propriétés <xref:System.Windows.Controls.ToolTip> et <xref:System.Windows.Controls.ToolTipService>, consultez [Positionner une info\-bulle](../../../../docs/framework/wpf/controls/how-to-position-a-tooltip.md).  
  
<a name="StylingToolTip"></a>   
## Application d'un style à une info\-bulle  
 Vous pouvez appliquer un style à un <xref:System.Windows.Controls.ToolTip> en définissant un <xref:System.Windows.Style> personnalisé.  L'exemple suivant définit un <xref:System.Windows.Style> appelé `Simple` qui indique comment décaler le positionnement du <xref:System.Windows.Controls.ToolTip> et modifier son apparence en définissant <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.FontSize%2A> et <xref:System.Windows.Controls.Control.FontWeight%2A>.  
  
 [!code-xml[ToolTipSimple#Style](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#style)]  
  
<a name="UsingtheToolTipServiceTimeIntervalProperties"></a>   
## Utilisation des propriétés d'intervalle de temps de ToolTipService  
 La classe <xref:System.Windows.Controls.ToolTipService> vous fournit les propriétés suivantes afin de définir des temps d'affichage d'info\-bulle : <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>, <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> et <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>.  
  
 Utilisez les propriétés <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> et <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> pour spécifier un délai, généralement bref, avant qu'un <xref:System.Windows.Controls.ToolTip> apparaisse et également pour spécifier combien de temps un <xref:System.Windows.Controls.ToolTip> reste visible.  Pour plus d'informations, consultez [How to: Delay the Display of a ToolTip](http://msdn.microsoft.com/fr-fr/618e05ef-f2bf-4a53-a0f4-aacb49918bd7).  
  
 La propriété <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> détermine si les info\-bulles des différents contrôles apparaissent sans délai initial lorsque vous déplacez rapidement le pointeur de la souris entre eux.  Pour plus d'informations sur la propriété <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>, consultez [Utiliser la propriété BetweenShowDelay](../../../../docs/framework/wpf/controls/how-to-use-the-betweenshowdelay-property.md).  
  
 L'exemple suivant montre comment définir ces propriétés pour une info\-bulle.  
  
 [!code-xml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.ToolTipService>   
 <xref:System.Windows.Controls.ToolTip>   
 <xref:System.Windows.Controls.ToolTipEventArgs>   
 <xref:System.Windows.Controls.ToolTipEventHandler>   
 [Rubriques Comment](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)