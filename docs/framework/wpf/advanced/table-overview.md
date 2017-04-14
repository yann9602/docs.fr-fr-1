---
title: "Vue d&#39;ensemble de Table | Microsoft Docs"
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
  - "documents, tableaux"
  - "éléments de contenu de flux (WPF), Table"
  - "tableaux"
ms.assetid: 5e1105f4-8fc4-473a-ba55-88c8e71386e6
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Vue d&#39;ensemble de Table
<xref:System.Windows.Documents.Table> est un élément de niveau bloc qui prend en charge la présentation basée sur grille du contenu de document dynamique.  La flexibilité de cet élément le rend très utile, mais également plus compliqué à comprendre et à utiliser correctement.  
  
 Cette rubrique contient les sections suivantes.  
  
-   [Concepts de base d'une table](#table_basics)  
  
-   [Comment une table est\-elle différente d'une grille ?](#table_vs_Grid)  
  
-   [Structure de base d'une table](#basic_table_structure)  
  
-   [Relation contenant\-contenu d'une table](#table_containment)  
  
-   [Groupements de lignes](#row_groupings)  
  
-   [Priorité de rendu d'arrière\-plan](#rednering_precedence)  
  
-   [Répartition des lignes ou colonnes](#spanning_rows_or_columns)  
  
-   [Génération d'une table avec du code](#building_a_table_with_code)  
  
-   [Rubriques connexes](#see_also)  
  
<a name="table_basics"></a>   
## Concepts de base d'une table  
  
<a name="table_vs_Grid"></a>   
### Comment une table est\-elle différente d'une grille ?  
 <xref:System.Windows.Documents.Table> et <xref:System.Windows.Controls.Grid> partagent des fonctionnalités communes, mais chacun d'eux est plus adapté à des scénarios différents.  <xref:System.Windows.Documents.Table> est conçu pour être utilisé au sein d'un contenu de flux \(consultez [Vue d'ensemble des documents dynamiques](../../../../docs/framework/wpf/advanced/flow-document-overview.md) pour plus d'informations sur le contenu de flux\).  Les grilles fonctionnent de manière optimale dans les formulaires \(en général n'importe où en dehors d'un contenu de flux\).  Dans un <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> prend en charge les comportements de contenu tels que la pagination, la gestion du rendu des colonnes et la sélection de contenu, tandis que <xref:System.Windows.Controls.Grid> ne le fait pas.  <xref:System.Windows.Controls.Grid> fonctionne en revanche de manière optimale en dehors d'un <xref:System.Windows.Documents.FlowDocument> pour de nombreuses raisons, dont le fait que <xref:System.Windows.Controls.Grid> ajoute des éléments basés sur un index de ligne et de colonne, alors que <xref:System.Windows.Documents.Table> ne le fait pas.  L'élément <xref:System.Windows.Controls.Grid> permet la superposition de contenu enfant, où plusieurs éléments peuvent exister dans une même « cellule ». <xref:System.Windows.Documents.Table> ne prend pas en charge la superposition.  Les éléments enfants d'un <xref:System.Windows.Controls.Grid> peuvent être positionnés de manière absolue par rapport à la zone de leurs limites de « cellule ».  <xref:System.Windows.Documents.Table> ne prend pas en charge cette fonctionnalité.  Enfin, une <xref:System.Windows.Controls.Grid> requiert moins de ressources qu'une <xref:System.Windows.Documents.Table>, envisagez donc d'utiliser une <xref:System.Windows.Controls.Grid> pour améliorer les performances.  
  
<a name="basic_table_structure"></a>   
### Structure de base d'une table  
 <xref:System.Windows.Documents.Table> fournit une présentation sous forme de grille qui se compose de colonnes \(représentées par les éléments <xref:System.Windows.Documents.TableColumn>\) et de lignes \(représentées par les éléments <xref:System.Windows.Documents.TableRow>\).  Les éléments <xref:System.Windows.Documents.TableColumn> n'hébergent pas de contenu ; ils définissent simplement les colonnes et les caractéristiques des colonnes.  Les éléments <xref:System.Windows.Documents.TableRow> doivent être hébergés dans un élément <xref:System.Windows.Documents.TableRowGroup> qui définit un groupement de lignes pour la table.  Les éléments <xref:System.Windows.Documents.TableCell>, qui contiennent le contenu réel que la table doit présenter, doivent être hébergés dans un élément <xref:System.Windows.Documents.TableRow>.  <xref:System.Windows.Documents.TableCell> peut uniquement contenir des éléments qui dérivent de <xref:System.Windows.Documents.Block>.  Les éléments enfants valides pour un <xref:System.Windows.Documents.TableCell> incluent :  
  
-   <xref:System.Windows.Documents.BlockUIContainer>  
  
-   <xref:System.Windows.Documents.List>  
  
-   <xref:System.Windows.Documents.Paragraph>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
>  Les éléments <xref:System.Windows.Documents.TableCell> ne peuvent pas héberger directement du contenu de texte.  Pour plus d'informations sur les règles de relation contenant\-contenu pour les éléments de contenu de flux comme <xref:System.Windows.Documents.TableCell>, consultez [Vue d'ensemble des documents dynamiques](../../../../docs/framework/wpf/advanced/flow-document-overview.md).  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Table> est identique à l'élément <xref:System.Windows.Controls.Grid> mais présente davantage de fonctions et, par conséquent, requiert une charge de ressources plus importante.  
  
 L'exemple suivant définit une simple table de 2 x 3 avec [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)].  
  
 [!code-xml[TableSnippets2#_Table_BasicLayout](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 L'illustration suivante montre comment s'affiche cet exemple.  
  
 ![Capture d'écran : affichage d'une table de base](../../../../docs/framework/wpf/advanced/media/basictablerrender.png "BasicTablerRender")  
  
<a name="table_containment"></a>   
### Relation contenant\-contenu d'une table  
 <xref:System.Windows.Documents.Table> dérive de l'élément <xref:System.Windows.Documents.Block> et adhère aux règles communes pour les éléments de niveau <xref:System.Windows.Documents.Block>.  Un élément <xref:System.Windows.Documents.Table> peut être contenu par chacun des éléments suivants :  
  
-   <xref:System.Windows.Documents.FlowDocument>  
  
-   <xref:System.Windows.Documents.TableCell>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.ListViewItem>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Floater>  
  
-   <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### Groupements de lignes  
 L'élément <xref:System.Windows.Documents.TableRowGroup> fournit un moyen de grouper arbitrairement des lignes dans une table; chaque ligne devant appartenir à un groupement de lignes.  Les lignes dans un groupe de lignes partagent souvent un but commun et peuvent avoir le format d'un groupe.  Une utilisation fréquente des groupements de lignes est de séparer des lignes à usage déterminé, telles qu'un titre, un en\-tête et des lignes de pied de page, du contenu principal du tableau.  
  
 L'exemple suivant utilise [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] pour définir une table avec l'en\-tête mis en forme avec des styles et lignes de pied de page.  
  
 [!code-xml[TableSnippets2#_Table_RowGroups](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 L'illustration suivante montre comment s'affiche cet exemple.  
  
 ![Capture d'écran : groupes de lignes de la table](../../../../docs/framework/wpf/advanced/media/table-rowgroups.png "Table\_RowGroups")  
  
<a name="renderning_precedence"></a>   
### Priorité de rendu d'arrière\-plan  
 Les éléments de table sont restitués dans l'ordre suivant \([ordre de plan](GTMT) du plus bas au plus élevé\).  Cet ordre ne peut pas être modifié.  Par exemple, il n'y a aucune propriété "ordre de plan" pour ces éléments que vous puissiez utiliser pour remplacer l'ordre établi.  
  
1.  <xref:System.Windows.Documents.Table>  
  
2.  <xref:System.Windows.Documents.TableColumn>  
  
3.  <xref:System.Windows.Documents.TableRowGroup>  
  
4.  <xref:System.Windows.Documents.TableRow>  
  
5.  <xref:System.Windows.Documents.TableCell>  
  
 Considérez l'exemple suivant, qui définit des couleurs d'arrière\-plan pour chacun de ces éléments dans une table.  
  
 [!code-xml[TableSnippets2#_Table_ZOrder](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 L'illustration suivante montre comment s'affiche cet exemple \(affichage de couleurs d'arrière\-plan uniquement\).  
  
 ![Capture d'écran : ordre de plan de la table](../../../../docs/framework/wpf/advanced/media/table-zorder.png "Table\_ZOrder")  
  
<a name="spanning_rows_or_columns"></a>   
### Répartition des lignes ou colonnes  
 Les cellules de tableau peuvent être configurées pour couvrir plusieurs lignes ou colonnes en utilisant respectivement les attributs <xref:System.Windows.Documents.TableCell.RowSpan%2A> ou <xref:System.Windows.Documents.TableCell.ColumnSpan%2A>.  
  
 Considérez l'exemple suivant, dans lequel une cellule couvre trois colonnes.  
  
 [!code-xml[TableSnippets2#_Table_ColumnSpan](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 L'illustration suivante montre comment s'affiche cet exemple.  
  
 ![Capture d'écran : cellule s'étendant sur les trois colonnes](../../../../docs/framework/wpf/advanced/media/table-columnspan.png "Table\_ColumnSpan")  
  
<a name="building_a_table_with_code"></a>   
## Génération d'une table avec du code  
 Les exemples suivants indiquent comment créer un <xref:System.Windows.Documents.Table> par programme et le remplir avec le contenu.  Le contenu de la table est réparti en cinq lignes \(représentées par les objets <xref:System.Windows.Documents.TableRow> contenus dans un objet <xref:System.Windows.Documents.Table.RowGroups%2A>\) et six colonnes \(représentées par les objets <xref:System.Windows.Documents.TableColumn>\).  Les lignes sont utilisées à différentes fins de présentation, y compris une ligne de titre prévue pour intituler la table entière, une ligne d'en\-tête pour décrire les colonnes de données dans la table et une ligne de pied de page avec les informations de résumé.  Notez que les notions de lignes de « titre », d'« en\-tête » et de « pied de page » ne sont pas inhérentes à la table ; ce sont simplement des lignes présentant des caractéristiques différentes.  Les cellules de tableau contiennent le contenu réel, qui peut être composé de texte, d'images ou de presque tout autre élément [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].  
  
 En premier lieu, un <xref:System.Windows.Documents.FlowDocument> est créé pour héberger la <xref:System.Windows.Documents.Table> et une nouvelle <xref:System.Windows.Documents.Table> est créée et ajoutée au contenu du <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[TableSnippets#_TableCreate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 Ensuite, six objets <xref:System.Windows.Documents.TableColumn> sont créés et ajoutés à la collection <xref:System.Windows.Documents.Table.Columns%2A> de la table, avec l'application de quelques mises en forme.  
  
> [!NOTE]
>  Notez que la collection <xref:System.Windows.Documents.Table.Columns%2A> de la table utilise une indexation standard commençant par zéro.  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 Ensuite, une ligne de titre est créée et ajoutée à la table avec l'application de quelques mises en forme.  La ligne de titre contient une cellule unique qui couvre les six colonnes de la table.  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 Ensuite, une ligne d'en\-tête est créée et ajoutée à la table, et les cellules dans la ligne d'en\-tête sont créées et sont remplies avec le contenu.  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 Ensuite, une ligne pour les données est créée et ajoutée à la table, et les cellules dans cette ligne sont créées et remplies avec le contenu.  La génération de cette ligne est semblable à la génération de la ligne d'en\-tête, avec l'application d'une mise en forme légèrement différente.  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 Enfin, une ligne de pied de page est créée, ajoutée et mise en forme.  Comme la ligne de titre, le pied de page contient une cellule unique qui couvre les six colonnes de la table.  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## Voir aussi  
 [Vue d'ensemble des documents dynamiques](../../../../docs/framework/wpf/advanced/flow-document-overview.md)   
 [Définir une table avec XAML](../../../../docs/framework/wpf/advanced/how-to-define-a-table-with-xaml.md)   
 [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [Utiliser les éléments de contenu de flux](../../../../docs/framework/wpf/advanced/how-to-use-flow-content-elements.md)