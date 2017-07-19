---
title: "Comment&#160;: obtenir un ListBoxItem | Microsoft Docs"
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
  - "contrôles ListBox, obtenir un ListBoxItem"
  - "ListBoxItem"
ms.assetid: da877c6f-5fd8-40cb-8909-225cbfd99aa5
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: obtenir un ListBoxItem
Si vous devez obtenir un <xref:System.Windows.Controls.ListBoxItem> spécifique à un index particulier dans un <xref:System.Windows.Controls.ListBox>, vous pouvez utiliser un <xref:System.Windows.Controls.ItemContainerGenerator>.  
  
## Exemple  
 L'exemple suivant montre un <xref:System.Windows.Controls.ListBox> et ses éléments.  
  
 [!code-xml[ListBoxItems#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml#1)]  
  
 L'exemple suivant montre comment extraire l'élément en spécifiant son index dans la propriété <xref:System.Windows.Controls.ItemContainerGenerator.ContainerFromIndex%2A> du <xref:System.Windows.Controls.ItemContainerGenerator>.  
  
 [!code-csharp[ListBoxItems#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ListBoxItems#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxItems/VisualBasic/Window1.xaml.vb#2)]  
  
 Après avoir extrait l'élément de zone de liste, vous pouvez afficher le contenu de l'élément, comme représenté dans l'exemple suivant.  
  
 [!code-csharp[ListBoxItems#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml.cs#3)]
 [!code-vb[ListBoxItems#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxItems/VisualBasic/Window1.xaml.vb#3)]