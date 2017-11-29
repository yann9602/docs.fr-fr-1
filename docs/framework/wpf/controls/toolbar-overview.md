---
title: Vue d'ensemble de ToolBar
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], ToolBar
- ToolBar control [WPF]
ms.assetid: a8edb32c-118d-4f31-b6e6-8899082b504b
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dddf6940e180b3d997357390ead38f99f52994ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="toolbar-overview"></a>Vue d'ensemble de ToolBar
<xref:System.Windows.Controls.ToolBar>les contrôles sont des conteneurs d’un groupe de commandes ou des contrôles généralement associés dans leur fonction. A <xref:System.Windows.Controls.ToolBar> contient généralement des boutons qui appellent des commandes.  
  
  
<a name="ToolBarControl"></a>   
## <a name="toolbar-control"></a>ToolBar, contrôle  
 Le <xref:System.Windows.Controls.ToolBar> contrôle tire son nom de la disposition sous forme de barre de boutons ou d’autres contrôles dans une seule ligne ou colonne. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.ToolBar> contrôles offrent un mécanisme de dépassement de capacité qui place tous les éléments qui ne tiennent pas naturellement au sein d’une contrainte de taille <xref:System.Windows.Controls.ToolBar> dans une zone de débordement spéciale. En outre, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> les contrôles sont généralement utilisés avec le <xref:System.Windows.Controls.ToolBarTray> contrôle, qui fournit le comportement de disposition spécial ainsi que la prise en charge de dimensionnement et d’organiser des barres d’outils initiée par l’utilisateur.  
  
<a name="Creating_ToolBars"></a>   
## <a name="specifying-the-position-of-toolbars-in-a-toolbartray"></a>Spécifier la position des contrôles ToolBar dans un ToolBarTray  
 Utilisez le <xref:System.Windows.Controls.ToolBar.Band%2A> et <xref:System.Windows.Controls.ToolBar.BandIndex%2A> propriétés pour positionner le <xref:System.Windows.Controls.ToolBar> dans le <xref:System.Windows.Controls.ToolBarTray>. <xref:System.Windows.Controls.ToolBar.Band%2A>Indique la position à laquelle le <xref:System.Windows.Controls.ToolBar> est placé dans son parent <xref:System.Windows.Controls.ToolBarTray>. <xref:System.Windows.Controls.ToolBar.BandIndex%2A>Indique l’ordre dans lequel le <xref:System.Windows.Controls.ToolBar> est placé dans sa bande. L’exemple suivant montre comment utiliser cette propriété pour placer <xref:System.Windows.Controls.ToolBar> contrôle à l’intérieur d’un <xref:System.Windows.Controls.ToolBarTray>.  
  
 [!code-xaml[ToolBarExample#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#2)]  
  
<a name="ToolBars_with_Overflow_Items"></a>   
## <a name="toolbars-with-overflow-items"></a>Contrôles ToolBar avec éléments de dépassement  
 Souvent <xref:System.Windows.Controls.ToolBar> contrôles contiennent plus d’éléments que s’adaptent à la taille de la barre d’outils. Dans ce cas, la <xref:System.Windows.Controls.ToolBar> affiche un bouton de dépassement de capacité. Pour afficher les éléments de dépassement de capacité, un utilisateur clique sur le bouton de dépassement de capacité et les éléments sont affichés dans une fenêtre contextuelle ci-dessous le <xref:System.Windows.Controls.ToolBar>. Le graphique suivant illustre un <xref:System.Windows.Controls.ToolBar> avec des éléments de dépassement de capacité.  
  
 ![Barre d’outils avec dépassement de capacité](../../../../docs/framework/wpf/controls/media/toolbarwithoverflowitem.png "ToolbarWithOverflowItem")  
ToolBar avec éléments de dépassement  
  
 Vous pouvez spécifier quand un élément dans une barre d’outils est placé sur le panneau de dépassement de capacité en définissant le <xref:System.Windows.Controls.ToolBar.OverflowMode%2A?displayProperty=nameWithType> propriété attachée <xref:System.Windows.Controls.OverflowMode.Always?displayProperty=nameWithType>, <xref:System.Windows.Controls.OverflowMode.Never?displayProperty=nameWithType>, ou <xref:System.Windows.Controls.OverflowMode.AsNeeded?displayProperty=nameWithType>. L’exemple suivant spécifie que les quatre derniers boutons de la barre d’outils doivent toujours se trouver sur le panneau de dépassement.  
  
 [!code-xaml[ToolBarExample#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#3)]  
  
 Le <xref:System.Windows.Controls.ToolBar> utilise un <xref:System.Windows.Controls.Primitives.ToolBarPanel> et un <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> dans son <xref:System.Windows.Controls.ControlTemplate>.  Le <xref:System.Windows.Controls.Primitives.ToolBarPanel> est responsable de la disposition des éléments dans la barre d’outils.  Le <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> est responsable de la disposition des éléments qui ne tiennent pas dans le <xref:System.Windows.Controls.ToolBar>. Pour obtenir un exemple d’un <xref:System.Windows.Controls.ControlTemplate> pour un <xref:System.Windows.Controls.ToolBar>, consultez  
  
 [Styles et modèles ToolBar](../../../../docs/framework/wpf/controls/toolbar-styles-and-templates.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
 <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
 [Donner un style aux contrôles d'une barre d'outils](../../../../docs/framework/wpf/controls/how-to-style-controls-on-a-toolbar.md)  
 [Exemple de galerie de contrôles WPF](http://go.microsoft.com/fwlink/?LinkID=160053)
