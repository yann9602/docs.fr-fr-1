---
title: "Vue d&#39;ensemble du contr&#244;le DataGrid (Windows Forms) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DataGrid"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "jeux de données (Windows Forms), lier au contrôle DataGrid"
  - "liaison de données, le contrôle DataGrid"
  - "colonnes (Windows Forms), le contrôle DataGrid"
  - "sources de données, lier au contrôle DataGrid"
  - "tables (Windows Forms), lier au contrôle DataGrid"
  - "Contrôle DataGrid (Windows Forms), liaison de données"
  - "Contrôle DataGrid (Windows Forms), à propos du contrôle DataGrid"
  - "tables parents dans un contrôle DataGrid"
  - "tables (Windows Forms), afficher dans le contrôle DataGrid"
  - "grilles de données, à propos des grilles de données"
  - "tables multiples dans un contrôle DataGrid"
  - "données (Windows Forms), avoir recours"
  - "données (Windows Forms), navigation"
  - "contrôles dépendants, contrôle DataGrid"
  - "contrôles dépendants, DataGrid"
  - "navigation entre tables parents dans un contrôle DataGrid"
  - "tables enfants, contrôle DataGrid"
ms.assetid: 85604bce-bc03-49d9-9030-dda8896c44b1
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# Vue d&#39;ensemble du contr&#244;le DataGrid (Windows Forms)
> [!NOTE]
>  Le <xref:System.Windows.Forms.DataGridView> contrôle remplace et ajoute des fonctionnalités à la <xref:System.Windows.Forms.DataGrid> contrôle ; Toutefois, le <xref:System.Windows.Forms.DataGrid> contrôle est conservé pour la compatibilité descendante et une utilisation future, si vous choisissez. Pour plus d’informations, consultez [différences entre le Windows Forms contrôles DataGridView et DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Windows Forms <xref:System.Windows.Forms.DataGrid> contrôle affiche les données dans une série de lignes et de colonnes. Le cas le plus simple est quand la grille est liée à une source de données avec une seule table ne contenant aucune relation. Dans ce cas, les données apparaissent dans des lignes et des colonnes simples, comme dans une feuille de calcul. Pour plus d’informations sur la liaison de données à d’autres contrôles, consultez [liaison de données et Windows Forms](../../../../docs/framework/winforms/data-binding-and-windows-forms.md).  
  
 Si le <xref:System.Windows.Forms.DataGrid> est lié aux données avec plusieurs tables connexes, et que la navigation est activée dans la grille, la grille affiche des développeurs dans chaque ligne. Avec un expander, l’utilisateur peut passer d’une table parente à une table enfant. Un clic sur un nœud affiche la table enfant et un clic sur un bouton Précédent affiche la table parente d'origine. De cette manière, la grille affiche les relations hiérarchiques entre les tables.  
  
 La capture d'écran suivante montre un contrôle DataGrid lié à des données avec plusieurs tables.  
  
 ![Un contrôle DataGrid lié aux données par plusieurs tables](../../../../docs/framework/winforms/controls/media/vbcontrol1.gif "vbControl1")  
Contrôle DataGrid lié aux données par plusieurs tables  
  
 Le <xref:System.Windows.Forms.DataGrid> peut fournir une interface utilisateur pour un jeu de données, la navigation entre les tables associées et riche mise en forme et les fonctionnalités d’édition.  
  
 L'affichage et la manipulation des données sont deux fonctions distinctes : le contrôle gère l'interface utilisateur, tandis que les mises à jour des données sont gérées par l'architecture de liaison de données Windows Forms et par des fournisseurs de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Ainsi, plusieurs contrôles liés à la même source de données resteront synchronisés.  
  
> [!NOTE]
>  Si vous êtes familiarisé avec le contrôle DataGrid dans Visual Basic 6.0, vous trouverez des différences significatives dans les Windows Forms <xref:System.Windows.Forms.DataGrid> contrôle.  
  
 Lorsque la grille est liée à un <xref:System.Data.DataSet>, les colonnes et les lignes sont automatiquement créés, mis en forme et remplies. Pour plus d'informations, consultez [Data Binding and Windows Forms](../../../../docs/framework/winforms/data-binding-and-windows-forms.md). Après la génération de la <xref:System.Windows.Forms.DataGrid> contrôle, vous pouvez ajouter, supprimer, réorganiser et mettre en forme les colonnes et lignes en fonction de vos besoins.  
  
## <a name="binding-data-to-the-control"></a>Liaison de données au contrôle  
 Pour le <xref:System.Windows.Forms.DataGrid> contrôler pour fonctionner, il doit être lié à une source de données à l’aide de la <xref:System.Windows.Forms.DataGrid.DataSource%2A> et <xref:System.Windows.Forms.DataGrid.DataMember%2A> propriétés au moment du design ou le <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> méthode au moment de l’exécution. Cette liaison pointe le <xref:System.Windows.Forms.DataGrid> à un objet de source de données instancié, tel un <xref:System.Data.DataSet> ou <xref:System.Data.DataTable>). Le <xref:System.Windows.Forms.DataGrid> contrôle affiche les résultats des actions qui sont effectuées sur les données. La plupart des actions spécifiques aux données ne sont pas effectuées par le <xref:System.Windows.Forms.DataGrid> , mais plutôt via la source de données.  
  
 Si les données du DataSet lié sont mis à jour via un mécanisme quelconque, le <xref:System.Windows.Forms.DataGrid> contrôle reflète les modifications. Si la grille de données et ses styles de table et de colonne ont le `ReadOnly` propriété `false`, les données dans le jeu de données peuvent être mis à jour via le <xref:System.Windows.Forms.DataGrid> contrôle.  
  
 Une seule table peut être affichée dans le <xref:System.Windows.Forms.DataGrid> à la fois. Si une relation parent-enfant est définie entre les tables, l’utilisateur peut déplacer entre les tables connexes pour sélectionner la table à afficher dans le <xref:System.Windows.Forms.DataGrid> contrôle. Pour plus d’informations sur la liaison d’un <xref:System.Windows.Forms.DataGrid> le contrôle à une [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] source de données au moment du design ou au moment de l’exécution, consultez [Comment : lier le contrôle DataGrid Windows Forms à une Source de données](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
 Sources de données valides pour le <xref:System.Windows.Forms.DataGrid> incluent :  
  
-   <xref:System.Data.DataTable> (classe)  
  
-   <xref:System.Data.DataView> (classe)  
  
-   <xref:System.Data.DataSet> (classe)  
  
-   <xref:System.Data.DataViewManager> (classe)  
  
 Si votre source est un dataset, celui-ci peut être un objet dans le formulaire ou un objet passé au formulaire par un service web XML. Vous pouvez lier à des datasets typés ou non typés.  
  
 Vous pouvez également lier un <xref:System.Windows.Forms.DataGrid> le contrôle à des structures supplémentaires si les objets dans la structure, tels que les éléments dans un tableau, exposent des propriétés publiques. La grille affichera toutes les propriétés publiques des éléments de la structure. Par exemple, si vous liez le <xref:System.Windows.Forms.DataGrid> objets de contrôle à un tableau de client, la grille affichera toutes les propriétés publiques de ces objets. Dans certains cas, cela signifie que bien que vous puissiez lier à la structure, la structure de liaison résultante peut ne pas avoir d'application pratique. Par exemple, vous pouvez lier à un tableau d'entiers, mais comme le type de données `Integer` ne prend pas en charge les propriétés publiques, la grille ne pourra pas afficher de données.  
  
 Vous pouvez lier aux structures suivantes si leurs éléments exposent des propriétés publiques :  
  
-   Tout composant qui implémente le <xref:System.Collections.IList> interface. Cela comprend les tableaux unidimensionnels.  
  
-   Tout composant qui implémente le <xref:System.ComponentModel.IListSource> interface.  
  
-   Tout composant qui implémente le <xref:System.ComponentModel.IBindingList> interface.  
  
 Pour plus d’informations sur les sources de données possibles, consultez la page [des Sources de données prises en charge par les Windows Forms](../../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md).  
  
## <a name="grid-display"></a>Affichage de la grille  
 Une utilisation courante de la <xref:System.Windows.Forms.DataGrid> contrôle consiste à afficher une table de données à partir d’un jeu de données. Toutefois, ce contrôle peut également servir à afficher plusieurs tables, y compris des tables associées. L'affichage de la grille est ajustée automatiquement en fonction de la source de données. Le tableau suivant montre ce qui est affiché pour différentes configurations.  
  
|Contenu du dataset|Ce qui est affiché|  
|--------------------------|-----------------------|  
|Une seule table.|La table est affichée dans une grille.|  
|Plusieurs tables.|La grille peut afficher une arborescence à laquelle les utilisateurs peuvent accéder pour trouver la table qu'ils souhaitent afficher.|  
|Plusieurs tables associées.|La grille peut afficher une arborescence dans laquelle sélectionner des tables ou vous pouvez spécifier que la grille affiche la table parente. Les enregistrements dans la table parente permettent aux utilisateurs d'accéder aux lignes enfants associées.|  
  
> [!NOTE]
>  Tables dans un groupe de données sont liées à l’aide un <xref:System.Data.DataRelation>.  Consultez également [lien hypertexte « http://msdn.microsoft.com/library/dbwcse3d (110) » relations dans les groupes de données](http://msdn.microsoft.com/library/dbwcse3d\(v=vs.110\)) ou [relations dans les groupes de données](http://msdn.microsoft.com/library/dbwcse3d\(v=vs.120\)).  
  
 Lors de la <xref:System.Windows.Forms.DataGrid> contrôle affiche une table et la <xref:System.Windows.Forms.DataGrid.AllowSorting%2A> est définie sur `true`, pouvez retrier les données en cliquant sur les en-têtes de colonne. L'utilisateur peut aussi ajouter des lignes et modifier des cellules.  
  
 Les relations entre un ensemble de tables sont présentées aux utilisateurs à l'aide d'une structure de navigation parent/enfant. Les tables parentes constituent le niveau de données le plus élevé et les tables enfants sont celles qui sont dérivées des différentes entrées dans les tables parentes. Des expanders sont affichés sur chaque ligne parente qui contient une table enfant. Un clic sur un expander génère une liste de liens web vers les tables enfants. Quand l'utilisateur sélectionne un lien, la table enfant est affichée. En cliquant sur l’icône Afficher/masquer les lignes parentes (![icône Afficher/masquer les lignes parentes](../../../../docs/framework/winforms/controls/media/vbicon.png "vbIcon")) masque les informations concernant la table parente ou les fait réapparaître si l’utilisateur a précédemment masquées. L'utilisateur peut cliquer sur un bouton Précédent pour revenir à la table affichée précédemment.  
  
## <a name="columns-and-rows"></a>Colonnes et lignes  
 Le <xref:System.Windows.Forms.DataGrid> se compose d’une collection de <xref:System.Windows.Forms.DataGridTableStyle> les objets contenus dans le <xref:System.Windows.Forms.DataGrid> du contrôle <xref:System.Windows.Forms.DataGrid.TableStyles%2A> propriété. Un style de table peut contenir une collection de <xref:System.Windows.Forms.DataGridColumnStyle> objets contenus dans le <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> propriétés de la <xref:System.Windows.Forms.DataGridTableStyle>... Vous pouvez modifier le <xref:System.Windows.Forms.DataGrid.TableStyles%2A> et <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> propriétés à l’aide des éditeurs de collections accédés via les **propriétés** fenêtre.  
  
 N’importe quel <xref:System.Windows.Forms.DataGridTableStyle> associé à la <xref:System.Windows.Forms.DataGrid> contrôle est accessible via la <xref:System.Windows.Forms.GridTableStylesCollection>. Le <xref:System.Windows.Forms.GridTableStylesCollection> peuvent être modifiées dans le concepteur avec le <xref:System.Windows.Forms.DataGridTableStyle> éditeur de collection, ou par programmation via la <xref:System.Windows.Forms.DataGrid> du contrôle <xref:System.Windows.Forms.DataGrid.TableStyles%2A> propriété.  
  
 ![Objets inclus dans le contrôle DataGrid](../../../../docs/framework/winforms/controls/media/vbcolumns1.png "vbColumns1")  
L'illustration suivante montre les objets inclus dans le contrôle DataGrid.  
  
 Styles de table et de colonne sont synchronisés avec <xref:System.Data.DataTable> objets et <xref:System.Data.DataColumn> en définissant leur `MappingName` propriétés approprié <xref:System.Data.DataTable.TableName%2A> et <xref:System.Data.DataColumn.ColumnName%2A> propriétés. Lorsqu’un <xref:System.Windows.Forms.DataGridTableStyle> qui n’a aucune colonne styles est ajouté à un <xref:System.Windows.Forms.DataGrid> contrôle lié à une source de données valide et la <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> de ce style de table est définie sur valide <xref:System.Data.DataTable.TableName%2A> propriété, une collection de <xref:System.Windows.Forms.DataGridColumnStyle> objets est créée pour ce style de table. Pour chaque <xref:System.Data.DataColumn> trouvé dans le <xref:System.Data.DataTable.Columns%2A> collection de la <xref:System.Data.DataTable>, correspondante <xref:System.Windows.Forms.DataGridColumnStyle> est ajouté à la <xref:System.Windows.Forms.GridColumnStylesCollection>. <xref:System.Windows.Forms.GridColumnStylesCollection> est accessible via la <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> propriétés de la <xref:System.Windows.Forms.DataGridTableStyle>. Colonnes peuvent être ajoutées ou supprimées de la grille à l’aide de la <xref:System.Windows.Forms.GridColumnStylesCollection.Add%2A> ou <xref:System.Windows.Forms.GridColumnStylesCollection.Remove%2A> méthode sur le <xref:System.Windows.Forms.GridColumnStylesCollection>. Pour plus d’informations, consultez [Comment : ajouter des Tables et des colonnes au contrôle DataGrid Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md) et [Comment : supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md).  
  
 Une collection de types de colonnes étend la <xref:System.Windows.Forms.DataGridColumnStyle> classe riche mise en forme et des fonctionnalités d’édition. Tous les types de colonne héritent de la <xref:System.Windows.Forms.DataGridColumnStyle> classe de base. La classe créée dépend le <xref:System.Data.DataColumn.DataType%2A> propriété de la <xref:System.Data.DataColumn> à partir de laquelle le <xref:System.Web.UI.WebControls.DataGridColumn> est basé. Par exemple, un <xref:System.Data.DataColumn> qui a son <xref:System.Data.DataColumn.DataType%2A> propriété <xref:System.Boolean> sera associé le <xref:System.Windows.Forms.DataGridBoolColumn>. Le tableau suivant décrit chacun de ces types de colonnes.  
  
|Type de colonne|Description|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.DataGridTextBoxColumn>|Accepte et affiche les données sous forme de chaînes mises en forme ou non mises en forme. Les fonctionnalités d’édition sont identiques en cas de modification des données dans une simple <xref:System.Windows.Forms.TextBox>. Hérite de <xref:System.Windows.Forms.DataGridColumnStyle>.|  
|<xref:System.Windows.Forms.DataGridBoolColumn>|Accepte et affiche des valeurs `true`, `false` et null. Hérite de <xref:System.Windows.Forms.DataGridColumnStyle>.|  
  
 Un double-clic sur le bord droit d'une colonne redimensionne la colonne pour afficher sa légende complète et son entrée la plus large.  
  
## <a name="table-styles-and-column-styles"></a>Styles de table et de colonne  
 Dès que vous avez établi le format par défaut de la <xref:System.Windows.Forms.DataGrid> contrôle, vous pouvez personnaliser les couleurs qui seront utilisées lors de certaines tables sont affichées dans la grille de données.  
  
 Pour cela, créer des instances de la <xref:System.Windows.Forms.DataGridTableStyle> classe. Styles de table spécifient la mise en forme de tables spécifiques, différente de la mise en forme par défaut de la <xref:System.Windows.Forms.DataGrid> contrôle lui-même. Vous ne pouvez définir qu'un seul style de table à la fois pour chaque table.  
  
 Parfois, vous souhaiterez donner à une colonne spécifique une apparence différente des autres colonnes d'une table de données particulière. Vous pouvez créer un jeu personnalisé de styles de colonne à l’aide de la <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> propriété.  
  
 Les styles de colonne sont liés aux colonnes d'un dataset tout comme les styles de table sont liés aux tables de données. Vous ne pouvez définir qu'un seul style de colonne à la fois pour chaque colonne dans un style de table particulier. Cette relation est définie dans la colonne <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> propriété.  
  
 Si vous avez créé un style de table sans y ajouter de style de colonne, [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] ajoute des styles de colonne par défaut quand le formulaire et la grille sont créés au moment de l'exécution. En revanche, si vous avez créé un style de table et que vous y avez ajouté des styles de colonne, [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] ne crée pas de style de colonne. De plus, vous devrez définir des styles de colonne et les assigner avec le nom de mappage pour afficher les colonnes de votre choix dans la grille.  
  
 Étant donné que vous spécifiez les colonnes à inclure dans la grille de données en leur assignant un style de colonne et qu'aucun style de colonne n'a été assigné aux colonnes, vous pouvez inclure dans le dataset des colonnes de données qui ne sont pas affichées dans la grille. Toutefois, comme la colonne de données est incluse dans le dataset, vous pouvez modifier par programmation les données qui ne sont pas affichées.  
  
> [!NOTE]
>  En général, vous devez créer des styles de colonne et les ajouter à la collection de styles de colonne avant d'ajouter des styles de tableau à la collection de styles de table. Quand vous ajoutez un style de table vide à la collection, des styles de colonne sont générés automatiquement pour vous. Par conséquent, une exception sera levée si vous essayez d’ajouter de nouveaux styles de colonne par duplication <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> valeurs à la collection de styles de colonne.  
>   
>  Parfois, vous souhaiterez simplement ajuster une colonne parmi d'autres ; par exemple, il se peut que le dataset contienne 50 colonnes et que vous n'ayez besoin que de 49 d'entre elles. Dans ce cas, il est plus facile d'importer les 50 colonnes et de supprimer l'une d'elles par programmation, plutôt que d'ajouter par programmation chacune des 49 colonnes souhaitées.  
  
## <a name="formatting"></a>Mise en forme  
 Mise en forme qui peut être appliqué à la <xref:System.Windows.Forms.DataGrid> contrôle inclut les styles de bordure, styles de quadrillage, des polices, ses propriétés de légende, alignement des données et des couleurs d’arrière-plan entre les lignes alternées. Pour plus d’informations, consultez [Comment : mettre en forme le contrôle DataGrid Windows Forms](../../../../docs/framework/winforms/controls/how-to-format-the-windows-forms-datagrid-control.md).  
  
## <a name="events"></a>Événements  
 Outre le contrôle courants événements tels que <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.Enter>, et <xref:System.Windows.Forms.DataGrid.Scroll>, le <xref:System.Windows.Forms.DataGrid> contrôle prend en charge les événements associés à la modification et la navigation dans la grille. Le <xref:System.Windows.Forms.DataGrid.CurrentCell%2A> propriété détermine la cellule sélectionnée. Le <xref:System.Windows.Forms.DataGrid.CurrentCellChanged> événement est déclenché lorsque l’utilisateur navigue vers une nouvelle cellule. Lorsque l’utilisateur navigue vers une nouvelle table via des relations parent/enfant, le <xref:System.Windows.Forms.DataGrid.Navigate> événement est déclenché. Le <xref:System.Windows.Forms.DataGrid.BackButtonClick> événement est déclenché lorsque l’utilisateur clique sur le bouton précédent lorsque l’utilisateur visualise une table enfant et le <xref:System.Windows.Forms.DataGrid.ShowParentDetailsButtonClick> événement est déclenché lorsque l’utilisateur clique sur l’icône Afficher/masquer les lignes parentes.  
  
## <a name="see-also"></a>Voir aussi  
 [DataGrid (contrôle)](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)   
 [Comment : lier le contrôle DataGrid Windows Forms à une Source de données](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)   
 [Comment : ajouter des Tables et colonnes à Windows Forms DataGrid (contrôle)](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)   
 [Comment : supprimer ou masquer des colonnes dans les Windows Forms DataGrid (contrôle)](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)   
 [Comment : mettre en forme le contrôle DataGrid Windows Forms](../../../../docs/framework/winforms/controls/how-to-format-the-windows-forms-datagrid-control.md)