---
title: "Comment&#160;: reconna&#238;tre des gestes d&#39;application | Microsoft Docs"
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
  - "mouvements d'application, reconnaître"
  - "mouvements, reconnaître"
ms.assetid: d58b740f-5192-4a3e-af59-7aa162e6ca15
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# Comment&#160;: reconna&#238;tre des gestes d&#39;application
L'exemple suivant montre comment effacer l'encre lorsqu'un utilisateur fait un geste <xref:System.Windows.Ink.ApplicationGesture> sur un <xref:System.Windows.Controls.InkCanvas>.  Cet exemple suppose qu'un <xref:System.Windows.Controls.InkCanvas>, appelé `inkCanvas1`, est déclaré dans le fichier XAML.  
  
## Exemple  
 [!code-csharp[HowToRecognizeGestures#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToRecognizeGestures/CSharp/Window1.xaml.cs#1)]
 [!code-vb[HowToRecognizeGestures#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToRecognizeGestures/VisualBasic/Window1.xaml.vb#1)]  
  
## Voir aussi  
 <xref:System.Windows.Ink.ApplicationGesture>   
 <xref:System.Windows.Controls.InkCanvas>   
 <xref:System.Windows.Controls.InkCanvas.Gesture>