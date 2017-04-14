---
title: "Comment&#160;: manipuler les colonnes d&#39;un tableau avec la propri&#233;t&#233; Columns | Microsoft Docs"
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
  - "Columns (propriété)"
  - "documents, manipuler les colonnes d'un tableau"
  - "propriétés, Colonnes, manipuler les colonnes d'un tableau"
  - "tableaux, manipuler des colonnes"
ms.assetid: 3f8884f4-7e1f-456b-be06-fbd3cf469bf3
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: manipuler les colonnes d&#39;un tableau avec la propri&#233;t&#233; Columns
Cet exemple montre quelques\-unes des opérations plus courantes qui peuvent être exécutées sur les colonnes d'une table à travers la propriété <xref:System.Windows.Documents.Table.Columns%2A>.  
  
## Exemple  
 L'exemple suivant crée une table puis utilise la méthode <xref:System.Windows.Documents.TableColumnCollection.Add%2A> pour ajouter des colonnes à la collection <xref:System.Windows.Documents.Table.Columns%2A> de la table.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Add](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_add)]
 [!code-vb[TableSnippets2#_Table_Columns_Add](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_add)]  
  
## Exemple  
 L'exemple suivant insère une nouvelle <xref:System.Windows.Documents.TableColumn>.  La nouvelle colonne est insérée à la position d'index 0, la transformant en première colonne de la table.  
  
> [!NOTE]
>  La collection <xref:System.Windows.Documents.TableColumnCollection> utilise l'indexation standard de base zéro.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Insert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_insert)]
 [!code-vb[TableSnippets2#_Table_Columns_Insert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_insert)]  
  
## Exemple  
 L'exemple suivant accède à quelques propriétés arbitraires sur les colonnes dans la collection <xref:System.Windows.Documents.TableColumnCollection>, en faisant référence à des colonnes particulières par index.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Manip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_manip)]
 [!code-vb[TableSnippets2#_Table_Columns_Manip](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_manip)]  
  
## Exemple  
 L'exemple suivant obtient le nombre de colonnes hébergées actuellement par la table.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Count](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_count)]
 [!code-vb[TableSnippets2#_Table_Columns_Count](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_count)]  
  
## Exemple  
 L'exemple suivant supprime une colonne particulière par référence.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelRef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delref)]
 [!code-vb[TableSnippets2#_Table_Columns_DelRef](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delref)]  
  
## Exemple  
 L'exemple suivant supprime une colonne particulière par index.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delindex)]
 [!code-vb[TableSnippets2#_Table_Columns_DelIndex](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delindex)]  
  
## Exemple  
 L'exemple suivant supprime toutes les colonnes de la collection de colonnes de la table.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Clear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_clear)]
 [!code-vb[TableSnippets2#_Table_Columns_Clear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_clear)]  
  
## Voir aussi  
 [Vue d'ensemble de Table](../../../../docs/framework/wpf/advanced/table-overview.md)   
 [Définir une table avec XAML](../../../../docs/framework/wpf/advanced/how-to-define-a-table-with-xaml.md)   
 [Générer une table par programmation](../../../../docs/framework/wpf/advanced/how-to-build-a-table-programmatically.md)   
 [Manipuler les groupes de lignes d'un tableau avec la propriété RowGroups](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)   
 [Manipuler un FlowDocument avec la propriété Blocks](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)   
 [Manipuler les groupes de lignes d'un tableau avec la propriété RowGroups](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)