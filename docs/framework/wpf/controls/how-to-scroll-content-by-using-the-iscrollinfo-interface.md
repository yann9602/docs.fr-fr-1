---
title: "Comment&#160;: faire d&#233;filer le contenu &#224; l&#39;aide de l&#39;interface IScrollInfo | Microsoft Docs"
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
  - "IScrollInfo (interface)"
  - "faire défiler un contenu"
  - "ScrollViewer (contrôle), faire défiler un contenu"
ms.assetid: d8700bef-a3f8-4c12-9de2-fc3b79f32cd3
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: faire d&#233;filer le contenu &#224; l&#39;aide de l&#39;interface IScrollInfo
Cet exemple montre comment faire défiler le contenu à l'aide de l'interface <xref:System.Windows.Controls.Primitives.IScrollInfo>.  
  
## Exemple  
 L'exemple suivant illustre les fonctionnalités de l'interface <xref:System.Windows.Controls.Primitives.IScrollInfo>.  L'exemple crée un élément <xref:System.Windows.Controls.StackPanel> en [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] qui est imbriqué dans un <xref:System.Windows.Controls.ScrollViewer> parent.  Les éléments enfants du <xref:System.Windows.Controls.StackPanel> peuvent faire l'objet d'un défilement logique en utilisant les méthodes définies par l'interface <xref:System.Windows.Controls.Primitives.IScrollInfo> et être castés en instance de <xref:System.Windows.Controls.StackPanel> \(`sp1`\) dans le code.  
  
 [!code-xml[IScrollInfoMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml#2)]  
  
 Chaque <xref:System.Windows.Controls.Button> du fichier [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] déclenche une méthode personnalisée associée qui contrôle le comportement de défilement dans <xref:System.Windows.Controls.StackPanel>.  L'exemple suivant montre comment utiliser les méthodes <xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> et <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> ; il indique également de manière générique comment utiliser toutes les méthodes de positionnement que la classe <xref:System.Windows.Controls.Primitives.IScrollInfo> définit.  
  
 [!code-csharp[IScrollInfoMethods#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.ScrollViewer>   
 <xref:System.Windows.Controls.Primitives.IScrollInfo>   
 <xref:System.Windows.Controls.StackPanel>   
 [Vue d'ensemble de ScrollViewer](../../../../docs/framework/wpf/controls/scrollviewer-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/controls/scrollviewer-how-to-topics.md)   
 [Vue d'ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md)