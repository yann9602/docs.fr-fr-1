---
title: "Types de colonnes dans le contrôle DataGridView Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- columns [Windows Forms], types
- DataGridView control [Windows Forms], column types
- data grids [Windows Forms], columns
ms.assetid: f0a0a9f1-8757-4bfd-891f-d7d12870dbed
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3e45ddcec4459e376a5dab4eec36e51cc2e5e49c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="column-types-in-the-windows-forms-datagridview-control"></a>Types de colonnes dans le contrôle DataGridView Windows Forms
Le <xref:System.Windows.Forms.DataGridView> contrôle utilise plusieurs types de colonne pour afficher ses informations et permettre aux utilisateurs de modifier ou ajouter des informations.  
  
 Lorsque vous liez un <xref:System.Windows.Forms.DataGridView> contrôler et de définir la <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> propriété `true`, les colonnes sont générées automatiquement à l’aide des types de colonne par défaut appropriées pour les types de données contenus dans la source de données.  
  
 Vous pouvez également créer vous-même des instances des classes de la colonne et les ajouter à la collection retournée par la <xref:System.Windows.Forms.DataGridView.Columns%2A> propriété. Vous pouvez créer ces instances pour une utilisation en tant que colonnes indépendantes, ou vous pouvez les lier manuellement. Par exemple, les colonnes liées manuellement sont utiles lorsque vous souhaitez remplacer une colonne générée automatiquement d’un type avec une colonne d’un autre type.  
  
 Le tableau suivant décrit les différentes classes de colonne disponibles pour une utilisation dans les <xref:System.Windows.Forms.DataGridView> contrôle.  
  
|Classe|Description|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|Utilisé avec les valeurs de texte. Généré automatiquement lors de la liaison pour les nombres et les chaînes.|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|Utilisé avec <xref:System.Boolean> et <xref:System.Windows.Forms.CheckState> valeurs. Généré automatiquement lors de la liaison à des valeurs de ces types.|  
|<xref:System.Windows.Forms.DataGridViewImageColumn>|Permet d’afficher des images. Généré automatiquement lors de la liaison à des tableaux d’octets, <xref:System.Drawing.Image> objets, ou <xref:System.Drawing.Icon> objets.|  
|<xref:System.Windows.Forms.DataGridViewButtonColumn>|Permet d’afficher les boutons dans les cellules. Pas générée automatiquement lors de la liaison. Généralement utilisé en tant que colonnes indépendantes.|  
|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|Utilisé pour afficher les listes déroulantes des cellules. Pas générée automatiquement lors de la liaison. En général liés aux données manuellement.|  
|<xref:System.Windows.Forms.DataGridViewLinkColumn>|Permet d’afficher les liens dans les cellules. Pas générée automatiquement lors de la liaison. En général liés aux données manuellement.|  
|Votre type de colonne personnalisé|Vous pouvez créer votre propre classe column en héritant la <xref:System.Windows.Forms.DataGridViewColumn> classe ou une de ses classes dérivées pour fournir une apparence personnalisée, comportement ou des contrôles hébergés. Pour plus d’informations, consultez [Comment : personnaliser des cellules et des colonnes dans le contrôle DataGridView Windows Forms à l’apparence et le comportement de leur extension](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)|  
  
 Ces types de colonnes sont décrites plus en détail dans les sections suivantes.  
  
## <a name="datagridviewtextboxcolumn"></a>DataGridViewTextBoxColumn  
 Le <xref:System.Windows.Forms.DataGridViewTextBoxColumn> est un type de colonne à usage général pour une utilisation avec les valeurs textuelles telles que les nombres et les chaînes. En mode de modification, un <xref:System.Windows.Forms.TextBox> contrôle est affiché dans la cellule active, permettant aux utilisateurs de modifier la valeur de cellule.  
  
 Les valeurs de cellule sont automatiquement convertis en chaînes pour l’affichage. Les valeurs entrées ou modifiées par l’utilisateur sont analysées automatiquement pour créer une valeur de cellule du type de données approprié. Vous pouvez personnaliser ces conversions en gérant les <xref:System.Windows.Forms.DataGridView.CellFormatting> et <xref:System.Windows.Forms.DataGridView.CellParsing> les événements de la <xref:System.Windows.Forms.DataGridView> contrôle.  
  
 Le type de données de valeur de cellule d’une colonne est spécifié dans le <xref:System.Windows.Forms.DataGridViewColumn.ValueType%2A> propriété de la colonne.  
  
## <a name="datagridviewcheckboxcolumn"></a>DataGridViewCheckBoxColumn  
 Le <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> est utilisé avec <xref:System.Boolean> et <xref:System.Windows.Forms.CheckState> valeurs. <xref:System.Boolean>affichent les valeurs comme des cases à cocher deux ou trois états, selon la valeur de la <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A> propriété. Lorsque la colonne est liée à <xref:System.Windows.Forms.CheckState> valeurs, le <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A> valeur de propriété est `true` par défaut.  
  
 En règle générale, les valeurs de cellules de case à cocher sont destinées au stockage, comme toutes les autres données, ou pour effectuer des opérations en bloc. Si vous souhaitez répondre immédiatement lorsque les utilisateurs cliquent sur une cellule de case à cocher, vous pouvez gérer le <xref:System.Windows.Forms.DataGridView.CellClick> événement, mais cet événement se produit avant la mise à jour de la valeur de cellule. Si vous avez besoin de la nouvelle valeur au moment de la, cliquez sur, une option est pour calculer la valeur attendue sera selon la valeur actuelle. Une autre approche consiste à valider immédiatement la modification et de gérer le <xref:System.Windows.Forms.DataGridView.CellValueChanged> événements y répondre. Pour valider la modification lorsque l’utilisateur clique sur la cellule, vous devez gérer le <xref:System.Windows.Forms.DataGridView.CurrentCellDirtyStateChanged> événement. Dans le gestionnaire, si la cellule active est une cellule de case à cocher, appelez le <xref:System.Windows.Forms.DataGridView.CommitEdit%2A> (méthode) et passez le <xref:System.Windows.Forms.DataGridViewDataErrorContexts.Commit> valeur.  
  
## <a name="datagridviewimagecolumn"></a>DataGridViewImageColumn  
 Le <xref:System.Windows.Forms.DataGridViewImageColumn> est utilisé pour afficher des images. Colonnes de type image peuvent être remplies automatiquement à partir d’une source de données, remplies manuellement pour les colonnes indépendantes ou remplies dynamiquement dans un gestionnaire pour le <xref:System.Windows.Forms.DataGridView.CellFormatting> événement.  
  
 Le remplissage automatique d’une colonne d’image à partir d’une source de données fonctionne avec les tableaux d’octets dans divers formats d’image, y compris tous les formats pris en charge par la <xref:System.Drawing.Image> classe et le format OLE Picture utilisé par Microsoft® Access et la base de données Northwind.  
  
 Remplissage d’une colonne d’image manuellement est utile lorsque vous souhaitez fournir les fonctionnalités d’un <xref:System.Windows.Forms.DataGridViewButtonColumn>, mais avec une apparence personnalisée. Vous pouvez gérer le <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> événement pour répondre aux clics dans une cellule d’image.  
  
 Remplissage des cellules d’une colonne d’image dans un gestionnaire pour le <xref:System.Windows.Forms.DataGridView.CellFormatting> événement est utile lorsque vous souhaitez fournir des images pour les valeurs calculées ou les valeurs dans des formats non-image. Par exemple, peut avoir une colonne « Risque » avec des valeurs de chaîne telles que `"high"`, `"middle"`, et `"low"` que vous souhaitez afficher sous forme d’icônes. Ou bien, vous avez peut-être une colonne « Image » qui contient les emplacements des images qui doivent être chargés au lieu du contenu binaire des images.  
  
## <a name="datagridviewbuttoncolumn"></a>DataGridViewButtonColumn  
 Avec la <xref:System.Windows.Forms.DataGridViewButtonColumn>, vous pouvez afficher une colonne de cellules qui contiennent des boutons. Cela est utile lorsque vous souhaitez fournir un moyen simple pour vos utilisateurs effectuer des actions sur des enregistrements particuliers, tels que le placement de la commande ou l’affichage des enregistrements enfants dans une fenêtre distincte.  
  
 Colonnes de boutons ne sont pas générées automatiquement lors de la liaison de données un <xref:System.Windows.Forms.DataGridView> contrôle. Pour utiliser des colonnes de bouton, vous devez les créer manuellement et les ajouter à la collection retournée par la <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType> propriété.  
  
 Vous pouvez répondre aux clics d’utilisateur dans les cellules de boutons en gérant le <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> événement.  
  
## <a name="datagridviewcomboboxcolumn"></a>DataGridViewComboBoxColumn  
 Avec la <xref:System.Windows.Forms.DataGridViewComboBoxColumn>, vous pouvez afficher une colonne de cellules qui contiennent des zones de liste déroulante. Cela est utile pour l’entrée de données dans les champs peuvent contenir uniquement des valeurs particulières, telles que la colonne catégorie de la table Products dans la base de données Northwind.  
  
 Vous pouvez remplir la liste déroulante utilisée pour toutes les cellules de la même façon que vous devez remplir un <xref:System.Windows.Forms.ComboBox> la liste déroulante, soit manuellement par le biais de la collection retournée par la <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> propriété, ou en le liant à une source de données via le <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A>, et <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> propriétés. Pour plus d’informations, consultez [contrôle ComboBox](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md).  
  
 Vous pouvez lier les valeurs de cellule réelle à la source de données utilisée par le <xref:System.Windows.Forms.DataGridView> contrôle en définissant le <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> propriété de la <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType>.  
  
 Colonnes de zone de liste déroulante ne sont pas générées automatiquement lors de la liaison de données un <xref:System.Windows.Forms.DataGridView> contrôle. Pour utiliser des colonnes de zone de liste déroulante, vous devez les créer manuellement et les ajouter à la collection retournée par la <xref:System.Windows.Forms.DataGridView.Columns%2A> propriété.  
  
## <a name="datagridviewlinkcolumn"></a>Valeur DataGridViewLinkColumn  
 Avec la <xref:System.Windows.Forms.DataGridViewLinkColumn>, vous pouvez afficher une colonne de cellules qui contiennent des liens hypertexte. Cela est utile pour les valeurs d’URL dans la source de données ou comme alternative à la colonne de boutons pour les comportements spéciaux tels que l’ouverture d’une fenêtre avec des enregistrements enfants.  
  
 Les colonnes de liens ne sont pas générées automatiquement lors de la liaison de données un <xref:System.Windows.Forms.DataGridView> contrôle. Pour utiliser des colonnes de liens, vous devez les créer manuellement et les ajouter à la collection retournée par la <xref:System.Windows.Forms.DataGridView.Columns%2A> propriété.  
  
 Vous pouvez répondre aux clics des utilisateurs sur les liens en gérant le <xref:System.Windows.Forms.DataGridView.CellContentClick> événement. Cet événement est distinct de le <xref:System.Windows.Forms.DataGridView.CellClick> et <xref:System.Windows.Forms.DataGridView.CellMouseClick> les événements qui se produisent lorsqu’un utilisateur clique sur n’importe où dans une cellule.  
  
 La <xref:System.Windows.Forms.DataGridViewLinkColumn> classe fournit plusieurs propriétés pour modifier l’apparence des liens avant, pendant et après avoir cliqué sur elles.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <xref:System.Windows.Forms.DataGridViewButtonColumn>  
 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
 <xref:System.Windows.Forms.DataGridViewImageColumn>  
 <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
 <xref:System.Windows.Forms.DataGridViewLinkColumn>  
 [DataGridView, contrôle](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [Comment : afficher des images dans les cellules du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)  
 [Guide pratique pour utiliser des colonnes de type image dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-work-with-image-columns-in-the-windows-forms-datagridview-control.md)  
 [Personnalisation du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
