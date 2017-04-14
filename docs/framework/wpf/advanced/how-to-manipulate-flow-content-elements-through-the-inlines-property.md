---
title: "Comment&#160;: manipuler des &#233;l&#233;ments de contenu de flux avec la propri&#233;t&#233; Inlines | Microsoft Docs"
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
  - "documents, manipuler des éléments de contenu de flux à l'aide de la propriété Inlines"
  - "éléments de contenu de flux, manipuler à l'aide de la propriété Inlines"
  - "Inlines (propriété), manipuler des éléments de contenu de flux"
  - "propriétés, Inlines, manipuler des éléments de contenu de flux"
ms.assetid: 510780d2-3da1-4360-8763-7054bda22ea3
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: manipuler des &#233;l&#233;ments de contenu de flux avec la propri&#233;t&#233; Inlines
Ces exemples montrent quelques\-unes des opérations les plus courantes qui peuvent être exécutées sur les éléments de contenu de flux inline \(et conteneurs de tels éléments, tels que <xref:System.Windows.Controls.TextBlock>\) à travers la propriété **Inlines**.  Cette propriété est utilisée pour ajouter et supprimer des éléments de <xref:System.Windows.Documents.InlineCollection>.  Les éléments de contenu de flux qui caractérisent une propriété **Inlines** incluent :  
  
-   <xref:System.Windows.Documents.Bold>  
  
-   <xref:System.Windows.Documents.Hyperlink>  
  
-   <xref:System.Windows.Documents.Italic>  
  
-   <xref:System.Windows.Documents.Paragraph>  
  
-   <xref:System.Windows.Documents.Span>  
  
-   <xref:System.Windows.Documents.Underline>  
  
 Il arrive que ces exemples utilisent <xref:System.Windows.Documents.Span> comme élément de contenu de flux, mais ces techniques sont applicable à tous les éléments ou contrôles qui hébergent une collection <xref:System.Windows.Documents.InlineCollection>.  
  
## Exemple  
 L'exemple suivant crée un objet <xref:System.Windows.Documents.Span>, puis utilise la méthode **Add** pour ajouter deux exécutions de texte comme contenu enfant du <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
## Exemple  
 L'exemple suivant crée un élément <xref:System.Windows.Documents.Run> et l'insère au début de <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
## Exemple  
 L'exemple suivant obtient le nombre d'éléments <xref:System.Windows.Documents.Inline> de niveau supérieur contenus dans le <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesCount](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinescount)]
 [!code-vb[SpanSnippets#_SpanInlinesCount](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinescount)]  
  
## Exemple  
 L'exemple suivant supprime le dernier élément <xref:System.Windows.Documents.Inline> de <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
## Exemple  
 L'exemple suivant efface tout le contenu \(éléments <xref:System.Windows.Documents.Inline> de <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
## Voir aussi  
 <xref:System.Windows.Documents.BlockCollection>   
 <xref:System.Windows.Documents.InlineCollection>   
 <xref:System.Windows.Documents.ListItemCollection>   
 [Vue d'ensemble des documents dynamiques](../../../../docs/framework/wpf/advanced/flow-document-overview.md)   
 [Manipuler un FlowDocument avec la propriété Blocks](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)   
 [Manipuler les colonnes d'un tableau avec la propriété Columns](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)   
 [Manipuler les groupes de lignes d'un tableau avec la propriété RowGroups](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)