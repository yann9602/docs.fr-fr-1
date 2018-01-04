---
title: Vue d'ensemble de ContextMenu
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
- controls [WPF], ContextMenu
- ContextMenu controls [WPF], about ContextMenu controls
ms.assetid: 16909c42-799a-4561-91e0-7d69dcfeea91
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0776e7960aa76a76422d01180af5fd6a089bc98b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="contextmenu-overview"></a>Vue d'ensemble de ContextMenu
Le <xref:System.Windows.Controls.ContextMenu> classe représente l’élément qui expose les fonctionnalités à l’aide d’un contexte spécifique <xref:System.Windows.Controls.Menu>. En règle générale, un utilisateur expose le <xref:System.Windows.Controls.ContextMenu> dans les [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] en cliquant sur le bouton de la souris. Cette rubrique présente la <xref:System.Windows.Controls.ContextMenu> élément et fournit des exemples d’utilisation dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et le code.  
  
  
  
<a name="contextmenu_control"></a>   
## <a name="contextmenu-control"></a>Contrôle ContextMenu  
 A <xref:System.Windows.Controls.ContextMenu> est attaché à un contrôle spécifique. Le <xref:System.Windows.Controls.ContextMenu> élément vous permet de présenter aux utilisateurs une liste d’éléments qui spécifient des commandes ou des options qui sont associées à un contrôle spécifique, par exemple, un <xref:System.Windows.Controls.Button>. Les utilisateurs cliquent avec le bouton droit sur le contrôle pour afficher le menu. En règle générale, en cliquant sur un <xref:System.Windows.Controls.MenuItem> ouvre un sous-menu ou entraîne l’application à exécuter une commande.  
  
<a name="creating_contextmenus"></a>   
## <a name="creating-contextmenus"></a>Création d’un ContextMenu  
 Les exemples suivants montrent comment créer un <xref:System.Windows.Controls.ContextMenu> avec les sous-menus. Le <xref:System.Windows.Controls.ContextMenu> contrôles associés à des contrôles de bouton.  
  
 [!code-xaml[ContextMenu#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>   
## <a name="applying-styles-to-a-contextmenu"></a>Application de styles à un ContextMenu  
 À l’aide d’un contrôle <xref:System.Windows.Style>, vous pouvez modifier considérablement l’apparence et le comportement d’un <xref:System.Windows.Controls.ContextMenu> sans avoir à écrire un contrôle personnalisé. Outre la définition de propriétés visuelles, vous pouvez appliquer des styles aux parties d’un contrôle. Par exemple, vous pouvez modifier le comportement de parties du contrôle à l’aide des propriétés, ou vous pouvez ajouter des articles, ou modifier la disposition, un <xref:System.Windows.Controls.ContextMenu>. Les exemples suivants montrent différentes manières d’ajouter des styles à <xref:System.Windows.Controls.ContextMenu> contrôles.  
  
 Le premier exemple définit un style appelé `SimpleSysResources`, qui explique comment utiliser les paramètres système actuels dans votre style. L’exemple affecte <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> comme le <xref:System.Windows.Controls.Control.Background%2A> couleur et <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> comme le <xref:System.Windows.Controls.Control.Foreground%2A> couleur de la <xref:System.Windows.Controls.ContextMenu>.  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=   
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=   
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 L’exemple suivant utilise le <xref:System.Windows.Trigger> élément pour modifier l’apparence d’un <xref:System.Windows.Controls.Menu> en réponse aux événements déclenchés sur le <xref:System.Windows.Controls.ContextMenu>. Lorsqu’un utilisateur déplace la souris sur le menu, l’apparence de la <xref:System.Windows.Controls.ContextMenu> modifications d’éléments.  
  
```xaml  
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
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.ContextMenu>  
 <xref:System.Windows.Style>  
 <xref:System.Windows.Controls.Menu>  
 <xref:System.Windows.Controls.MenuItem>  
 [ContextMenu](../../../../docs/framework/wpf/controls/contextmenu.md)  
 [Styles et modèles ContextMenu](../../../../docs/framework/wpf/controls/contextmenu-styles-and-templates.md)  
 [Exemple de galerie de contrôles WPF](http://go.microsoft.com/fwlink/?LinkID=160053)
