---
title: "Vue d&#39;ensemble de ContextMenu | Microsoft Docs"
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
  - "contrôles ContextMenu (WPF), à propos des contrôles ContextMenu"
  - "contrôles, ContextMenu"
ms.assetid: 16909c42-799a-4561-91e0-7d69dcfeea91
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# Vue d&#39;ensemble de ContextMenu
La classe <xref:System.Windows.Controls.ContextMenu> représente l'élément qui expose les fonctionnalités à l'aide d'un <xref:System.Windows.Controls.Menu> spécifique au contexte.  En général, un utilisateur expose le <xref:System.Windows.Controls.ContextMenu> dans l'[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] en cliquant avec le bouton droit de la souris.  Cette rubrique présente l'élément <xref:System.Windows.Controls.ContextMenu> et fournit des exemples d'utilisation de cet élément dans le [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et le code.  
  
   
  
<a name="contextmenu_control"></a>   
## Contrôle ContextMenu  
 Un <xref:System.Windows.Controls.ContextMenu> est associé à un contrôle spécifique.  L'élément <xref:System.Windows.Controls.ContextMenu> vous permet de présenter aux utilisateurs une liste d'éléments qui spécifient des commandes ou des options associées à un contrôle particulier, par exemple, un <xref:System.Windows.Controls.Button>.  Les utilisateurs cliquent avec le bouton droit sur le contrôle pour afficher le menu.  En général, le fait de cliquer sur <xref:System.Windows.Controls.MenuItem> ouvre un sous\-menu ou entraîne l'application à exécuter une commande.  
  
<a name="creating_contextmenus"></a>   
## Création de ContextMenus  
 Les exemples suivants indiquent comment créer un <xref:System.Windows.Controls.ContextMenu> avec des sous\-menus.  Les contrôles <xref:System.Windows.Controls.ContextMenu> sont associés aux contrôles bouton.  
  
 [!code-xml[ContextMenu#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>   
## Application de styles à un ContextMenu  
 En utilisant un <xref:System.Windows.Style> de contrôle, vous pouvez modifier radicalement l'apparence et le comportement d'un <xref:System.Windows.Controls.ContextMenu> sans écrire un contrôle personnalisé.  Outre la définition de propriétés visuelles, vous pouvez également appliquer des styles aux parties d'un contrôle.  Par exemple, vous pouvez modifier le comportement de parties du contrôle en utilisant des propriétés, ou vous pouvez ajouter des parties à un <xref:System.Windows.Controls.ContextMenu> ou modifier la disposition de ce dernier.  Les exemples suivants indiquent plusieurs façons d'ajouter des styles à des contrôles <xref:System.Windows.Controls.ContextMenu>.  
  
 Le premier exemple définit un style appelé `SimpleSysResources`, qui indique comment utiliser les paramètres système actifs dans votre style.  L'exemple assigne <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> comme couleur <xref:System.Windows.Controls.Control.Background%2A> et <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> comme couleur <xref:System.Windows.Controls.Control.Foreground%2A> du <xref:System.Windows.Controls.ContextMenu>.  
  
```  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=   
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=   
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 L'exemple suivant utilise l'élément <xref:System.Windows.Trigger> pour modifier l'apparence d'un <xref:System.Windows.Controls.Menu> en réponse aux événements déclenchés sur le <xref:System.Windows.Controls.ContextMenu>.  Lorsqu'un utilisateur déplace la souris sur le menu, l'apparence des éléments du <xref:System.Windows.Controls.ContextMenu> change.  
  
```  
<Style x:Key="Triggers" TargetType="{x:Type MenuItem}">  
  <Style.Triggers>  
    <Trigger Property="MenuItem.IsMouseOver" Value="true">  
      <Setter Property = "FontSize" Value="16"/>  
      <Setter Property = "FontStyle" Value="Italic"/>  
      <Setter Property = "Foreground" Value="Red"/>  
    </Trigger>  
  </Style.Triggers>  
</Style>  
```  
  
## Voir aussi  
 <xref:System.Windows.Controls.ContextMenu>   
 <xref:System.Windows.Style>   
 <xref:System.Windows.Controls.Menu>   
 <xref:System.Windows.Controls.MenuItem>   
 [ContextMenu](../../../../docs/framework/wpf/controls/contextmenu.md)   
 [Styles et modèles ContextMenu](../../../../docs/framework/wpf/controls/contextmenu-styles-and-templates.md)   
 [Galerie de contrôles WPF, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=160053)