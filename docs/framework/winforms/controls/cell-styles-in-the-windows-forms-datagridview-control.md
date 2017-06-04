---
title: "Styles de cellules dans le contr&#244;le DataGridView Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "cellules, styles"
  - "grilles de données, styles de cellules"
  - "DataGridView (contrôle Windows Forms), styles de cellules"
ms.assetid: dbb75ed6-8804-4232-8382-f9920c2e380c
caps.latest.revision: 33
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 33
---
# Styles de cellules dans le contr&#244;le DataGridView Windows Forms
Chaque cellule du contrôle <xref:System.Windows.Forms.DataGridView> peut avoir son propre style, tel qu'un format de texte, une couleur d'arrière\-plan, une couleur de premier plan et une police.  Toutefois, en règle générale, plusieurs cellules partageront des caractéristiques de style spécifiques.  
  
 Les groupes de cellules qui partagent des styles peuvent inclure toutes les cellules de lignes ou colonnes spécifiques, toutes les cellules qui contiennent des valeurs particulières, ou toutes les cellules du contrôle.  Comme ces groupes se chevauchent, chaque cellule peut obtenir ses informations de style à partir de plusieurs emplacements.  Par exemple, vous pouvez souhaiter que toutes les cellules d'un contrôle <xref:System.Windows.Forms.DataGridView> utilisent la même police, mais que seules les cellules des colonnes de devises utilisent le format monétaire, et que seules les cellules de devises contenant des nombres négatifs utilisent une couleur de premier plan rouge.  
  
## Classe DataGridViewCellStyle  
 La classe <xref:System.Windows.Forms.DataGridViewCellStyle> contient les propriétés suivantes relatives au style visuel :  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> et <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> et <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A>  
  
 Cette classe contient également les propriétés suivantes relatives à la mise en forme :  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> et <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> et <xref:System.Windows.Forms.DataGridViewCellStyle.DataSourceNullValue%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Padding%2A>  
  
 Pour plus d'informations sur ces propriétés et d'autres propriétés de style de cellule, consultez la documentation de référence <xref:System.Windows.Forms.DataGridViewCellStyle> et les rubriques répertoriées dans la section Voir aussi ci\-dessous.  
  
## Utilisation d'objets DataGridViewCellStyle  
 Vous pouvez récupérer des objets <xref:System.Windows.Forms.DataGridViewCellStyle> de plusieurs propriétés des classes <xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.DataGridViewColumn>, <xref:System.Windows.Forms.DataGridViewRow> et <xref:System.Windows.Forms.DataGridViewCell>, et de leurs classes dérivées.  Si l'une de ces propriétés n'a pas encore été définie, la récupération de sa valeur créera un nouvel objet <xref:System.Windows.Forms.DataGridViewCellStyle>.  Vous pouvez également instancier vos propres objets <xref:System.Windows.Forms.DataGridViewCellStyle> et les assigner à ces propriétés.  
  
 Vous pouvez éviter une duplication inutile d'informations de style en partageant des objets <xref:System.Windows.Forms.DataGridViewCellStyle> entre plusieurs éléments <xref:System.Windows.Forms.DataGridView>.  Les styles définis au niveau des contrôles, des colonnes et des lignes effectuant un filtrage sur chaque niveau jusqu'au niveau de la cellule, vous pouvez également éviter la duplication de style en définissant uniquement, pour chaque niveau, les propriétés de style qui diffèrent des niveaux au\-dessus.  Cela est décrit de façon détaillée dans la section Héritage de style qui suit.  
  
 Le tableau suivant répertorie les principales propriétés qui permettent d'obtenir ou de définir des objets <xref:System.Windows.Forms.DataGridViewCellStyle>.  
  
|Propriété|Classes|Description|  
|---------------|-------------|-----------------|  
|`DefaultCellStyle`|<xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.DataGridViewColumn>, <xref:System.Windows.Forms.DataGridViewRow> et classes dérivées|Obtient ou définit les styles par défaut utilisés par toutes les cellules du contrôle entier \(y compris les cellules d'en\-tête\) dans une colonne ou dans une ligne.|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Obtient ou définit les styles de cellules par défaut utilisés par toutes les lignes du contrôle.  Cela n'inclut pas les cellules d'en\-tête.|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Obtient ou définit les styles de cellules par défaut utilisés par les lignes alternées du contrôle.  Utilisée pour créer un effet de livre comptable.|  
|<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Obtient ou définit des styles de cellules par défaut utilisés par les en\-têtes de ligne du contrôle.  Substitution par le thème actuel si les styles visuels sont activés.|  
|<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Obtient ou définit des styles de cellules par défaut utilisés par les en\-têtes de colonne du contrôle.  Substitution par le thème actuel si les styles visuels sont activés.|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A>|<xref:System.Windows.Forms.DataGridViewCell> et classes dérivées|Obtient ou définit des styles spécifiés au niveau de la cellule.  Ces styles se substituent à ceux hérités des niveaux supérieurs.|  
|`InheritedStyle`|<xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewRow>, <xref:System.Windows.Forms.DataGridViewColumn> et classes dérivées|Permet d'obtenir tous les styles appliqués actuellement à la cellule, ligne ou colonne, y compris les styles hérités de niveaux supérieurs.|  
  
 Comme mentionné ci\-dessus, l'obtention de la valeur d'une propriété de style instancie automatiquement un nouvel objet <xref:System.Windows.Forms.DataGridViewCellStyle> si la propriété n'a pas été définie précédemment.  Pour éviter de créer ces objets inutilement, les classes de ligne et de colonne ont une propriété <xref:System.Windows.Forms.DataGridViewBand.HasDefaultCellStyle%2A> que vous pouvez examiner pour déterminer si la propriété <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A> a été définie.  De la même façon, les classes de cellule ont une propriété <xref:System.Windows.Forms.DataGridViewCell.HasStyle%2A> qui indique si la propriété <xref:System.Windows.Forms.DataGridViewCell.Style%2A> a été définie.  
  
 Chacune des propriétés de style possède un événement *NomPropriété*`Changed` correspondant dans le contrôle <xref:System.Windows.Forms.DataGridView>.  Pour les propriétés de ligne, de colonne et de cellule, le nom de l'événement commence par "`Row`", "`Column`" ou "`Cell`" \(par exemple, <xref:System.Windows.Forms.DataGridView.RowDefaultCellStyleChanged>\).  Chacun de ces événements se produit lorsque la propriété de style correspondante a pour valeur un objet <xref:System.Windows.Forms.DataGridViewCellStyle> différent.  Ces événements ne se produisent pas lorsque vous récupérez un objet <xref:System.Windows.Forms.DataGridViewCellStyle> à partir d'une propriété de style et que vous modifiez ses valeurs de propriété.  Pour répondre aux modifications apportées aux objets de style de la cellule eux\-mêmes, gérez l'événement <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged>.  
  
## Héritage de style  
 Chaque <xref:System.Windows.Forms.DataGridViewCell> obtient son aspect à partir de sa propriété <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>.  L'objet <xref:System.Windows.Forms.DataGridViewCellStyle> retourné par cette propriété hérite ses valeurs d'une hiérarchie de propriétés de type <xref:System.Windows.Forms.DataGridViewCellStyle>.  Ces propriétés sont répertoriées ci\-dessous dans l'ordre dans lequel le <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> des cellules autres que les cellules d'en\-tête obtient ses valeurs.  
  
1.  <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=fullName>  
  
2.  <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=fullName>  
  
3.  <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=fullName> \(uniquement pour les cellules des lignes portant des numéros d'index impairs\)  
  
4.  <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=fullName>  
  
5.  <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=fullName>  
  
6.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName>  
  
 Pour les cellules d'en\-tête de ligne et de colonne, la propriété <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> est remplie à l'aide des valeurs figurant dans la liste suivante des propriétés de la source, dans l'ordre indiqué.  
  
1.  <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=fullName>  
  
2.  <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=fullName> ou <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=fullName>  
  
3.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName>  
  
 Le schéma suivant illustre ce processus.  
  
 ![Propriétés du type DataGridViewCellStyle](../../../../docs/framework/winforms/controls/media/datagridviewcells1.png "DataGridViewCells1")  
  
 Vous pouvez également accéder aux styles hérités par des lignes et colonnes spécifiques.  La propriété <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A> de colonne hérite ses valeurs des propriétés suivantes.  
  
1.  <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=fullName>  
  
2.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName>  
  
 La propriété <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> de ligne hérite ses valeurs des propriétés suivantes.  
  
1.  <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=fullName>  
  
2.  <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=fullName> \(uniquement pour les cellules des lignes portant des numéros d'index impairs\)  
  
3.  <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=fullName>  
  
4.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName>  
  
 Pour chaque propriété d'un objet <xref:System.Windows.Forms.DataGridViewCellStyle> retourné par une propriété `InheritedStyle`, la valeur de propriété est obtenue à partir du premier style de cellule figurant dans la liste appropriée \(contenant une propriété dont la valeur est autre que la valeur par défaut de la classe <xref:System.Windows.Forms.DataGridViewCellStyle>\).  
  
 Le tableau suivant illustre la façon dont la valeur de propriété <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> pour une cellule d'exemple est héritée de sa colonne conteneur.  
  
|Propriété de type `DataGridViewCellStyle`|Valeur `ForeColor` d'exemple pour un objet récupéré|  
|-----------------------------------------------|---------------------------------------------------------|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=fullName>|<xref:System.Drawing.Color.Empty?displayProperty=fullName>|  
|<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=fullName>|<xref:System.Drawing.Color.Red%2A?displayProperty=fullName>|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=fullName>|<xref:System.Drawing.Color.Empty?displayProperty=fullName>|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=fullName>|<xref:System.Drawing.Color.Empty?displayProperty=fullName>|  
|<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=fullName>|<xref:System.Drawing.Color.DarkBlue%2A?displayProperty=fullName>|  
|<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName>|<xref:System.Drawing.Color.Black%2A?displayProperty=fullName>|  
  
 Dans ce cas, la valeur <xref:System.Drawing.Color.Red%2A?displayProperty=fullName> de la ligne de la cellule est la première valeur réelle de la liste.  Elle devient la valeur de propriété <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> de <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> de la cellule.  
  
 Le schéma suivant illustre comment des propriétés <xref:System.Windows.Forms.DataGridViewCellStyle> différentes peuvent hériter leurs valeurs d'emplacements différents.  
  
 ![Propriété DataGridView &#45; héritage de valeur](../../../../docs/framework/winforms/controls/media/datagridviewcells2.png "DataGridViewCells2")  
  
 Grâce à l'héritage de style, vous pouvez fournir des styles appropriés pour le contrôle entier sans devoir spécifier les mêmes informations à différents emplacements.  
  
 Bien que les cellules d'en\-tête participent à l'héritage de style comme mentionné, les objets retournés par les propriétés <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> et <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> du contrôle <xref:System.Windows.Forms.DataGridView> ont des valeurs de propriété initiales qui se substituent aux valeurs de propriété de l'objet retourné par la propriété <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>.  Si vous souhaitez que les propriétés définies pour l'objet retourné par la propriété <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> s'appliquent aux en\-têtes de ligne et de colonne, vous devez affecter aux propriétés correspondantes des objets retournés par les propriétés <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> et <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> les valeurs par défaut indiquées pour la classe <xref:System.Windows.Forms.DataGridViewCellStyle>.  
  
> [!NOTE]
>  Si les styles visuels sont activés, les en\-têtes de ligne et de colonne \(à l'exception de <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>\), reçoivent automatiquement un style du thème actuel, en substituant tous les styles spécifiés par ces propriétés.  
  
 Les types <xref:System.Windows.Forms.DataGridViewButtonColumn>, <xref:System.Windows.Forms.DataGridViewImageColumn> et <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> initialisent également quelques valeurs de l'objet retourné par la propriété <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> de la colonne.  Pour plus d'informations, consultez la documentation de référence correspondant à ces types.  
  
## Définition dynamique des styles  
 Pour personnaliser les styles de cellules à l'aide de valeurs spécifiques, implémentez un gestionnaire pour l'événement <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=fullName>.  Les gestionnaires chargés de cet événement reçoivent un argument du type <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs>.  Cet objet contient les propriétés qui vous permettent de déterminer la valeur de la cellule en cours de mise en forme ainsi que son emplacement dans le contrôle <xref:System.Windows.Forms.DataGridView>.  Il contient également une propriété <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.CellStyle%2A> initialisée à l'aide de la valeur de la propriété <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> de la cellule mise en forme.  Vous pouvez modifier les propriétés de style de la cellule pour spécifier des informations de style adaptées à la valeur de la cellule et à son emplacement.  
  
> [!NOTE]
>  Les événements <xref:System.Windows.Forms.DataGridView.RowPrePaint> et <xref:System.Windows.Forms.DataGridView.RowPostPaint> reçoivent également un objet <xref:System.Windows.Forms.DataGridViewCellStyle> dans les données d'événement, mais dans leur cas, il s'agit d'une copie de la propriété <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> de la ligne à des fins de lecture seule, et les modifications apportées n'affectent pas le contrôle.  
  
 Vous pouvez également modifier dynamiquement les styles de cellules individuelles en réponse à des événements, tels que les événements <xref:System.Windows.Forms.DataGridView.CellMouseEnter?displayProperty=fullName> et <xref:System.Windows.Forms.DataGridView.CellMouseLeave>.  Par exemple, vous pouvez stocker la valeur actuelle de la couleur d'arrière\-plan de cellule \(récupérée via la propriété <xref:System.Windows.Forms.DataGridViewCell.Style%2A> de la cellule\) dans un gestionnaire pour l'événement <xref:System.Windows.Forms.DataGridView.CellMouseEnter>, puis définir une nouvelle couleur qui mettra la cellule en surbrillance lorsque la souris se trouvera sur elle.  Dans un gestionnaire pour l'événement <xref:System.Windows.Forms.DataGridView.CellMouseLeave>, vous pouvez ensuite restaurer la valeur d'origine comme couleur d'arrière\-plan.  
  
> [!NOTE]
>  La mise en cache des valeurs stockées dans la propriété <xref:System.Windows.Forms.DataGridViewCell.Style%2A> de la cellule est importante, qu'une valeur de style spécifique ait été définie ou non.  Si vous remplacez temporairement un paramètre de style en restaurant son état d'origine « non défini », cela garantit que la cellule héritera de nouveau du paramètre de style d'un niveau supérieur.  Si vous devez déterminer le style réel en vigueur pour une cellule, que ce style ait été hérité ou non, utilisez la propriété <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> de la cellule.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewCellStyle>   
 <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewBand.InheritedStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=fullName>   
 [Mises en forme et styles de base dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)   
 [Comment : définir les styles de cellules par défaut pour le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)   
 [Mise en forme de données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)