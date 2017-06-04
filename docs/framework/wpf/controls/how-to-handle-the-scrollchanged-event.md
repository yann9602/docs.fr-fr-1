---
title: "Comment&#160;: g&#233;rer l&#39;&#233;v&#233;nement ScrollChanged | Microsoft Docs"
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
  - "événements ScrollChanged"
  - "ScrollViewer (contrôle), déclencher des événements ScrollChanged"
ms.assetid: 42c695d8-ee28-49d4-80fd-fc71e9be7f29
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: g&#233;rer l&#39;&#233;v&#233;nement ScrollChanged
## Exemple  
 Cet exemple montre comment gérer l'événement <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> d'un <xref:System.Windows.Controls.ScrollViewer>.  
  
 Un élément <xref:System.Windows.Documents.FlowDocument> avec des parties <xref:System.Windows.Documents.Paragraph> est défini en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  Lorsque l'événement <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> se produit suite à l'intervention de l'utilisateur, un gestionnaire est appelé, et le texte est écrit dans un <xref:System.Windows.Controls.TextBlock> qui indique que l'événement s'est produit.  
  
 [!code-xml[scrollchangedeventargsLayout#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/scrollchangedeventargsLayout/CSharp/Window1.xaml#1)]  
[!code-xml[scrollchangedeventargsLayout#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/scrollchangedeventargsLayout/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[scrollchangedeventargsLayout#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/scrollchangedeventargsLayout/CSharp/Window1.xaml.cs#3)]
 [!code-vb[scrollchangedeventargsLayout#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/scrollchangedeventargsLayout/VisualBasic/Window1.xaml.vb#3)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.ScrollViewer>   
 <xref:System.Windows.Controls.ScrollViewer.ScrollChanged>   
 <xref:System.Windows.Controls.ScrollChangedEventHandler>   
 <xref:System.Windows.Controls.ScrollChangedEventArgs>