---
title: "Vue d&#39;ensemble du mod&#232;le de contenu de TextElement | Microsoft Docs"
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
  - "documents, documents dynamiques"
  - "éléments de contenu de flux (WPF), TextElement (modèle de contenu)"
  - "documents dynamiques"
  - "TextElement (modèle de contenu)"
ms.assetid: d0a7791c-b090-438c-812f-b9d009d83ee9
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Vue d&#39;ensemble du mod&#232;le de contenu de TextElement
Cette vue d'ensemble de modèle de contenu décrit le contenu pris en charge pour un <xref:System.Windows.Documents.TextElement>.  La classe <xref:System.Windows.Documents.Paragraph> est un type de <xref:System.Windows.Documents.TextElement>.  Un modèle de contenu décrit les types d'objets\/d'éléments qui peuvent être contenus dans d'autres.  Cette vue d'ensemble résume le modèle de contenu utilisé pour les objets dérivés de <xref:System.Windows.Documents.TextElement>.  Pour plus d'informations, consultez [Vue d'ensemble des documents dynamiques](../../../../docs/framework/wpf/advanced/flow-document-overview.md).  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="text_element_classes"></a>   
## Diagramme de modèle de contenu  
 Le diagramme suivant résume le modèle de contenu pour les classes dérivées de <xref:System.Windows.Documents.TextElement> ainsi que la façon dont les autres classes non\-`TextElement` s'adaptent à ce modèle.  
  
 ![Diagramme : schéma de relation contenant&#45;contenu du flux](../../../../docs/framework/wpf/advanced/media/flow-content-schema.png "Flow\_Content\_Schema")  
  
 Comme vous pouvez le constater dans le diagramme précédent, les enfants autorisés pour un élément ne sont pas nécessairement déterminés par le fait qu'une classe dérive de la classe <xref:System.Windows.Documents.Block> ou d'une classe <xref:System.Windows.Documents.Inline>.  Par exemple, une <xref:System.Windows.Documents.Span> \(une classe dérivée <xref:System.Windows.Documents.Inline>\) peut uniquement avoir des éléments enfants <xref:System.Windows.Documents.Inline>, mais une <xref:System.Windows.Documents.Figure> \(également une classe dérivée <xref:System.Windows.Documents.Inline>\) peut uniquement avoir des éléments enfants <xref:System.Windows.Documents.Block>.  Par conséquent, ce schéma est très utile pour savoir rapidement quel élément peut être contenu dans un autre.  Par exemple, utilisons le schéma pour déterminer comment construire le contenu dynamique d'un <xref:System.Windows.Controls.RichTextBox>.  
  
1.  Un <xref:System.Windows.Controls.RichTextBox> doit contenir un<xref:System.Windows.Documents.FlowDocument> qui doit à son tour contenir un objet dérivé de <xref:System.Windows.Documents.Block>.  Voici le segment correspondant extrait du diagramme précédent.  
  
     ![Diagramme : règles de relation contenant&#45;contenu RichtextBox](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough1.png "Flow\_Ovw\_SchemaWalkThrough1")  
  
     À ce stade, le balisage peut ressembler à ceci.  
  
     [!code-xml[FlowOvwSnippets_snip#SchemaWalkThrough1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2.  D'après le schéma, plusieurs éléments <xref:System.Windows.Documents.Block> peuvent être sélectionnés, notamment <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.List> et <xref:System.Windows.Documents.BlockUIContainer> \(voir classes dérivées de Block dans le diagramme précédent\).  Supposons que nous voulons l'élément <xref:System.Windows.Documents.Table>.  Le diagramme précédent indique qu'un <xref:System.Windows.Documents.Table> contient un <xref:System.Windows.Documents.TableRowGroup> contenant des éléments <xref:System.Windows.Documents.TableRow>, qui contiennent des éléments <xref:System.Windows.Documents.TableCell> contenant eux\-mêmes un objet dérivé de <xref:System.Windows.Documents.Block>.  Voici le segment correspondant pour <xref:System.Windows.Documents.Table>, extrait du diagramme précédent.  
  
     ![Diagramme : schéma parent&#47;enfant pour Table](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough2.png "Flow\_Ovw\_SchemaWalkThrough2")  
  
     Voici le balisage correspondant.  
  
     [!code-xml[FlowOvwSnippets_snip#SchemaWalkThrough2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3.  Ici encore, un ou plusieurs éléments <xref:System.Windows.Documents.Block> sont requis sous <xref:System.Windows.Documents.TableCell>.  Pour simplifier, insérons du texte dans la cellule.  Pour cela, nous pouvons utiliser un <xref:System.Windows.Documents.Paragraph> avec un élément <xref:System.Windows.Documents.Run>.  Voici les segments correspondants extraits du diagramme ; ils indiquent qu'un <xref:System.Windows.Documents.Paragraph> peut contenir un élément <xref:System.Windows.Documents.Inline> et qu'un <xref:System.Windows.Documents.Run> \(élément <xref:System.Windows.Documents.Inline>\) peut uniquement contenir du texte brut.  
  
     ![Diagramme : schéma parent&#47;enfant pour Paragraph](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough3.png "Flow\_Ovw\_SchemaWalkThrough3")  
  
     ![Diagramme : schéma parent&#47;enfant pour Run](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough4.png "Flow\_Ovw\_SchemaWalkThrough4")  
  
 Voici le balisage de l'exemple complet.  
  
 [!code-xml[FlowOvwSnippets_snip#SchemaExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>   
## Utilisation du contenu de TextElement par programme  
 Le contenu de <xref:System.Windows.Documents.TextElement> est composé de collections. La manipulation par programme du contenu d'objets <xref:System.Windows.Documents.TextElement> se fait en travaillant avec ces collections.  Il existe trois collections différentes utilisées par les classes dérivées <xref:System.Windows.Documents.TextElement> :  
  
-   <xref:System.Windows.Documents.InlineCollection> : représente une collection d'éléments <xref:System.Windows.Documents.Inline>.  <xref:System.Windows.Documents.InlineCollection> définit le contenu enfant autorisé des éléments <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Span> et <xref:System.Windows.Controls.TextBlock>.  
  
-   <xref:System.Windows.Documents.BlockCollection> : représente une collection d'éléments <xref:System.Windows.Documents.Block>.  <xref:System.Windows.Documents.BlockCollection> définit le contenu enfant autorisé des éléments <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.TableCell>, <xref:System.Windows.Documents.Floater> et <xref:System.Windows.Documents.Figure>.  
  
-   <xref:System.Windows.Documents.ListItemCollection> : un élément de contenu de flux qui représente un élément de contenu particulier dans une <xref:System.Windows.Documents.List> ordonnée ou non ordonnée.  
  
 Vous pouvez manipuler \(ajouter ou supprimer des éléments\) ces collections à l'aide des propriétés **Inlines**, **Blocks** et **ListItems** correspondantes.  Les exemples suivants montrent comment manipuler le contenu d'un Span à l'aide de la propriété **Inlines**.  
  
> [!NOTE]
>  La table utilise plusieurs collections pour manipuler son contenu, mais elles ne sont pas abordées ici.  Pour plus d'informations, consultez [Vue d'ensemble de Table](../../../../docs/framework/wpf/advanced/table-overview.md).  
  
 L'exemple suivant crée un objet <xref:System.Windows.Documents.Span>, puis utilise la méthode `Add` pour ajouter deux exécutions de texte comme contenu enfant du <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 L'exemple suivant crée un élément <xref:System.Windows.Documents.Run> et l'insère au début de <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 L'exemple suivant supprime le dernier élément <xref:System.Windows.Documents.Inline> de <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 L'exemple suivant efface tout le contenu \(éléments <xref:System.Windows.Documents.Inline> de <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>   
## Types partageant ce modèle de contenu  
 Les types suivants héritent de la classe <xref:System.Windows.Documents.TextElement> et peuvent être utilisés pour afficher le contenu décrit dans cette vue d'ensemble.  
  
 <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.  
  
 Notez que cette liste inclut uniquement les types non abstraits distribués avec le [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)].  Vous pouvez utiliser d'autres types qui héritent de <xref:System.Windows.Documents.TextElement>.  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>   
## Types qui peuvent contenir des objets TextElement  
 Consultez [Modèle de contenu WPF](../../../../docs/framework/wpf/controls/wpf-content-model.md).  
  
## Voir aussi  
 [Manipuler un FlowDocument avec la propriété Blocks](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)   
 [Manipuler des éléments de contenu de flux avec la propriété Blocks](../../../../docs/framework/wpf/advanced/how-to-manipulate-flow-content-elements-through-the-blocks-property.md)   
 [Manipuler un FlowDocument avec la propriété Blocks](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)   
 [Manipuler les colonnes d'un tableau avec la propriété Columns](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)   
 [Manipuler les groupes de lignes d'un tableau avec la propriété RowGroups](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)