---
title: "Comment&#160;: am&#233;liorer les performances de d&#233;filement d&#39;un contr&#244;le ListBox | Microsoft Docs"
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
  - "ListBox (contrôle WPF), améliorer les performances de défilement"
  - "ListBox (contrôle WPF), réutiliser les conteneurs d'éléments"
ms.assetid: 1e2bf8f3-c8ce-47f7-a400-a7fe11d1a848
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: am&#233;liorer les performances de d&#233;filement d&#39;un contr&#244;le ListBox
Si un <xref:System.Windows.Controls.ListBox> contient de nombreux éléments, la réponse de l'interface utilisateur risque d'être lente lorsqu'un utilisateur fait défiler le <xref:System.Windows.Controls.ListBox> à l'aide de la roulette de la souris ou en faisant glisser le curseur d'une barre de défilement.  Vous pouvez améliorer les performances de <xref:System.Windows.Controls.ListBox> lorsque l'utilisateur effectue un défilement en affectant à la propriété jointe <xref:System.Windows.Controls.VirtualizingStackPanel.VirtualizationMode%2A?displayProperty=fullName> la valeur <xref:System.Windows.Controls.VirtualizationMode>.  
  
## Exemple  
  
## Description  
 L'exemple suivant crée un <xref:System.Windows.Controls.ListBox> et affecte à <xref:System.Windows.Controls.VirtualizingStackPanel.VirtualizationMode%2A?displayProperty=fullName> la valeur <xref:System.Windows.Controls.VirtualizationMode> pour améliorer les performances de défilement.  
  
## Code  
 [!code-xml[RecycleItemContainerShippets#VirtualizationMode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizationmode)]  
  
 L'exemple suivant présente les données utilisées dans l'exemple précédent.  
  
 [!code-csharp[RecycleItemContainerShippets#ListBoxData](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#listboxdata)]
 [!code-vb[RecycleItemContainerShippets#ListBoxData](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#listboxdata)]