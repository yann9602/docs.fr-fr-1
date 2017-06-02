---
title: "Comment&#160;: cr&#233;er un effet de substitution &#224; l&#39;aide d&#39;&#233;v&#233;nements | Microsoft Docs"
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
  - "couleurs des éléments, modifier"
  - "éléments (couleurs), modifier"
  - "effets de substitution"
ms.assetid: 3b20d028-6f1c-4b25-95d2-fa68cefbdb4c
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: cr&#233;er un effet de substitution &#224; l&#39;aide d&#39;&#233;v&#233;nements
Cet exemple montre comment modifier la couleur d'un élément lorsque le pointeur de la souris entre et sort de la zone occupée par l'élément.  
  
 Cet exemple comprend un fichier [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et un fichier code\-behind.  
  
> [!NOTE]
>  Cet exemple montre comment utiliser des événements, mais la méthode recommandée pour parvenir à ce même effet consiste à utiliser un <xref:System.Windows.Trigger> dans un style.  Pour plus d'informations, consultez [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
## Exemple  
 Le [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] suivant crée l'interface utilisateur, qui se compose de <xref:System.Windows.Controls.Border> autour d'un <xref:System.Windows.Controls.TextBlock> et joint les gestionnaires d'événements <xref:System.Windows.Input.Mouse.MouseEnter> et <xref:System.Windows.UIElement.MouseLeave> au <xref:System.Windows.Controls.Border>.  
  
 [!code-xml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 Le code\-behind suivant crée les gestionnaires d'événements <xref:System.Windows.UIElement.MouseEnter> et <xref:System.Windows.UIElement.MouseLeave>.  Lorsque le pointeur de la souris entre dans le <xref:System.Windows.Controls.Border>, l'arrière\-plan du <xref:System.Windows.Controls.Border> est modifié en rouge.  Lorsque le pointeur de la souris quitte le <xref:System.Windows.Controls.Border>, l'arrière\-plan du <xref:System.Windows.Controls.Border> repasse au blanc.  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]