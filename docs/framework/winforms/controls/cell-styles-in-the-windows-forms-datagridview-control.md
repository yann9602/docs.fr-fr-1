---
title: "Styles de cellules dans le contrôle DataGridView Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: dbb75ed6-8804-4232-8382-f9920c2e380c
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 915aba380b6fe35299de94720f216cda5ab66721
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="cell-styles-in-the-windows-forms-datagridview-control"></a>Styles de cellules dans le contrôle DataGridView Windows Forms
Chaque cellule dans le <xref:System.Windows.Forms.DataGridView> contrôle peut avoir son propre style, tel que le format texte, couleur d’arrière-plan, couleur de premier plan et la police. En général, toutefois, plusieurs cellules partagent des caractéristiques de style particulière.  
  
 Groupes de cellules qui partagent des styles peuvent inclure toutes les cellules de lignes particuliers ou colonnes, toutes les cellules qui contiennent des valeurs particulières ou toutes les cellules dans le contrôle. Étant donné que ces groupes se chevauchent, chaque cellule peut obtenir ses informations de style à partir de plusieurs emplacements. Par exemple, vous souhaiterez chaque cellule un <xref:System.Windows.Forms.DataGridView> contrôle à utiliser la même police, mais que les cellules dans les colonnes de la devise à utiliser le format monétaire et uniquement les cellules de devises contenant des nombres négatifs pour utiliser une couleur de premier plan rouge.  
  
## <a name="the-datagridviewcellstyle-class"></a>La classe DataGridViewCellStyle  
 La <xref:System.Windows.Forms.DataGridViewCellStyle> classe contient les propriétés suivantes relatives au style visuel :  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> et <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> et <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A>  
  
 Cette classe contient également les propriétés suivantes relatives à la mise en forme :  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> et <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> et <xref:System.Windows.Forms.DataGridViewCellStyle.DataSourceNullValue%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Padding%2A>  
  
 Pour plus d’informations sur ces propriétés et d’autres propriétés de style de cellule, consultez la <xref:System.Windows.Forms.DataGridViewCellStyle> documentation de référence et les rubriques répertoriées dans la section Voir aussi ci-dessous.  
  
## <a name="using-datagridviewcellstyle-objects"></a>Utilisation d’objets DataGridViewCellStyle  
 Vous pouvez récupérer <xref:System.Windows.Forms.DataGridViewCellStyle> objets de différentes propriétés de la <xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.DataGridViewColumn>, <xref:System.Windows.Forms.DataGridViewRow>, et <xref:System.Windows.Forms.DataGridViewCell> classes et leurs classes dérivées. Si une de ces propriétés n’a pas encore été définie, la récupération de sa valeur créera un nouveau <xref:System.Windows.Forms.DataGridViewCellStyle> objet. Vous pouvez également instancier votre propre <xref:System.Windows.Forms.DataGridViewCellStyle> des objets et les assigner à ces propriétés.  
  
 Vous pouvez éviter une duplication inutile des informations de style en partageant <xref:System.Windows.Forms.DataGridViewCellStyle> objets entre plusieurs <xref:System.Windows.Forms.DataGridView> éléments. Les styles définis dans le contrôle, la colonne et le filtre de niveaux de ligne vers le bas à chaque niveau dans le niveau de la cellule, vous pouvez également éviter la duplication de style en définissant uniquement les propriétés de style à chaque niveau qui diffèrent des niveaux au-dessus. Cela est décrit plus en détail dans la section qui suit.  
  
 Le tableau suivant répertorie les principales propriétés qui obtient ou définit la <xref:System.Windows.Forms.DataGridViewCellStyle> objets.  
  
|Propriété|Classes|Description|  
|--------------|-------------|-----------------|  
|`DefaultCellStyle`|<xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.DataGridViewColumn>, <xref:System.Windows.Forms.DataGridViewRow>et les classes dérivées|Obtient ou définit les styles par défaut utilisés par toutes les cellules dans le contrôle entier (y compris les cellules d’en-tête), dans une colonne ou d’une ligne.|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Obtient ou définit les styles de cellules par défaut utilisés par toutes les lignes dans le contrôle. Cela n’inclut pas de cellules d’en-tête.|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Obtient ou définit les styles de cellules par défaut utilisés par les lignes en alternance dans le contrôle. Utilisé pour créer un effet de type livre comptable.|  
|<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Obtient ou définit les styles de cellules par défaut utilisés par des en-têtes de lignes du contrôle. Substitution du thème actuel si les styles visuels sont activés.|  
|<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Obtient ou définit les styles de cellules par défaut utilisés par des en-têtes de colonnes du contrôle. Substitution du thème actuel si les styles visuels sont activés.|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A>|<xref:System.Windows.Forms.DataGridViewCell>et classes dérivées|Obtient ou définit des styles spécifiés au niveau de la cellule. Ces styles remplacent ceux hérités des niveaux supérieurs.|  
|`InheritedStyle`|<xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewRow>, <xref:System.Windows.Forms.DataGridViewColumn>et les classes dérivées|Obtient tous les styles actuellement appliqués à la cellule, ligne ou colonne, y compris les styles hérités des niveaux supérieurs.|  
  
 Comme indiqué ci-dessus, l’obtention de la valeur d’une propriété de style automatiquement instancie un nouveau <xref:System.Windows.Forms.DataGridViewCellStyle> de l’objet si la propriété n’a pas été définie précédemment. Pour éviter de créer ces objets inutilement, les classes de ligne et de colonne ont une <xref:System.Windows.Forms.DataGridViewBand.HasDefaultCellStyle%2A> propriété que vous pouvez examiner pour déterminer si le <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A> propriété a été définie. De même, les classes de cellule ont une <xref:System.Windows.Forms.DataGridViewCell.HasStyle%2A> propriété qui indique si le <xref:System.Windows.Forms.DataGridViewCell.Style%2A> propriété a été définie.  
  
 Chacune des propriétés de style est associée à une *PropertyName* `Changed` événement sur le <xref:System.Windows.Forms.DataGridView> contrôle. Pour les propriétés de cellule, colonne et ligne, le nom de l’événement commence par «`Row`«, »`Column`», ou «`Cell`» (par exemple, <xref:System.Windows.Forms.DataGridView.RowDefaultCellStyleChanged>). Chacun de ces événements se produit lorsque la propriété de style correspondante est définie à une autre <xref:System.Windows.Forms.DataGridViewCellStyle> objet. Ces événements ne se produisent pas lorsque vous récupérez un <xref:System.Windows.Forms.DataGridViewCellStyle> de l’objet à partir d’une propriété de style et modifier ses valeurs de propriété. Pour répondre aux modifications apportées aux objets de style de la cellule eux-mêmes, gérez le <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged> événement.  
  
## <a name="style-inheritance"></a>Héritage de style  
 Chaque <xref:System.Windows.Forms.DataGridViewCell> obtient son apparence à partir de son <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> propriété. Le <xref:System.Windows.Forms.DataGridViewCellStyle> objet retourné par cette propriété hérite ses valeurs d’une hiérarchie de propriétés de type <xref:System.Windows.Forms.DataGridViewCellStyle>. Ces propriétés sont répertoriées ci-dessous dans l’ordre dans lequel le <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> pour les cellules d’en-tête obtient ses valeurs.  
  
1.  <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
3.  <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>(uniquement pour les cellules des lignes avec des numéros d’index impairs)  
  
4.  <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
5.  <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
6.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Pour les cellules d’en-tête de ligne et de colonne, le <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> propriété est remplie par les valeurs de la liste suivante des propriétés de la source dans l’ordre indiqué.  
  
1.  <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType> ou <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
  
3.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Le diagramme suivant illustre ce processus.  
  
 ![Propriétés du type DataGridViewCellStyle](../../../../docs/framework/winforms/controls/media/datagridviewcells1.gif "DataGridViewCells1")  
  
 Vous pouvez également accéder aux styles hérités par des colonnes et des lignes spécifiques. La colonne <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A> propriété hérite ses valeurs des propriétés suivantes.  
  
1.  <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 La ligne <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> propriété hérite ses valeurs des propriétés suivantes.  
  
1.  <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>(uniquement pour les cellules des lignes avec des numéros d’index impairs)  
  
3.  <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
4.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Pour chaque propriété dans un <xref:System.Windows.Forms.DataGridViewCellStyle> objet retourné par une `InheritedStyle` propriété, la valeur de propriété est obtenue à partir du premier style de cellule dans la liste appropriée qui possède la propriété correspondante est définie sur une valeur autre que la <xref:System.Windows.Forms.DataGridViewCellStyle> classe les valeurs par défaut.  
  
 Le tableau suivant illustre comment la <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> valeur de propriété pour une cellule d’exemple est héritée de sa colonne conteneur.  
  
|Propriété de type`DataGridViewCellStyle`|Exemple `ForeColor` valeur pour un objet récupéré|  
|----------------------------------------------|----------------------------------------------------|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.DarkBlue%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Black%2A?displayProperty=nameWithType>|  
  
 Dans ce cas, le <xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType> valeur à partir de la ligne de la cellule est la première valeur réelle de la liste. Cela devient le <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> valeur de la propriété de la cellule <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>.  
  
 Le diagramme suivant illustre comment les différents <xref:System.Windows.Forms.DataGridViewCellStyle> propriétés peuvent hériter leurs valeurs à partir d’emplacements différents.  
  
 ![DataGridView propriété &#45; l’héritage de valeur](../../../../docs/framework/winforms/controls/media/datagridviewcells2.gif "DataGridViewCells2")  
  
 En tirant parti de l’héritage de style, vous pouvez fournir des styles appropriés pour l’ensemble du contrôle sans avoir à spécifier les mêmes informations dans plusieurs emplacements.  
  
 Bien que les cellules d’en-tête participent à l’héritage de style comme décrit, les objets retournés par le <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> et <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> propriétés de la <xref:System.Windows.Forms.DataGridView> contrôle ont des valeurs de propriété initiales qui remplacent les valeurs de propriété de l’objet retourné par le <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> propriété. Si vous souhaitez que les propriétés définies pour l’objet retourné par la <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> propriété à appliquer aux en-têtes de ligne et de colonne, vous devez définir les propriétés correspondantes des objets retournés par le <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> et <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> propriétés par défaut indiqué pour la <xref:System.Windows.Forms.DataGridViewCellStyle> classe.  
  
> [!NOTE]
>  Si les styles visuels sont activés, les en-têtes de ligne et de colonne (à l’exception de la <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) sont automatiquement un style du thème actuel, en substituant tous les styles spécifiés par ces propriétés.  
  
 Le <xref:System.Windows.Forms.DataGridViewButtonColumn>, <xref:System.Windows.Forms.DataGridViewImageColumn>, et <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> types initialisent également quelques valeurs de l’objet retourné par la colonne <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> propriété. Pour plus d’informations, consultez la documentation de référence pour ces types.  
  
## <a name="setting-styles-dynamically"></a>Définition dynamique des Styles  
 Pour personnaliser les styles de cellules à l’aide de valeurs spécifiques, implémentez un gestionnaire pour le <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> événement. Gestionnaires pour cet événement reçoivent un argument de la <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> type. Cet objet contient des propriétés qui vous permettent de déterminer la valeur de la cellule mise en forme, ainsi que son emplacement dans la <xref:System.Windows.Forms.DataGridView> contrôle. Cet objet contient également un <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.CellStyle%2A> propriété est initialisée à la valeur de la <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> propriété de la mise en forme de cellule. Vous pouvez modifier les propriétés de style de cellule pour spécifier les informations de style appropriées à la valeur de cellule et l’emplacement.  
  
> [!NOTE]
>  Le <xref:System.Windows.Forms.DataGridView.RowPrePaint> et <xref:System.Windows.Forms.DataGridView.RowPostPaint> événements également recevoir un <xref:System.Windows.Forms.DataGridViewCellStyle> données de l’événement d’objet, mais dans leur cas, il s’agit d’une copie de la ligne <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> propriété en lecture seule, ainsi que les modifications apportées à ce dernier n’affectent pas le contrôle.  
  
 Vous pouvez également modifier dynamiquement les styles de cellules individuelles en réponse à des événements tels que les <xref:System.Windows.Forms.DataGridView.CellMouseEnter?displayProperty=nameWithType> et <xref:System.Windows.Forms.DataGridView.CellMouseLeave> les événements. Par exemple, dans un gestionnaire pour le <xref:System.Windows.Forms.DataGridView.CellMouseEnter> événement, vous pouvez stocker la valeur actuelle de la couleur d’arrière-plan de cellule (récupérée par le biais de la cellule <xref:System.Windows.Forms.DataGridViewCell.Style%2A> propriété), puis affectez-lui une nouvelle couleur qui met en surbrillance la cellule lorsque la souris passe dessus. Dans un gestionnaire pour le <xref:System.Windows.Forms.DataGridView.CellMouseLeave> événement, vous pouvez ensuite restaurer la couleur d’arrière-plan à la valeur d’origine.  
  
> [!NOTE]
>  La mise en cache les valeurs stockées dans la cellule <xref:System.Windows.Forms.DataGridViewCell.Style%2A> propriété est importante, même si une valeur de style spécifique est définie. Si vous remplacez temporairement un paramètre de style, le restaurant à son état d’origine « non définie » garantit que la cellule passe à hériter le paramètre de style d’un niveau supérieur. Si vous avez besoin déterminer le style réel en vigueur pour une cellule, quelle que soit le style est hérité ou non, utilisez la cellule <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> propriété.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.InheritedStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>  
 [Mises en forme et styles de base dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [Guide pratique pour définir les styles de cellules par défaut pour le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 [Mise en forme de données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)
