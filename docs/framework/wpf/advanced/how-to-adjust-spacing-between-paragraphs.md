---
title: "Comment&#160;: ajuster l&#39;espacement entre les paragraphes | Microsoft Docs"
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
  - "documents, ajuster l'espacement entre les paragraphes"
  - "paragraphes, espacement entre"
  - "espacement entre les paragraphes"
ms.assetid: 7cd2f2ac-0e19-4587-bfb6-7f5b18c9536e
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# Comment&#160;: ajuster l&#39;espacement entre les paragraphes
Cet exemple montre comment ajuster ou éliminer l'espacement entre les paragraphes dans le contenu d'un flux.  
  
 Dans un contenu de flux, l'espace supplémentaire qui apparaît entre les paragraphes est le résultat des marges définies pour ces paragraphes ; ainsi, l'espacement entre les paragraphes peut être contrôlé par l'ajustement des marges sur ces paragraphes.  Pour éliminer l'espacement supplémentaire entre deux paragraphes, définissez les marges pour les paragraphes en leur attribuant la valeur **0**.  Pour obtenir un espacement uniforme entre les paragraphes dans l'ensemble d'un <xref:System.Windows.Documents.FlowDocument>, utilisez les styles pour définir une valeur de marge uniforme pour tous les paragraphes dans le <xref:System.Windows.Documents.FlowDocument>.  
  
 Il est important de noter que les marges de deux paragraphes adjacents se « réduiront » à la plus large des deux marges, au lieu de se doubler.  Si deux paragraphes adjacents ont des marges de 20 et 40 pixels respectivement, l'espace obtenu entre les paragraphes est 40 pixels, la plus large des deux valeurs de marges.  
  
## Exemple  
 L'exemple suivant utilise les styles pour définir les marges pour tous les éléments <xref:System.Windows.Documents.Paragraph> dans un <xref:System.Windows.Documents.FlowDocument> à la valeur **0**, ce qui élimine l'espacement supplémentaire entre les paragraphes dans le <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-xml[BlockSnippets#_ParagraphSpacingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BlockSnippets/CSharp/Window1.xaml#_paragraphspacingxaml)]