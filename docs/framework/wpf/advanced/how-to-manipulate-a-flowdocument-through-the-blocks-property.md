---
title: "Comment&#160;: manipuler un FlowDocument avec la propri&#233;t&#233; Blocks | Microsoft Docs"
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
  - "Blocks (propriété), manipuler des FlowDocuments"
  - "documents, manipuler des FlowDocuments à l'aide de la propriété Blocks"
  - "FlowDocuments, manipuler à l'aide de la propriété Blocks"
  - "propriétés, Blocs, manipuler des FlowDocuments"
ms.assetid: cbb7291e-3f1b-433e-9e16-f4d93ced14e8
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: manipuler un FlowDocument avec la propri&#233;t&#233; Blocks
Cet exemple montre quelques\-unes des opérations courantes qui peuvent être exécutées sur un <xref:System.Windows.Documents.FlowDocument> par le biais de la propriété <xref:System.Windows.Documents.FlowDocument.Blocks%2A>.  
  
## Exemple  
 L'exemple suivant crée un nouveau <xref:System.Windows.Documents.FlowDocument> puis ajoute un nouvel élément <xref:System.Windows.Documents.Paragraph> au <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksadd)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksadd)]  
  
## Exemple  
 L'exemple suivant crée un élément <xref:System.Windows.Documents.Paragraph> et l'insère au début de <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksInsert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksinsert)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksInsert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksinsert)]  
  
## Exemple  
 L'exemple suivant obtient le nombre d'éléments <xref:System.Windows.Documents.Block> de niveau supérieur contenus dans le <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksCount](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblockscount)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksCount](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblockscount)]  
  
## Exemple  
 L'exemple suivant supprime le dernier élément <xref:System.Windows.Documents.Block> de <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksremovelast)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksremovelast)]  
  
## Exemple  
 L'exemple suivant efface tout le contenu \(éléments <xref:System.Windows.Documents.Block> de <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksclear)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksclear)]  
  
## Voir aussi  
 [Manipuler les groupes de lignes d'un tableau avec la propriété RowGroups](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)   
 [Manipuler les colonnes d'un tableau avec la propriété Columns](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)   
 [Manipuler les groupes de lignes d'un tableau avec la propriété RowGroups](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)