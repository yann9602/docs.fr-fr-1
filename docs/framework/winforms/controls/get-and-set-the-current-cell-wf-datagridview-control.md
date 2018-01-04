---
title: "Comment : obtenir et définir la cellule active dans le contrôle DataGridView Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 75f8a96b77ffcd40a51cf484f50032f7f2e44309
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a>Comment : obtenir et définir la cellule active dans le contrôle DataGridView Windows Forms
Interaction avec le <xref:System.Windows.Forms.DataGridView> requiert souvent que vous découvriez par programme la cellule qui est actuellement active. Vous devez également modifier la cellule active. Vous pouvez effectuer ces tâches avec la <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> propriété.  
  
> [!NOTE]
>  Vous ne pouvez pas définir la cellule active dans une ligne ou une colonne qui a son <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> propriété `false`.  
  
 Selon la <xref:System.Windows.Forms.DataGridView> mode de sélection du contrôle, la modification de la cellule active peut modifier la sélection. Pour plus d’informations, consultez [les Modes de sélection dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md).  
  
### <a name="to-get-the-current-cell-programmatically"></a>Pour obtenir la cellule active par programme  
  
-   Utilisez le <xref:System.Windows.Forms.DataGridView> du contrôle <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> propriété.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a>Pour définir la cellule active par programmation  
  
-   Définir le <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> propriété de la <xref:System.Windows.Forms.DataGridView> contrôle. Dans l’exemple de code suivant, la cellule active est définie à la ligne 0, colonne 1.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
-   <xref:System.Windows.Forms.Button>contrôles nommés `getCurrentCellButton` et `setCurrentCellButton`. Dans [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], vous devez joindre le <xref:System.Windows.Forms.Control.Click> événements pour chaque bouton au gestionnaire d’événements associé dans l’exemple de code.  
  
-   un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;  
  
-   des références aux assemblys <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>  
 [Fonctionnalités de base liées aux colonnes, lignes et cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [Modes de sélection dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)
