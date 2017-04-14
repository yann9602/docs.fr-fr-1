---
title: "Architecture du contr&#244;le DataGridView (Windows Forms) | Microsoft Docs"
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
  - "DataGridView (contrôle Windows Forms), architecture"
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# Architecture du contr&#244;le DataGridView (Windows Forms)
Le contrôle <xref:System.Windows.Forms.DataGridView> et ses classes connexes sont conçus pour constituer un système flexible et extensible pour afficher et modifier des données sous forme de tableau.  Ces classes sont toutes contenues dans l'espace de noms <xref:System.Windows.Forms?displayProperty=fullName>, et elles portent toutes le préfixe "DataGridView".  
  
## Éléments d'architecture  
 Les principales classes auxiliaires <xref:System.Windows.Forms.DataGridView> dérivent de <xref:System.Windows.Forms.DataGridViewElement>.  Le modèle objet suivant illustre la hiérarchie d'héritage de <xref:System.Windows.Forms.DataGridViewElement>.  
  
 ![Modèle objet DataGridViewElement](../../../../docs/framework/winforms/controls/media/datagridviewelement.png "DataGridViewElement")  
Modèle objet DataGridViewElement  
  
 La classe <xref:System.Windows.Forms.DataGridViewElement> fournit une référence au contrôle <xref:System.Windows.Forms.DataGridView> parent et a une propriété <xref:System.Windows.Forms.DataGridViewElement.State%2A> qui détient une valeur qui représente une combinaison de valeurs issues de l'énumération <xref:System.Windows.Forms.DataGridViewElementStates>.  
  
 Les sections suivantes décrivent les classes auxiliaires <xref:System.Windows.Forms.DataGridView> de façon plus détaillées.  
  
### DataGridViewElementStates  
 L'énumération <xref:System.Windows.Forms.DataGridViewElementStates> contient les valeurs suivantes :  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates>  
  
 Les valeurs de cette énumération peuvent être combinées avec les opérateurs logiques de bits, de sorte que la propriété <xref:System.Windows.Forms.DataGridViewElement.State%2A> peut exprimer plusieurs états à la fois.  Par exemple, un <xref:System.Windows.Forms.DataGridViewElement> peut être simultanément <xref:System.Windows.Forms.DataGridViewElementStates>, <xref:System.Windows.Forms.DataGridViewElementStates> et <xref:System.Windows.Forms.DataGridViewElementStates>.  
  
### Cellules et bandes  
 Le contrôle <xref:System.Windows.Forms.DataGridView> comprend deux types d'objets fondamentaux : les cellules et les bandes.  Toutes les cellules dérivent de la classe de base <xref:System.Windows.Forms.DataGridViewCell>.  Les deux types des bandes, <xref:System.Windows.Forms.DataGridViewColumn> et <xref:System.Windows.Forms.DataGridViewRow>, dérivent toutes deux de la classe de base <xref:System.Windows.Forms.DataGridViewBand>.  
  
 Le contrôle <xref:System.Windows.Forms.DataGridView> interagit avec plusieurs classes, mais celles que l'on rencontre le plus souvent sont les classes <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>et <xref:System.Windows.Forms.DataGridViewRow>.  
  
### DataGridViewCell  
 La cellule est l'unité fondamentale d'interaction pour le <xref:System.Windows.Forms.DataGridView>.  L'affichage est centré sur les cellules, et l'entrée de données s'effectue souvent par les cellules.  Vous pouvez accéder aux cellules à l'aide de la collection <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> de la classe <xref:System.Windows.Forms.DataGridViewRow>, et vous pouvez accéder aux cellules sélectionnées à l'aide de la collection <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> du contrôle <xref:System.Windows.Forms.DataGridView>.  Le modèle d'objet suivant illustre cette utilisation et montre la hiérarchie d'héritage de <xref:System.Windows.Forms.DataGridViewCell>.  
  
 ![Modèle objet DataGridViewCell](../../../../docs/framework/winforms/controls/media/datagridviewcell.png "DataGridViewCell")  
Modèle objet DataGridViewCell  
  
 Le type <xref:System.Windows.Forms.DataGridViewCell> est une classe abstraite de base, de laquelle tous les types de cellules dérivent.  <xref:System.Windows.Forms.DataGridViewCell> et ses types dérivés ne sont pas des contrôles Windows Forms, mais des contrôles Windows Forms hôtes.  Toute fonctionnalité d'édition prise en charge par une cellule est généralement gérée par un contrôle hébergé.  
  
 Les objets <xref:System.Windows.Forms.DataGridViewCell> ne contrôlent leur propre apparence et fonctionnalités de peinture de la même manière que les contrôles Windows Forms.  À la place, la <xref:System.Windows.Forms.DataGridView> est responsable de l'apparence de ses objets <xref:System.Windows.Forms.DataGridViewCell>.  Vous pouvez considérablement affecter l'apparence et le comportement des cellules en interagissant avec les propriétés et les événements du contrôle <xref:System.Windows.Forms.DataGridView>.  Lorsque vos besoins en matière de personnalisation dépassent les capacités du contrôle <xref:System.Windows.Forms.DataGridView>, vous pouvez implémenter votre propre classe qui dérive de <xref:System.Windows.Forms.DataGridViewCell> ou d'une de ses classes enfants.  
  
 La liste suivante présente les classes dérivées de <xref:System.Windows.Forms.DataGridViewCell> :  
  
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
  
-   Vos types de cellule personnalisés  
  
### DataGridViewColumn  
 Le schéma du magasin de données attaché du contrôle <xref:System.Windows.Forms.DataGridView> est exprimé dans les colonnes du contrôle <xref:System.Windows.Forms.DataGridView>.  Vous pouvez accéder aux colonnes du contrôle <xref:System.Windows.Forms.DataGridView> en utilisant la collection <xref:System.Windows.Forms.DataGridView.Columns%2A>.  Vous pouvez accéder aux colonnes sélectionnées à l'aide de la collection <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.  Le modèle d'objet suivant illustre cette utilisation et montre la hiérarchie d'héritage de <xref:System.Windows.Forms.DataGridViewColumn>.  
  
 ![Modèle objet DataGridViewColumn](../../../../docs/framework/winforms/controls/media/datagridviewcolumn.png "DataGridViewColumn")  
Modèle objet DataGridViewColumn  
  
 Certains des types de cellule clés ont des types de colonne correspondants.  Ils sont dérivés de la classe de base <xref:System.Windows.Forms.DataGridViewColumn>.  
  
 La liste suivante présente les classes dérivées de <xref:System.Windows.Forms.DataGridViewColumn> :  
  
-   <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
-   Vos types de colonnes personnalisés  
  
### Contrôles d'édition DataGridView  
 Les cellules qui prennent en charge la fonctionnalité d'édition avancée utilisent généralement un contrôle hébergé qui est dérivé d'un contrôle Windows Forms.  Ces contrôles implémentent également l'interface <xref:System.Windows.Forms.IDataGridViewEditingControl>.  Le modèle objet suivant illustre l'utilisation de ces contrôles.  
  
 ![Modèle objet du contrôle d'édition DataGridView](../../../../docs/framework/winforms/controls/media/datagridviewediting.png "DataGridViewEditing")  
Modèle objet des contrôles d'édition DataGridView  
  
 Les contrôles d'édition suivants sont fournis avec le contrôle <xref:System.Windows.Forms.DataGridView> :  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 Pour plus d'informations sur la création de vos propres contrôles d'édition, consultez [Comment : héberger des contrôles dans des cellules DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
 Le tableau suivant illustre la relation entre les types de cellule, les types de colonne et les contrôles d'édition.  
  
|Type de cellule|Contrôle hébergé|Type de colonne|  
|---------------------|----------------------|---------------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|N\/A|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|N\/A|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|N\/A|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|N\/A|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### DataGridViewRow  
 La classe <xref:System.Windows.Forms.DataGridViewRow> affiche les champs de données d'un enregistrement depuis le magasin de données auquel le contrôle <xref:System.Windows.Forms.DataGridView> est joint.  Vous pouvez accéder aux lignes du contrôle <xref:System.Windows.Forms.DataGridView> en utilisant la collection <xref:System.Windows.Forms.DataGridView.Rows%2A>.  Vous pouvez accéder aux lignes sélectionnées à l'aide de la collection <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>.  Le modèle d'objet suivant illustre cette utilisation et montre la hiérarchie d'héritage de <xref:System.Windows.Forms.DataGridViewRow>.  
  
 ![Modèle objet DataGridViewRow](../../../../docs/framework/winforms/controls/media/datagridviewrow.png "DataGridViewRow")  
Modèle objet DataGridViewRow  
  
 Vous pouvez dériver vos propres types à partir de la classe <xref:System.Windows.Forms.DataGridViewRow>, bien que cela ne soit généralement pas nécessaire.  Le contrôle <xref:System.Windows.Forms.DataGridView> contient plusieurs événements et propriétés liés aux lignes pour personnaliser le comportement de ses objets <xref:System.Windows.Forms.DataGridViewRow>.  
  
 Si vous activez la propriété <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> du contrôle <xref:System.Windows.Forms.DataGridView>, une ligne spéciale permettant d'ajouter de nouvelles lignes apparaît comme la dernière ligne.  Cette ligne fait partie de la collection <xref:System.Windows.Forms.DataGridView.Rows%2A>, mais possède des fonctionnalités spéciales pouvant exiger votre attention.  Pour plus d'informations, consultez [Utilisation de la ligne pour les nouveaux enregistrements dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).  
  
## Voir aussi  
 [Vue d'ensemble du contrôle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)   
 [Personnalisation du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)   
 [Utilisation de la ligne pour les nouveaux enregistrements dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)