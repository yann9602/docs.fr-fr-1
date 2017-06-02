---
title: "Comment&#160;: extraire le texte d&#39;un RichTextBox | Microsoft Docs"
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
  - "contenu, extraire"
  - "extraire un contenu de texte"
  - "RichTextBox (contrôle), extraire un contenu de texte"
  - "Texte, extraire"
ms.assetid: f13c093f-1a05-45b3-ac8f-c9ea5e4a11c5
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: extraire le texte d&#39;un RichTextBox
Cet exemple montre comment extraire le contenu d'un <xref:System.Windows.Controls.RichTextBox> sous la forme d'un texte brut.  
  
## Exemple  
 Le code [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] suivant décrit un contrôle nommé <xref:System.Windows.Controls.RichTextBox> avec du contenu simple.  
  
 [!code-xml[RichTextBoxSnippets#_RTB_XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml#_rtb_xaml)]  
  
## Exemple  
 Le code suivant implémente une méthode qui prend une <xref:System.Windows.Controls.RichTextBox> comme argument et retourne une chaîne qui représente le contenu de texte brut de la <xref:System.Windows.Controls.RichTextBox>.  
  
 La méthode crée un <xref:System.Windows.Documents.TextRange> à partir du contenu de la <xref:System.Windows.Controls.RichTextBox>, à l'aide de <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> et de <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> pour indiquer la plage de contenu à extraire.  Les propriétés <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> et <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> retournent chacune un <xref:System.Windows.Documents.TextPointer>, et sont accessibles dans le FlowDocument sous\-jacent qui représente le contenu de la <xref:System.Windows.Controls.RichTextBox>.  <xref:System.Windows.Documents.TextRange> fournit une propriété Text qui retourne les parties de texte brut de la <xref:System.Windows.Documents.TextRange> sous la forme d'une chaîne.  
  
 [!code-csharp[RichTextBoxSnippets#_RTB_StringFrom](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml.cs#_rtb_stringfrom)]
 [!code-vb[RichTextBoxSnippets#_RTB_StringFrom](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxSnippets/visualbasic/window1.xaml.vb#_rtb_stringfrom)]  
  
## Voir aussi  
 [Vue d'ensemble de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)   
 [Vue d'ensemble de TextBox](../../../../docs/framework/wpf/controls/textbox-overview.md)