---
title: "Comment&#160;: faire pivoter l&#39;encre | Microsoft Docs"
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
  - "encre, faire pivoter"
  - "faire pivoter l'encre"
ms.assetid: fac36cc9-dd01-41ca-9bde-9d33e3790bbe
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: faire pivoter l&#39;encre
## Exemple  
 L'exemple suivant copie l'encre d'un <xref:System.Windows.Controls.InkCanvas> vers un <xref:System.Windows.Controls.Canvas> qui contient un <xref:System.Windows.Controls.InkPresenter>.  Lorsque l'application copie l'encre, elle la fait également pivoter à 90 degrés dans le sens des aiguilles d'une montre.  
  
 [!code-xml[HowToRotateInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToRotateInk/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[HowToRotateInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToRotateInk/CSharp/Window1.xaml.cs#2)]  
  
## Exemple  
 L'exemple suivant est un <xref:System.Windows.Documents.Adorner> personnalisé qui fait pivoter les traits sur un <xref:System.Windows.Controls.InkPresenter>.  
  
 [!code-csharp[AdornerForStrokes#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornerForStrokes/CSharp/RotatingAdornerForStrokes.cs#1)]
 [!code-vb[AdornerForStrokes#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornerForStrokes/VisualBasic/RotatingAdornerForStrokes.vb#1)]  
  
 L'exemple suivant est un fichier [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] qui définit un <xref:System.Windows.Controls.InkPresenter> et le remplit avec l'encre.  Le gestionnaire d'événements `Window_Loaded` ajoute l'ornement personnalisé au <xref:System.Windows.Controls.InkPresenter>.  
  
 [!code-xml[AdornerForStrokes#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornerForStrokes/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[AdornerForStrokes#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornerForStrokes/CSharp/Window1.xaml.cs#3)]
 [!code-vb[AdornerForStrokes#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornerForStrokes/VisualBasic/Window1.xaml.vb#3)]