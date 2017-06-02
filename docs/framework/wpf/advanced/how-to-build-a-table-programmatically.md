---
title: "Comment&#160;: g&#233;n&#233;rer une table par programmation | Microsoft Docs"
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
  - "créer, tables (par programmation)"
  - "documents, créer des tables par programmation"
  - "tableaux, créer par programmation"
ms.assetid: e3ca88f3-6e94-4b61-82fc-42104c10b761
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: g&#233;n&#233;rer une table par programmation
Les exemples suivants indiquent comment créer un <xref:System.Windows.Documents.Table> par programme et le remplir avec le contenu.  Le contenu de la table est réparti en cinq lignes \(représentées par les objets <xref:System.Windows.Documents.TableRow> contenus dans un objet <xref:System.Windows.Documents.Table.RowGroups%2A>\) et six colonnes \(représentées par les objets <xref:System.Windows.Documents.TableColumn>\).  Les lignes sont utilisées à différentes fins de présentation, y compris une ligne de titre prévue pour intituler la table entière, une ligne d'en\-tête pour décrire les colonnes de données dans la table et une ligne de pied de page avec les informations de résumé.  Notez que les notions de lignes de « titre », d'« en\-tête » et de « pied de page » ne sont pas inhérentes à la table ; ce sont simplement des lignes présentant des caractéristiques différentes.  Les cellules de tableau contiennent le contenu réel, qui peut être composé de texte, d'images ou de presque tout autre élément [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].  
  
## Exemple  
 En premier lieu, un <xref:System.Windows.Documents.FlowDocument> est créé pour héberger la <xref:System.Windows.Documents.Table> et une nouvelle <xref:System.Windows.Documents.Table> est créée et ajoutée au contenu du <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[TableSnippets#_TableCreate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
## Exemple  
 Ensuite, six objets <xref:System.Windows.Documents.TableColumn> sont créés et ajoutés à la collection <xref:System.Windows.Documents.Table.Columns%2A> de la table, avec l'application de quelques mises en forme.  
  
> [!NOTE]
>  Notez que la collection <xref:System.Windows.Documents.Table.Columns%2A> de la table utilise une indexation standard commençant par zéro.  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
## Exemple  
 Ensuite, une ligne de titre est créée et ajoutée à la table avec l'application de quelques mises en forme.  La ligne de titre contient une cellule unique qui couvre les six colonnes de la table.  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
## Exemple  
 Ensuite, une ligne d'en\-tête est créée et ajoutée à la table, et les cellules dans la ligne d'en\-tête sont créées et sont remplies avec le contenu.  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
## Exemple  
 Ensuite, une ligne pour les données est créée et ajoutée à la table, et les cellules dans cette ligne sont créées et remplies avec le contenu.  La génération de cette ligne est semblable à la génération de la ligne d'en\-tête, avec l'application d'une mise en forme légèrement différente.  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
## Exemple  
 Enfin, une ligne de pied de page est créée, ajoutée et mise en forme.  Comme la ligne de titre, le pied de page contient une cellule unique qui couvre les six colonnes de la table.  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## Voir aussi  
 [Vue d'ensemble de Table](../../../../docs/framework/wpf/advanced/table-overview.md)