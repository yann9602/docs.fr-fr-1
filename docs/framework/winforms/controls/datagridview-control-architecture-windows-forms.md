---
title: "Architecture du contrôle DataGridView (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fb44a32e63fd7a0ff0e480c205d5459da2ce2bd3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="datagridview-control-architecture-windows-forms"></a>Architecture du contrôle DataGridView (Windows Forms)
Le <xref:System.Windows.Forms.DataGridView> contrôle et ses classes connexes sont conçus pour être un système flexible et extensible pour afficher et modifier des données tabulaires. Ces classes sont toutes contenues dans le <xref:System.Windows.Forms?displayProperty=nameWithType> espace de noms et elles portent toutes le préfixe « DataGridView ».  
  
## <a name="architecture-elements"></a>Éléments d'architecture  
 Le serveur principal <xref:System.Windows.Forms.DataGridView> dérivent des classes auxiliaires <xref:System.Windows.Forms.DataGridViewElement>. Le modèle objet suivant illustre la <xref:System.Windows.Forms.DataGridViewElement> hiérarchie d’héritage.  
  
 ![Modèle objet DataGridViewElement](../../../../docs/framework/winforms/controls/media/datagridviewelement.gif "DataGridViewElement")  
Modèle objet DataGridViewElement  
  
 Le <xref:System.Windows.Forms.DataGridViewElement> classe fournit une référence au parent <xref:System.Windows.Forms.DataGridView> contrôler et a un <xref:System.Windows.Forms.DataGridViewElement.State%2A> propriété, qui contient une valeur qui représente une combinaison de valeurs à partir de la <xref:System.Windows.Forms.DataGridViewElementStates> énumération.  
  
 Les sections suivantes décrivent les <xref:System.Windows.Forms.DataGridView> Compagnon classes plus en détail.  
  
### <a name="datagridviewelementstates"></a>DataGridViewElementStates  
 Le <xref:System.Windows.Forms.DataGridViewElementStates> énumération contient les valeurs suivantes :  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 Les valeurs de cette énumération peuvent être combinées avec les opérateurs logiques au niveau du bit, donc la <xref:System.Windows.Forms.DataGridViewElement.State%2A> propriété peut exprimer plusieurs États à la fois. Par exemple, un <xref:System.Windows.Forms.DataGridViewElement> peuvent être simultanément <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, et <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.  
  
### <a name="cells-and-bands"></a>Cellules et les bandes  
 Le <xref:System.Windows.Forms.DataGridView> contrôle comprend deux types d’objets fondamentaux : les cellules et les bandes. Toutes les cellules dérivent la <xref:System.Windows.Forms.DataGridViewCell> classe de base. Les deux types des bandes, <xref:System.Windows.Forms.DataGridViewColumn> et <xref:System.Windows.Forms.DataGridViewRow>, dérivent toutes les deux la <xref:System.Windows.Forms.DataGridViewBand> classe de base.  
  
 Le <xref:System.Windows.Forms.DataGridView> contrôle interagit avec plusieurs classes, mais sont les plus couramment rencontrés <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, et <xref:System.Windows.Forms.DataGridViewRow>.  
  
### <a name="datagridviewcell"></a>DataGridViewCell  
 La cellule est l’unité fondamentale d’interaction pour le <xref:System.Windows.Forms.DataGridView>. Affichage est centré sur les cellules et saisie de données est souvent effectuée dans les cellules. Vous pouvez accéder aux cellules à l’aide de la <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> collection de la <xref:System.Windows.Forms.DataGridViewRow> classe et vous pouvez accéder les cellules sélectionnées à l’aide de la <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> collection de la <xref:System.Windows.Forms.DataGridView> contrôle. Le modèle objet suivant illustre cette utilisation et montre la <xref:System.Windows.Forms.DataGridViewCell> hiérarchie d’héritage.  
  
 ![Modèle objet DataGridViewCell](../../../../docs/framework/winforms/controls/media/datagridviewcell.gif "DataGridViewCell")  
Modèle objet DataGridViewCell  
  
 Le <xref:System.Windows.Forms.DataGridViewCell> type est une classe de base abstraite de laquelle dérivent tous les types de cellules. <xref:System.Windows.Forms.DataGridViewCell>et ses types dérivés ne sont pas des contrôles Windows Forms, mais certains contrôles Windows Forms de hôte. Toutes les fonctionnalités d’édition prise en charge par une cellule sont généralement gérée par un contrôle hébergé.  
  
 <xref:System.Windows.Forms.DataGridViewCell>objets ne contrôlent pas de leur propre apparence et les fonctionnalités de peinture de la même façon que les contrôles Windows Forms. Au lieu de cela, le <xref:System.Windows.Forms.DataGridView> est responsable de l’apparence de son <xref:System.Windows.Forms.DataGridViewCell> objets. Vous pouvez affecter de manière significative l’apparence et le comportement des cellules en interagissant avec le <xref:System.Windows.Forms.DataGridView> événements et les propriétés du contrôle. Lorsque vous avez des spécifications spéciales pour les personnalisations qui sont au-delà des capacités de la <xref:System.Windows.Forms.DataGridView> (contrôle), vous pouvez implémenter votre propre classe qui dérive de <xref:System.Windows.Forms.DataGridViewCell> ou l’une de ses classes enfants.  
  
 La liste suivante présente les classes dérivées de <xref:System.Windows.Forms.DataGridViewCell>:  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewButtonCell>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkCell>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewImageCell>  
  
-   <xref:System.Windows.Forms.DataGridViewHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewRowHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewColumnHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell>  
  
-   Vos types de cellule personnalisé  
  
### <a name="datagridviewcolumn"></a>DataGridViewColumn  
 Le schéma de la <xref:System.Windows.Forms.DataGridView> magasin de données attaché du contrôle est exprimée dans le <xref:System.Windows.Forms.DataGridView> les colonnes du contrôle. Vous pouvez accéder à la <xref:System.Windows.Forms.DataGridView> les colonnes du contrôle à l’aide de la <xref:System.Windows.Forms.DataGridView.Columns%2A> collection. Vous pouvez accéder à des colonnes sélectionnées à l’aide de la <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> collection. Le modèle objet suivant illustre cette utilisation et montre la <xref:System.Windows.Forms.DataGridViewColumn> hiérarchie d’héritage.  
  
 ![Modèle objet DataGridViewColumn](../../../../docs/framework/winforms/controls/media/datagridviewcolumn.gif "DataGridViewColumn")  
Modèle objet DataGridViewColumn  
  
 Certains des types de cellule clés ont des types de colonne correspondants. Ils sont dérivés de la <xref:System.Windows.Forms.DataGridViewColumn> classe de base.  
  
 La liste suivante présente les classes dérivées de <xref:System.Windows.Forms.DataGridViewColumn>:  
  
-   <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
-   Vos types de colonnes personnalisées  
  
### <a name="datagridview-editing-controls"></a>Contrôles d’édition DataGridView  
 Les cellules qui prennent en charge les fonctionnalités d’édition avancées en général utilisent un contrôle hébergé qui est dérivé d’un contrôle Windows Forms. Ces contrôles implémentent également le <xref:System.Windows.Forms.IDataGridViewEditingControl> interface. Le modèle objet suivant illustre l’utilisation de ces contrôles.  
  
 ![DataGridView, modèle d’objet de contrôle d’édition](../../../../docs/framework/winforms/controls/media/datagridviewediting.gif "DataGridViewEditing")  
Modèle objet de contrôle d’édition DataGridView  
  
 Les contrôles d’édition suivants sont fournis avec le <xref:System.Windows.Forms.DataGridView> contrôle :  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 Pour plus d’informations sur la création de vos propres modification des contrôles, consultez [Comment : héberger des contrôles dans les cellules DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
 Le tableau suivant illustre la relation entre les types de cellules, des types de colonnes et des contrôles d’édition.  
  
|Type de cellule|Contrôle hébergé|Type de colonne|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|N/A|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|N/A|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|N/A|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|N/A|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a>DataGridViewRow  
 Le <xref:System.Windows.Forms.DataGridViewRow> affiche de classe les données d’un enregistrement des champs à partir des données des magasins à laquelle le <xref:System.Windows.Forms.DataGridView> contrôle est attaché. Vous pouvez accéder à la <xref:System.Windows.Forms.DataGridView> les lignes du contrôle à l’aide de la <xref:System.Windows.Forms.DataGridView.Rows%2A> collection. Vous pouvez accéder à des lignes sélectionnées à l’aide de la <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> collection. Le modèle objet suivant illustre cette utilisation et montre la <xref:System.Windows.Forms.DataGridViewRow> hiérarchie d’héritage.  
  
 ![Modèle objet DataGridViewRow](../../../../docs/framework/winforms/controls/media/datagridviewrow.gif "DataGridViewRow")  
Modèle objet DataGridViewRow  
  
 Vous pouvez dériver vos propres types à partir de la <xref:System.Windows.Forms.DataGridViewRow> classe, bien que cela ne soit généralement pas nécessaire. Le <xref:System.Windows.Forms.DataGridView> contrôle a plusieurs événements liés à la ligne et propriétés pour personnaliser le comportement de son <xref:System.Windows.Forms.DataGridViewRow> objets.  
  
 Si vous activez le <xref:System.Windows.Forms.DataGridView> du contrôle <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> propriété, une ligne spéciale pour l’ajout de nouvelles lignes apparaît en tant que la dernière ligne. Cette ligne fait partie de la <xref:System.Windows.Forms.DataGridView.Rows%2A> collection, mais il possède des fonctionnalités spéciales qui peuvent nécessiter votre attention. Pour plus d’informations, consultez [à l’aide de la ligne pour les nouveaux enregistrements dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du contrôle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 [Personnalisation du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [Utilisation de la ligne pour les nouveaux enregistrements dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
