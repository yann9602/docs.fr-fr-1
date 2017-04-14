---
title: "Comment&#160;: modifier la typographie d&#39;un texte | Microsoft Docs"
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
  - "définir des attributs Typography"
  - "Typography (attribut), définir"
ms.assetid: 19a3b49b-60a2-4c11-a786-e26b4c965588
caps.latest.revision: 3
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 3
---
# Comment&#160;: modifier la typographie d&#39;un texte
L'exemple suivant montre comment définir l'attribut <xref:System.Windows.Documents.TextElement.Typography%2A> en utilisant l'élément <xref:System.Windows.Documents.Paragraph> comme exemple.  
  
## Exemple  
 [!code-xml[TextElementSnippets#_TextElement_TypogXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]  
  
 L'illustration suivante montre comment s'affiche cet exemple.  
  
 ![Capture d'écran : texte avec typographie altérée](../../../../docs/framework/wpf/advanced/media/textelement-typog.png "TextElement\_Typog")  
  
 Par contraste, l'illustration suivante montre comment s'affiche un exemple similaire avec des propriétés typographiques par défaut.  
  
 ![Capture d'écran : texte avec typographie altérée](../../../../docs/framework/wpf/advanced/media/textelement-typog-default.png "TextElement\_Typog\_Default")  
  
## Exemple  
 L'exemple suivant montre comment définir la propriété <xref:System.Windows.Controls.TextBox.Typography%2A> par programmation.  
  
 [!code-csharp[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
 [!code-vb[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]  
  
## Voir aussi  
 [Vue d'ensemble des documents dynamiques](../../../../docs/framework/wpf/advanced/flow-document-overview.md)