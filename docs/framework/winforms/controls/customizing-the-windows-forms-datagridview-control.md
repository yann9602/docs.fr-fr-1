---
title: "Personnalisation du contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "grilles de données, personnalisation"
  - "DataGridView (contrôle Windows Forms), personnalisation"
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Personnalisation du contr&#244;le DataGridView Windows Forms
Le contrôle `DataGridView` fournit plusieurs propriétés que vous pouvez utiliser pour ajuster l'apparence et comportement de base de ses cellules, lignes et colonnes.  Toutefois, si vous avez des besoins particuliers qui vont au\-delà des capacités de la classe <xref:System.Windows.Forms.DataGridViewCellStyle>, vous pouvez également implémenter le dessin owner\-drawn pour le contrôle ou étendre ses fonctions en créant des cellules, des colonnes et des lignes personnalisées.  
  
 Pour peindre des cellules et des lignes vous\-même, vous pouvez gérer différents événements de peinture `DataGridView`.  Pour modifier des fonctionnalités existantes ou en fournir de nouvelles, vous pouvez créer vos propres types dérivés des types `DataGridViewCell`, `DataGridViewColumn` et `DataGridViewRow` existants.  Vous pouvez également fournir de nouvelles fonctions d'édition en créant des types dérivés qui affichent un contrôle de votre choix lorsqu'une cellule est en mode édition.  
  
## Dans cette section  
 [Comment : personnaliser l'apparence des cellules du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)  
 Décrit comment gérer l'événement <xref:System.Windows.Forms.DataGridView.CellPainting> pour peindre les cellules manuellement.  
  
 [Comment : personnaliser l'apparence des lignes du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)  
 Décrit comment gérer les événements <xref:System.Windows.Forms.DataGridView.RowPrePaint> et <xref:System.Windows.Forms.DataGridView.RowPostPaint> pour peindre les lignes avec un arrière\-plan dégradé personnalisé et un contenu qui couvrent plusieurs colonnes.  
  
 [Comment : personnaliser les cellules et les colonnes du contrôle DataGridView Windows Forms en étendant leur comportement et leur apparence](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 Décrit comment créer des types personnalisés dérivés de `DataGridViewCell` et `DataGridViewColumn` pour mettre en surbrillance les cellules lorsque le pointeur de la souris s'attarde au\-dessus d'elles.  
  
 [Comment : désactiver des boutons d'une colonne de boutons dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/disable-buttons-in-a-button-column-in-the-datagrid.md)  
 Décrit comment créer des types personnalisés dérivés de <xref:System.Windows.Forms.DataGridViewButtonCell> et <xref:System.Windows.Forms.DataGridViewButtonColumn> pour afficher les boutons désactivés dans une colonne de boutons.  
  
 [Comment : héberger des contrôles dans des cellules DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 Explique comment implémenter l'interface `IDataGridViewEditingControl` et créer des types personnalisés dérivés de `DataGridViewCell` et de `DataGridViewColumn` pour afficher un contrôle <xref:System.Windows.Forms.DateTimePicker> lorsqu'une cellule est en mode édition.  
  
## Référence  
 <xref:System.Windows.Forms.DataGridView>  
 Fournit de la documentation de référence pour le contrôle <xref:System.Windows.Forms.DataGridView>.  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 Fournit de la documentation de référence pour la classe <xref:System.Windows.Forms.DataGridViewCell>.  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 Fournit de la documentation de référence pour la classe <xref:System.Windows.Forms.DataGridViewRow>.  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 Fournit de la documentation de référence pour la classe <xref:System.Windows.Forms.DataGridViewColumn>.  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 Fournit de la documentation de référence pour l'interface <xref:System.Windows.Forms.IDataGridViewEditingControl>.  
  
## Rubriques connexes  
 [Mises en forme et styles de base dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 Fournit des rubriques qui décrivent comment modifier l'apparence de base du contrôle et le format d'affichage des données de cellule.  
  
## Voir aussi  
 [DataGridView, contrôle](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)   
 [Types de colonnes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)