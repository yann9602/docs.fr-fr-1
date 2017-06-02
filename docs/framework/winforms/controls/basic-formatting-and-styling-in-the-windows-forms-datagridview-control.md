---
title: "Mises en forme et styles de base dans le contr&#244;le DataGridView Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "grilles de données, mettre en forme"
  - "DataGridView (contrôle Windows Forms), mettre en forme et appliquer un style"
ms.assetid: b9b90836-1f56-4aa9-8db8-edc78fe830e8
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Mises en forme et styles de base dans le contr&#244;le DataGridView Windows Forms
Le contrôle `DataGridView` facilite la définition de l'apparence de base des cellules et le format d'affichage des valeurs de cellules.  Vous pouvez définir les styles d'apparence et de mise en forme pour les cellules individuelles, pour les cellules de colonnes et de lignes spécifiques, ou pour toutes les cellules du contrôle en définissant les propriétés des objets `DataGridViewCellStyle` accessibles par l'intermédiaire de différentes propriétés de contrôle `DataGridView`.  En outre, vous pouvez modifier ces styles dynamiquement selon des facteurs tels que la valeur de la cellule en gérant l'événement `CellFormatting`.  
  
## Dans cette section  
 [Comment : modifier les styles de bordures et de quadrillage dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md)  
 Décrit comment définir des propriétés `DataGridView` qui définissent l'apparence de la bordure de contrôle et des lignes de séparation entre les cellules.  
  
 [Styles de cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 Décrit la classe `DataGridViewCellStyle` et comment les propriétés de ce type interagissent pour définir l'affichage des cellules dans le contrôle.  
  
 [Comment : définir les styles de cellules par défaut pour le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 Décrit comment utiliser les propriétés `DataGridViewCellStyle` pour définir l'apparence par défaut des cellules dans des lignes et des colonnes spécifiques et dans le contrôle entier.  
  
 [Comment : mettre en forme des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 Décrit comment mettre en forme les valeurs d'affichage des cellules à l'aide des propriétés `DataGridViewCellStyle`.  
  
 [Comment : définir des styles de police et de couleur dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)  
 Décrit comment utiliser la propriété `DefaultCellStyle` pour définir les caractéristiques d'affichage de base pour toutes les cellules du contrôle.  
  
 [Comment : définir des styles de lignes en alternance pour le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)  
 Décrit comment créer un effet "livre comptable" dans le contrôle par affichage alterné de lignes différentes.  
  
 [Comment : utiliser le modèle de ligne pour personnaliser les lignes du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/use-the-row-template-to-customize-rows-in-the-datagrid.md)  
 Décrit comment utiliser la propriété `RowTemplate` pour définir les propriétés de ligne qui seront utilisées pour toutes les lignes dans le contrôle.  
  
## Référence  
 <xref:System.Windows.Forms.DataGridView>  
 Fournit de la documentation de référence pour le contrôle <xref:System.Windows.Forms.DataGridView>.  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 Fournit de la documentation de référence pour la classe <xref:System.Windows.Forms.DataGridViewCellStyle>.  
  
 <xref:System.Windows.Forms.DataGridView.CellFormatting>  
 Fournit de la documentation de référence pour l'événement <xref:System.Windows.Forms.DataGridView.CellFormatting>.  
  
 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>  
 Fournit de la documentation de référence pour la propriété <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>.  
  
## Rubriques connexes  
 [Personnalisation du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 Fournit des rubriques qui décrivent la peinture personnalisée de cellules et de lignes <xref:System.Windows.Forms.DataGridView>, ainsi que la création de types de cellule, colonne et ligne dérivés.  
  
 [Fonctionnalités de base liées aux colonnes, lignes et cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 Fournit des rubriques qui décrivent des propriétés de cellule, ligne et colonne communément utilisées.  
  
## Voir aussi  
 [DataGridView, contrôle](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)