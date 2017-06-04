---
title: "Comment&#160;: aligner horizontalement ou verticalement le contenu dans un StackPanel | Microsoft Docs"
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
  - "aligner, contenu"
  - "alignement de contenu"
  - "StackPanel (contrôle), alignement de contenu"
ms.assetid: c1e8f962-72c8-4e7a-8670-7a2d7e021791
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: aligner horizontalement ou verticalement le contenu dans un StackPanel
Cet exemple montre comment ajuster l'<xref:System.Windows.Controls.StackPanel.Orientation%2A> du contenu dans un élément <xref:System.Windows.Controls.StackPanel> et comment ajuster le <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> et le <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> du contenu enfant.  
  
## Exemple  
 L'exemple suivant crée trois éléments <xref:System.Windows.Controls.ListBox> en [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  Chaque <xref:System.Windows.Controls.ListBox> représente les valeurs possibles des propriétés <xref:System.Windows.Controls.StackPanel.Orientation%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> et <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> d'un <xref:System.Windows.Controls.StackPanel>.  Lorsqu'un utilisateur sélectionne une valeur dans l'un des éléments <xref:System.Windows.Controls.ListBox>, la propriété associée du <xref:System.Windows.Controls.StackPanel> et ses éléments <xref:System.Windows.Controls.Button> enfants sont modifiés.  
  
 [!code-xml[StackPanelIntroSamp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml#1)]  
  
 Le fichier code\-behind suivant définit les modifications des événements associés aux modifications de sélection <xref:System.Windows.Controls.ListBox>.  <xref:System.Windows.Controls.StackPanel> est identifié par le <xref:System.Windows.FrameworkElement.Name%2A> `sp1`.  
  
 [!code-csharp[StackPanelIntroSamp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[StackPanelIntroSamp#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelIntroSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.StackPanel>   
 <xref:System.Windows.Controls.ListBox>   
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>   
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>   
 [Vue d'ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md)