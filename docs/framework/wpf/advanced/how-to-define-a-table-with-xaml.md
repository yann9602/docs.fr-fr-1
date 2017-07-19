---
title: "Comment&#160;: d&#233;finir une table avec XAML | Microsoft Docs"
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
  - "documents, définir des tables avec XAML"
  - "tableaux, définir avec XAML"
  - "XAML, définir des tables"
ms.assetid: 83f2dc58-437e-4cdc-b5dd-0019810c7a85
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# Comment&#160;: d&#233;finir une table avec XAML
L'exemple suivant montre comment définir <xref:System.Windows.Documents.Table> à l'aide de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  L'exemple de tableau a quatre colonnes \(représentées par les éléments <xref:System.Windows.Documents.TableColumn>\) et plusieurs lignes \(représentées par les éléments <xref:System.Windows.Documents.TableRow>\) contenant des données ainsi que des informations pour le titre, l'en\-tête et le pied de page.  Les lignes doivent être contenues dans un élément <xref:System.Windows.Documents.TableRowGroup>.  Chaque ligne du tableau est composée d'une ou de plusieurs cellules \(représentées par les éléments <xref:System.Windows.Documents.TableCell>\).  Le contenu d'une cellule de tableau doit figurer dans un élément <xref:System.Windows.Documents.Block> ; dans ce cas, les éléments <xref:System.Windows.Documents.Paragraph> sont utilisés.  Le tableau héberge également un lien hypertexte \(représenté par l'élément <xref:System.Windows.Documents.Hyperlink>\) dans la ligne du pied de page.  
  
## Exemple  
 [!code-xml[TableSnippetsXAML#_TableXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippetsXAML/CS/Window1.xaml#_tablexaml)]  
  
 La figure suivante illustre le rendu du tableau défini dans cet exemple.  
  
 ![Table affichée.](../../../../docs/framework/wpf/advanced/media/tableeg.png "TableEG")