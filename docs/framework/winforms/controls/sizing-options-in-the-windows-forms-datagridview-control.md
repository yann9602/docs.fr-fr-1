---
title: "Options de dimensionnement dans le contrôle DataGridView Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], row sizing
- data grids [Windows Forms], column sizing
- DataGridView control [Windows Forms], column sizing
- DataGridView control [Windows Forms], sizing options
- data grids [Windows Forms], row sizing
- data grids [Windows Forms], sizing options
ms.assetid: a5620a9c-0d06-41e3-8934-c25ddb16c9e6
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1a4819f0c4596c34312bf689d57cca687641d6a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sizing-options-in-the-windows-forms-datagridview-control"></a>Options de dimensionnement dans le contrôle DataGridView Windows Forms
<xref:System.Windows.Forms.DataGridView>lignes, colonnes et en-têtes peuvent modifier la taille à la suite de nombreuses occurrences différentes. Le tableau suivant présente ces occurrences.  
  
|Occurrence|Description|  
|----------------|-----------------|  
|Redimensionnement par l’utilisateur|Les utilisateurs peuvent effectuer des ajustements de taille en faisant glisser ou en double-cliquant sur les séparateurs de ligne, de colonne ou en-tête.|  
|Redimensionnement des contrôles|En mode de remplissage de colonne, les largeurs de colonne changent lorsque la largeur du contrôle change ; par exemple, lorsque le contrôle est ancré à son formulaire parent et l’utilisateur redimensionne le formulaire.|  
|Modification de valeur de cellule|Dans les modes de dimensionnement automatique basé sur le contenu, les tailles changent pour s’ajuster à nouvelles valeurs d’affichage.|  
|Appel de méthode|Le redimensionnement par programmation en fonction du contenu vous permet d’effectuer des ajustements de taille opportunistes selon les valeurs de cellule au moment de l’appel de méthode.|  
|Paramètre de propriété|Vous pouvez également définir des valeurs de hauteur et largeur.|  
  
 Par défaut, redimensionnement par l’utilisateur est activé, dimensionnement automatique est désactivé, et les valeurs de cellule qui sont plus larges que leurs colonnes sont tronquées.  
  
 Le tableau suivant présente les scénarios que vous pouvez utiliser pour ajuster le comportement par défaut ou utiliser les options de dimensionnement spécifiques pour obtenir des effets particuliers.  
  
|Scénario|Implémentation|  
|--------------|--------------------|  
|Mode de remplissage de colonne utilisé pour l’affichage des données de taille similaire dans un petit nombre de colonnes qui occupent toute la largeur du contrôle sans afficher la barre de défilement horizontale.|Affectez à la propriété <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> la valeur <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>.|  
|Mode de remplissage de colonne utilisé avec afficher les valeurs de tailles différentes.|Affectez à la propriété <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> la valeur <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>. Initialiser des largeurs de colonne en définissant la colonne <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> propriétés ou en appelant le contrôle <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> méthode après avoir rempli le contrôle de données.|  
|Utilisez le mode de remplissage de colonne avec des valeurs d’importance variable.|Affectez à la propriété <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> la valeur <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>. Paramétrez la plus grande <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> les valeurs des colonnes qui doivent toujours afficher certaines de leurs données ou utilisez une option de dimensionnement autre que mode de remplissage pour des colonnes spécifiques.|  
|Utilisez le mode de remplissage de colonne pour éviter d’afficher l’arrière-plan du contrôle.|Définir le <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> propriété de la dernière colonne à <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> et utiliser d’autres options de dimensionnement pour les autres colonnes. Si les autres colonnes utilisent une trop grande partie de l’espace disponible, définissez le <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> propriété de la dernière colonne.|  
|Afficher une colonne de largeur fixe, tels qu’une icône ou d’une colonne d’ID.|Définissez <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> à <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None> et <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> à <xref:System.Windows.Forms.DataGridViewTriState.False> pour la colonne. Initialisez sa largeur en définissant le <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> propriété ou en appelant le contrôle <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A> méthode après avoir rempli le contrôle de données.|  
|Ajuster la taille automatiquement chaque fois que le contenu de cellule change pour éviter le découpage et d’optimiser l’utilisation de l’espace.|Définir une propriété de dimensionnement automatique sur une valeur qui représente un mode de dimensionnement basé sur le contenu. Pour éviter une altération des performances lorsque vous travaillez avec grandes quantités de données, utilisez un mode de dimensionnement qui calcule les lignes affichées uniquement.|  
|Ajuster les tailles en fonction des valeurs des lignes affichées pour éviter de trop handicaper les performances lorsque vous travaillez avec un grand nombre de lignes.|Utilisez les valeurs d’énumération de mode de dimensionnement approprié avec de redimensionnement automatique ou par programme. Pour ajuster les tailles en fonction des valeurs des lignes qui vient d’être affichées pendant le défilement, appelez une méthode de redimensionnement un <xref:System.Windows.Forms.DataGridView.Scroll> Gestionnaire d’événements. Pour personnaliser le double-clic de l’utilisateur de redimensionnement afin que seules les valeurs des lignes affichées déterminent les nouvelles tailles, appelez une méthode de redimensionnement un <xref:System.Windows.Forms.DataGridView.RowDividerDoubleClick> ou <xref:System.Windows.Forms.DataGridView.ColumnDividerDoubleClick> Gestionnaire d’événements.|  
|Ajuster les tailles en fonction du contenu de la cellule à des moments spécifiques pour éviter de trop handicaper les performances ou pour activer le redimensionnement par l’utilisateur.|Appeler une méthode de redimensionnement en fonction du contenu dans un gestionnaire d’événements. Par exemple, utiliser le <xref:System.Windows.Forms.DataGridView.DataBindingComplete> événements pour initialiser les tailles après la liaison et de gérer le <xref:System.Windows.Forms.DataGridView.CellValidated> ou <xref:System.Windows.Forms.DataGridView.CellValueChanged> événement pour ajuster la taille pour compenser les modifications utilisateur dans une source de données.|  
|Ajustez les hauteurs de lignes pour le contenu de la cellule multiligne.|Assurez-vous que les largeurs de colonne sont appropriées pour afficher les paragraphes du texte et dimensionner les lignes automatique ou par programme en fonction du contenu permet d’ajuster la hauteur. Vérifiez également que les cellules à contenu multiligne sont affichés en utilisant un <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> valeur de style de la cellule <xref:System.Windows.Forms.DataGridViewTriState.True>.<br /><br /> En règle générale, vous utiliserez un mode de dimensionnement automatique des colonnes pour conserver des largeurs de colonne ou les définir à des largeurs spécifiques avant que les hauteurs de lignes sont ajustées.|  
  
## <a name="resizing-with-the-mouse"></a>Redimensionnement avec la souris  
 Par défaut, les utilisateurs peuvent redimensionner les lignes, colonnes et en-têtes qui n’utilisent pas le mode de dimensionnement automatique en fonction des valeurs de cellule. Pour empêcher les utilisateurs de redimensionner dans d’autres modes, telles que le mode de remplissage de colonne, définissez une ou plusieurs des opérations suivantes <xref:System.Windows.Forms.DataGridView> propriétés :  
  
-   <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
 Vous pouvez également empêcher les utilisateurs de redimensionner des lignes ou des colonnes en définissant leurs <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> propriétés. Par défaut, le <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> valeur de propriété est basée sur la <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A> valeur de propriété pour les colonnes et les <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A> valeur de propriété pour les lignes. Si vous définissez explicitement <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> à <xref:System.Windows.Forms.DataGridViewTriState.True> ou <xref:System.Windows.Forms.DataGridViewTriState.False>, toutefois, la valeur spécifiée substitue la valeur de contrôle est pour cette ligne ou colonne. Définissez <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> à <xref:System.Windows.Forms.DataGridViewTriState.NotSet> pour restaurer l’héritage.  
  
 Étant donné que <xref:System.Windows.Forms.DataGridViewTriState.NotSet> restaure l’héritage de valeur, le <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> propriété ne retourne jamais un <xref:System.Windows.Forms.DataGridViewTriState.NotSet> valeur sauf la ligne ou la colonne n’a pas été ajouté à un <xref:System.Windows.Forms.DataGridView> contrôle. Si vous avez besoin déterminer si le <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> valeur de propriété d’une ligne ou colonne est héritée, examinez ses <xref:System.Windows.Forms.DataGridViewElement.State%2A> propriété. Si le <xref:System.Windows.Forms.DataGridViewElement.State%2A> valeur comprend le <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet> indicateur, la <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> valeur de propriété n’est pas héritée.  
  
## <a name="automatic-sizing"></a>Dimensionnement automatique  
 Il existe deux types de dimensionnement automatique dans le <xref:System.Windows.Forms.DataGridView> contrôle : mode de remplissage de colonne et en fonction du contenu de dimensionnement automatique.  
  
 Mode de remplissage de colonne, les colonnes visibles dans le contrôle pour remplir la largeur de la zone d’affichage du contrôle. Pour plus d’informations sur ce mode, consultez [Mode remplissage des colonnes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/column-fill-mode-in-the-windows-forms-datagridview-control.md).  
  
 Vous pouvez également configurer des lignes, colonnes et en-têtes pour ajuster automatiquement leur taille pour s’ajuster à leur contenu de la cellule. Dans ce cas, ajustement de taille se produit chaque fois que le contenu de cellule change.  
  
> [!NOTE]
>  Si vous conservez les valeurs des cellules dans un cache de données personnalisé à l’aide du mode virtuel, le dimensionnement automatique se produit lorsque l’utilisateur modifie une valeur de cellule, mais ne se produit pas lorsque vous modifiez une valeur mise en cache en dehors d’un <xref:System.Windows.Forms.DataGridView.CellValuePushed> Gestionnaire d’événements. Dans ce cas, appelez le <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> méthode pour forcer le contrôle à mettre à jour l’affichage des cellules et appliquer les modes de dimensionnement automatique en cours.  
  
 Si en fonction du contenu de dimensionnement automatique est activé pour une seule dimension, qui est, pour les lignes, mais pas de colonnes, ou pour les colonnes, mais pas les lignes, et <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> est également activé, la taille de réglage se produit également chaque fois que l’autre dimension change. Par exemple, si les lignes, mais pas les colonnes sont configurées pour le dimensionnement automatique et <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> est activé, les utilisateurs peuvent faire glisser les séparateurs de colonne pour modifier la largeur d’une colonne et les hauteurs de lignes seront ajustent afin que le contenu de cellule est toujours affiché.  
  
 Si vous configurez des lignes et des colonnes pour le redimensionnement automatique basé sur le contenu et <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> est activé, le <xref:System.Windows.Forms.DataGridView> contrôle ajuster la taille à chaque changement de contenu de la cellule et sera un rapport largeur-hauteur de cellule idéal calculer les nouvelles tailles.  
  
 Pour configurer le mode de dimensionnement pour les en-têtes et des lignes et des colonnes qui ne substituent pas la valeur du contrôle, définissez une ou plusieurs des opérations suivantes <xref:System.Windows.Forms.DataGridView> propriétés :  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A>  
  
 Pour remplacer le mode de dimensionnement du contrôle pour une colonne, affectez à sa <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> propriété à une valeur autre que <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>. Le mode de dimensionnement pour une colonne est déterminé par son <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> propriété. La valeur de cette propriété est basée sur la colonne <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> valeur de propriété, sauf si cette valeur est <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>, auquel cas du contrôle <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> valeur est héritée.  
  
 Utiliser en fonction du contenu redimensionnement automatique avec précaution lorsque vous travaillez avec grandes quantités de données. Pour éviter de trop handicaper les performances, utilisez le mode de dimensionnement automatique qui calculent les tailles basés uniquement sur les lignes affichées au lieu d’analyser toutes les lignes dans le contrôle. Pour des performances optimales, utilisez redimensionnement par programmation à la place afin que vous pouvez redimensionner à des moments spécifiques, tels qu’immédiatement après les nouvelles données est chargée.  
  
 Modes de dimensionnement automatique basé sur le contenu n’affectent pas les lignes, colonnes ou les en-têtes que vous avez masqués en définissant la ligne ou colonne <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> propriété ou le contrôle <xref:System.Windows.Forms.DataGridView.RowHeadersVisible%2A> ou <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> propriétés `false`. Par exemple, si une colonne est masquée après que qu’il est automatiquement dimensionnée à une grande valeur de cellule, la colonne masquée ne changera pas sa taille si la ligne contenant la valeur de cellule volumineux est supprimée. Dimensionnement automatique ne se produit pas lors de la visibilité change, par conséquent, la modification de la colonne <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> propriété revenir `true` ne force pas à recalculer sa taille en fonction de son contenu en cours.  
  
 Le redimensionnement par programmation en fonction du contenu affecte les lignes, colonnes et en-têtes indépendamment de leur visibilité.  
  
## <a name="programmatic-resizing"></a>Le redimensionnement par programmation  
 Lorsque le dimensionnement automatique est désactivé, vous pouvez définir par programme la largeur ou la hauteur des lignes, des colonnes ou des en-têtes via les propriétés suivantes :  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
  
 Vous pouvez également programmer redimensionner les lignes, colonnes et en-têtes pour s’adapter à leur contenu à l’aide des méthodes suivantes :  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A>  
  
 Ces méthodes seront redimensionne les lignes, colonnes, ou une fois les en-têtes plutôt que leur configuration pour le redimensionnement en continu. Les nouvelles tailles sont calculées automatiquement pour afficher le contenu d’une cellule sans découpage. Lorsque vous redimensionnez par programme des colonnes qui ont <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> valeurs de propriété de <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill>, toutefois, les largeurs calculées en fonction du contenu sont utilisées pour ajuster proportionnellement <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> valeurs de propriété et la colonne réellement largeurs sont Ensuite, calculée en fonction de ces nouvelles proportions afin que toutes les colonnes remplissent la zone d’affichage disponible du contrôle.  
  
 Le redimensionnement par programmation est utile pour éviter de trop handicaper les performances avec le redimensionnement en continu. Il est également utile fournir des tailles initiales pour les en-têtes de colonnes et lignes redimensionnables par l’utilisateur et pour le mode de remplissage de colonne.  
  
 En règle générale, vous appellerez les méthodes de redimensionnement par programmation à des moments spécifiques. Par exemple, vous pouvez redimensionner par programme toutes les colonnes immédiatement après le chargement des données, ou vous pouvez redimensionner par programme une ligne spécifique après qu’une valeur de cellule spécifique a été modifiée.  
  
## <a name="customizing-content-based-sizing-behavior"></a>Personnalisation du comportement de dimensionnement basé sur le contenu  
 Vous pouvez personnaliser les comportements de dimensionnement lorsque vous travaillez avec dérivée <xref:System.Windows.Forms.DataGridView> les types de cellules, lignes et colonnes en substituant le <xref:System.Windows.Forms.DataGridViewCell.GetPreferredSize%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.DataGridViewRow.GetPreferredHeight%2A?displayProperty=nameWithType>, ou <xref:System.Windows.Forms.DataGridViewColumn.GetPreferredWidth%2A?displayProperty=nameWithType> méthodes ou en appelant protégé redimensionnement des surcharges de méthode dans une dérivée <xref:System.Windows.Forms.DataGridView> contrôle. Les surcharges de méthode de redimensionnement protégées sont conçus pour fonctionner en paires pour obtenir un rapport largeur-hauteur de cellule idéal, ce qui évite de trop larges ou à la hauteur des cellules. Par exemple, si vous appelez le `AutoResizeRows(DataGridViewAutoSizeRowsMode,Boolean)` surcharge de la <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A> (méthode) et passez la valeur de `false` pour la <xref:System.Boolean> paramètre, la surcharge calculera les hauteurs et largeurs idéales pour les cellules de la ligne, mais il ajuste la hauteur de ligne uniquement. Vous devez ensuite appeler la <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> méthode pour ajuster les largeurs de colonne à la valeur idéale calculée.  
  
## <a name="content-based-sizing-options"></a>Options de dimensionnement basé sur le contenu  
 Les énumérations utilisées par les méthodes et propriétés de dimensionnement ont des valeurs similaires de dimensionnement basé sur le contenu. Avec ces valeurs, vous pouvez limiter les cellules sont utilisées pour calculer la taille par défaut. Pour toutes les énumérations de dimensionnement, les valeurs avec des noms qui font référence aux cellules affichées limitent leurs calculs aux cellules des lignes affichées. En excluant les lignes est utile pour éviter une altération des performances lorsque vous travaillez avec une grande quantité de lignes. Vous pouvez également limiter les calculs aux valeurs des cellules dans un en-tête ou aux cellules.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeRowMode>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>  
 <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>  
 <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>  
 [Redimensionnement des colonnes et des lignes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)  
 [Mode Remplissage des colonnes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 [Guide pratique pour définir les modes de redimensionnement du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)
