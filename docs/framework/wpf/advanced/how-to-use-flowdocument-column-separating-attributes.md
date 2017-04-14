---
title: "Comment&#160;: utiliser les attributs de s&#233;paration de colonnes de FlowDocument | Microsoft Docs"
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
  - "attributs de séparation de colonnes"
  - "documents, attributs de séparation de colonnes FlowDocument"
  - "attributs de séparation de colonnes FlowDocument"
ms.assetid: c7a822f8-aeca-45bd-a258-2852ff28005c
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: utiliser les attributs de s&#233;paration de colonnes de FlowDocument
Cet exemple montre comment utiliser les fonctionnalités de séparation de colonnes de <xref:System.Windows.Documents.FlowDocument>.  
  
## Exemple  
 L'exemple suivant définit un <xref:System.Windows.Documents.FlowDocument> et définit les attributs <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A> et <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A>.  Le <xref:System.Windows.Documents.FlowDocument> contient un paragraphe unique d'exemple de contenu.  
  
 [!code-xml[FlowDocumentSnippets#_FlowDocumentColumnStuffXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml#_flowdocumentcolumnstuffxaml)]  
  
 L'illustration suivante montre les effets des attributs <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A> et <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> dans un <xref:System.Windows.Documents.FlowDocument> rendu.  
  
 ![Capture d'écran : FlowDocument intra&#45;colonnes](../../../../docs/framework/wpf/advanced/media/flowdocumentintracolumn.png "FlowDocumentIntraColumn")