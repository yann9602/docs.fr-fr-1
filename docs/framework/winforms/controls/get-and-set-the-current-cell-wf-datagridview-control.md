---
title: "Comment&#160;: obtenir et d&#233;finir la cellule active dans le contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "cellules, obtenir et définir les cellules actives"
  - "DataGridView (contrôle Windows Forms), obtenir la cellule active"
  - "DataGridView (contrôle Windows Forms), définir la cellule active"
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: obtenir et d&#233;finir la cellule active dans le contr&#244;le DataGridView Windows Forms
L'interaction avec <xref:System.Windows.Forms.DataGridView> requiert souvent que vous découvriez par programme la cellule qui est actuellement active.  Vous pouvez devoir également modifier la cellule active.  Vous pouvez effectuer ces tâches avec la propriété <xref:System.Windows.Forms.DataGridView.CurrentCell%2A>.  
  
> [!NOTE]
>  Vous ne pouvez pas définir la cellule active dans une ligne ou une colonne dont la propriété <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> a la valeur `false`.  
  
 Selon le mode de sélection du contrôle <xref:System.Windows.Forms.DataGridView>, la modification de la cellule active peut modifier la sélection.  Pour plus d'informations, consultez [Modes de sélection dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md).  
  
### Pour obtenir la cellule active par programme  
  
-   Utilisez la propriété <xref:System.Windows.Forms.DataGridView> du contrôle <xref:System.Windows.Forms.DataGridView.CurrentCell%2A>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### Pour définir la cellule active par programme  
  
-   Définissez la propriété <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> du contrôle <xref:System.Windows.Forms.DataGridView>.  Dans l'exemple de code suivant, la cellule active a pour valeur la ligne 0, et la colonne 1.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Des contrôles <xref:System.Windows.Forms.Button> nommés `getCurrentCellButton` et `setCurrentCellButton`.  En [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], vous devez joindre les événements <xref:System.Windows.Forms.Control.Click> pour chaque bouton au gestionnaire d'événements associé dans l'exemple de code.  
  
-   un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;  
  
-   Références aux assemblys <xref:System?displayProperty=fullName> et <xref:System.Windows.Forms?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=fullName>   
 [Fonctionnalités de base liées aux colonnes, lignes et cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)   
 [Modes de sélection dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)