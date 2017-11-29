---
title: "Personnalisation du contrôle DataGridView Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data grids [Windows Forms], customization
- DataGridView control [Windows Forms], customization
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d1246a8052af19057f7aa9d6729e34203177f8e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="customizing-the-windows-forms-datagridview-control"></a>Personnalisation du contrôle DataGridView Windows Forms
Le `DataGridView` contrôle fournit plusieurs propriétés que vous pouvez utiliser pour ajuster l’apparence et le comportement de base (apparence et convivialité) de ses cellules, lignes et colonnes. Si vous avez des besoins particuliers qui vont au-delà des capacités de la <xref:System.Windows.Forms.DataGridViewCellStyle> de classe, toutefois, vous pouvez également implémenter owner-drawn pour le contrôle ou étendre ses fonctionnalités en créant des cellules personnalisées, des colonnes et des lignes.  
  
 Pour peindre des cellules et des lignes vous-même, vous pouvez gérer différents `DataGridView` événements de peinture. Pour modifier des fonctionnalités existantes ou ajouter de nouvelles fonctionnalités, vous pouvez créer vos propres types dérivés existante `DataGridViewCell`, `DataGridViewColumn`, et `DataGridViewRow` types. Vous pouvez également fournir les nouvelles fonctions d’édition en créant des types dérivés qui affichent un contrôle de votre choix lorsqu’une cellule est en mode édition.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour personnaliser l’apparence des cellules du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)  
 Décrit comment gérer les <xref:System.Windows.Forms.DataGridView.CellPainting> événement pour peindre les cellules manuellement.  
  
 [Guide pratique pour personnaliser l’apparence des lignes du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)  
 Décrit comment gérer les <xref:System.Windows.Forms.DataGridView.RowPrePaint> et <xref:System.Windows.Forms.DataGridView.RowPostPaint> événements pour peindre les lignes avec un arrière-plan dégradé personnalisé et un contenu qui s’étend sur plusieurs colonnes.  
  
 [Guide pratique pour personnaliser les cellules et les colonnes du contrôle DataGridView Windows Forms en étendant leur comportement et leur apparence](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 Décrit comment créer des types personnalisés dérivés de `DataGridViewCell` et `DataGridViewColumn` afin de mettre en surbrillance les cellules lorsque le pointeur de la souris est placé sur eux.  
  
 [Guide pratique pour désactiver des boutons d'une colonne de boutons dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/disable-buttons-in-a-button-column-in-the-datagrid.md)  
 Décrit comment créer des types personnalisés dérivés de <xref:System.Windows.Forms.DataGridViewButtonCell> et <xref:System.Windows.Forms.DataGridViewButtonColumn> afin d’afficher les boutons désactivés dans une colonne de boutons.  
  
 [Guide pratique pour héberger des contrôles dans des cellules DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 Décrit comment implémenter le `IDataGridViewEditingControl` interface et créer des types personnalisés dérivés de `DataGridViewCell` et `DataGridViewColumn` afin d’afficher un <xref:System.Windows.Forms.DateTimePicker> contrôle lorsqu’une cellule est en mode édition.  
  
## <a name="reference"></a>Référence  
 <xref:System.Windows.Forms.DataGridView>  
 Fournit la documentation de référence pour le contrôle <xref:System.Windows.Forms.DataGridView>.  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 Fournit la documentation de référence pour la <xref:System.Windows.Forms.DataGridViewCell> classe.  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 Fournit la documentation de référence pour la <xref:System.Windows.Forms.DataGridViewRow> classe.  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 Fournit la documentation de référence pour la <xref:System.Windows.Forms.DataGridViewColumn> classe.  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 Fournit la documentation de référence pour le <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Mises en forme et styles de base dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 Fournit des rubriques qui décrivent comment modifier l'apparence de base du contrôle et le format d'affichage des données de cellules.  
  
## <a name="see-also"></a>Voir aussi  
 [DataGridView, contrôle](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [Types de colonnes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
