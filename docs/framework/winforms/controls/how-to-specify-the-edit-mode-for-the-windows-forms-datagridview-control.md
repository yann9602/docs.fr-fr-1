---
title: "Comment : spécifier le mode édition pour le contrôle DataGridView Windows Forms"
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
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 42773e29d7071c5bc5f3d5de3660c9891788b422
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a>Comment : spécifier le mode édition pour le contrôle DataGridView Windows Forms
Par défaut, les utilisateurs peuvent modifier le contenu d’actuel <xref:System.Windows.Forms.DataGridView> cellule de zone de texte en tapant qu’il contient ou en appuyant sur F2. Cela met la cellule en mode édition si toutes les conditions suivantes sont remplies :  
  
-   La source de données sous-jacente prend en charge la modification.  
  
-   Le <xref:System.Windows.Forms.DataGridView> le contrôle est activé.  
  
-   Le <xref:System.Windows.Forms.DataGridView.EditMode%2A> valeur de propriété n’est pas <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.  
  
-   Le `ReadOnly` propriétés de cellule, de ligne, de colonne et de contrôle sont tous définis sur `false`.  
  
 En mode édition, l’utilisateur peut modifier la valeur de cellule et appuyez sur ENTRÉE pour valider la modification ou la touche ÉCHAP pour rétablir sa valeur d’origine de la cellule.  
  
 Vous pouvez configurer un <xref:System.Windows.Forms.DataGridView> permettant à une cellule passe en mode édition dès qu’elle devient la cellule active. Le comportement des touches entrée et ÉCHAP est inchangé dans ce cas, mais la cellule reste en mode édition après que la valeur est validée ou annulée. Vous pouvez également configurer le contrôle afin que les cellules entrer en mode Édition uniquement lorsque les utilisateurs entrent dans la cellule ou uniquement lorsque les utilisateurs appuient sur F2. Enfin, vous pouvez empêcher des cellules à partir de l’entrée en mode d’édition, sauf lorsque vous appelez le <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> (méthode).  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a>Pour modifier le mode d’édition d’un contrôle DataGridView  
  
-   Définir le <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> propriété approprié <xref:System.Windows.Forms.DataGridViewEditMode> énumération.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
-   un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;  
  
-   des références aux assemblys <xref:System> et <xref:System.Windows.Forms>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>  
 [Saisie de données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)
