---
title: "Vue d&#39;ensemble de ToolBar | Microsoft Docs"
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
  - "contrôles, ToolBar"
  - "ToolBar (contrôle)"
ms.assetid: a8edb32c-118d-4f31-b6e6-8899082b504b
caps.latest.revision: 28
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 27
---
# Vue d&#39;ensemble de ToolBar
Les contrôles <xref:System.Windows.Controls.ToolBar> sont les conteneurs d'un groupe de commandes ou des contrôles généralement associés dans leur fonction.  Un <xref:System.Windows.Controls.ToolBar> contient généralement des boutons qui appellent des commandes.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="ToolBarControl"></a>   
## Contrôle ToolBar  
 Le contrôle <xref:System.Windows.Controls.ToolBar> prend son nom de la disposition sous forme de barre des boutons ou autres contrôles figurant sur une ligne ou dans une colonne unique.  Les contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.ToolBar> fournissent un mécanisme de dépassement de capacité qui place dans une zone de débordement spéciale les éléments qui ne tiennent pas naturellement dans un <xref:System.Windows.Controls.ToolBar> à taille limitée.  En outre, les contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> sont habituellement utilisés avec le contrôle <xref:System.Windows.Controls.ToolBarTray> associé, qui fournit un comportement de disposition spécial, ainsi que la prise en charge du dimensionnement et de l'organisation des barres d'outils déterminés par l'utilisateur.  
  
<a name="Creating_ToolBars"></a>   
## Spécification de la position de Toolbars dans un ToolBarTray  
 Utilisez les propriétés <xref:System.Windows.Controls.ToolBar.Band%2A> et <xref:System.Windows.Controls.ToolBar.BandIndex%2A> pour positionner le <xref:System.Windows.Controls.ToolBar> dans le <xref:System.Windows.Controls.ToolBarTray>.  <xref:System.Windows.Controls.ToolBar.Band%2A> indique la position à laquelle le <xref:System.Windows.Controls.ToolBar> est placé dans son <xref:System.Windows.Controls.ToolBarTray> parent.  <xref:System.Windows.Controls.ToolBar.BandIndex%2A> indique l'ordre dans lequel le <xref:System.Windows.Controls.ToolBar> est placé dans sa bande.  L'exemple suivant indique comment utiliser cette propriété pour placer des contrôles <xref:System.Windows.Controls.ToolBar> dans un <xref:System.Windows.Controls.ToolBarTray>.  
  
 [!code-xml[ToolBarExample#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#2)]  
  
<a name="ToolBars_with_Overflow_Items"></a>   
## ToolBars avec éléments de dépassement de capacité  
 Les contrôles <xref:System.Windows.Controls.ToolBar> contiennent souvent un nombre d'éléments supérieur à la capacité de la barre d'outils.  Lorsque cela se produit, le <xref:System.Windows.Controls.ToolBar> affiche un bouton de dépassement de capacité.  Pour afficher les éléments de dépassement de capacité, cliquez sur le bouton de dépassement de capacité et les éléments apparaissent dans une fenêtre indépendante sous le <xref:System.Windows.Controls.ToolBar>.  Le graphique suivant illustre un <xref:System.Windows.Controls.ToolBar> avec des éléments de dépassement de capacité.  
  
 ![Barre d'outils avec dépassement de capacité](../../../../docs/framework/wpf/controls/media/toolbarwithoverflowitem.png "ToolbarWithOverflowItem")  
ToolBars avec éléments de dépassement de capacité  
  
 Vous pouvez spécifier à quel moment un élément d'une barre d'outils est placé sur le panneau de dépassement de capacité en affectant <xref:System.Windows.Controls.OverflowMode?displayProperty=fullName>, <xref:System.Windows.Controls.OverflowMode?displayProperty=fullName> ou <xref:System.Windows.Controls.OverflowMode?displayProperty=fullName> à la propriété <xref:System.Windows.Controls.ToolBar.OverflowMode%2A?displayProperty=fullName> attachée.  L'exemple suivant spécifie que les quatre derniers boutons sur la barre d'outils doivent toujours être placés sur le panneau de dépassement de capacité.  
  
 [!code-xml[ToolBarExample#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#3)]  
  
 Le <xref:System.Windows.Controls.ToolBar> utilise un <xref:System.Windows.Controls.Primitives.ToolBarPanel> et un <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> dans son <xref:System.Windows.Controls.ControlTemplate>.  Le <xref:System.Windows.Controls.Primitives.ToolBarPanel> est responsable de la disposition des éléments sur la barre d'outils.  Le <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> est responsable de la disposition des éléments qui ne tiennent pas sur le <xref:System.Windows.Controls.ToolBar>.  Pour obtenir un exemple d'un <xref:System.Windows.Controls.ControlTemplate> pour un <xref:System.Windows.Controls.ToolBar>, consultez  
  
 [Styles et modèles ToolBar](../../../../docs/framework/wpf/controls/toolbar-styles-and-templates.md).  
  
## Voir aussi  
 <xref:System.Windows.Controls.Primitives.ToolBarPanel>   
 <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>   
 [Donner un style aux contrôles d'une barre d'outils](../../../../docs/framework/wpf/controls/how-to-style-controls-on-a-toolbar.md)   
 [Galerie de contrôles WPF, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=160053)