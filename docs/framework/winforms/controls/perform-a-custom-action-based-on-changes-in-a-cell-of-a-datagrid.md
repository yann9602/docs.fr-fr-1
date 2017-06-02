---
title: "Comment&#160;: ex&#233;cuter une action personnalis&#233;e bas&#233;e sur les modifications apport&#233;es dans une cellule d&#39;un contr&#244;le DataGridView Windows Form | Microsoft Docs"
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
  - "cellules, détecter des modifications"
  - "grilles de données, détecter des modifications dans les cellules"
  - "DataGridView (contrôle Windows Forms), détecter des modifications dans les cellules"
ms.assetid: 7fa44d01-97f4-4ccb-a149-bc72628d2c36
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: ex&#233;cuter une action personnalis&#233;e bas&#233;e sur les modifications apport&#233;es dans une cellule d&#39;un contr&#244;le DataGridView Windows Form
Le contrôle <xref:System.Windows.Forms.DataGridView> a plusieurs événements que vous pouvez utiliser pour détecter des modifications dans l'état des cellules <xref:System.Windows.Forms.DataGridView>.  Deux événements parmi les plus communément utilisés sont <xref:System.Windows.Forms.DataGridView.CellValueChanged> et <xref:System.Windows.Forms.DataGridView.CellStateChanged>.  
  
### Pour détecter des modifications dans les valeurs des cellules DataGridView  
  
-   Ajoutez un gestionnaire pour l'événement <xref:System.Windows.Forms.DataGridView.CellValueChanged>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#130)]  
  
### Pour détecter des modifications dans les états des cellules DataGridView  
  
-   Ajoutez un gestionnaire pour l'événement <xref:System.Windows.Forms.DataGridView.CellStateChanged>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#135](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#135)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#135](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#135)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;  Pour C\#, les gestionnaires d'événements doivent être connectés aux événements correspondants.  
  
-   Références aux assemblys <xref:System?displayProperty=fullName> et <xref:System.Windows.Forms?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.CellValueChanged?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.CellStateChanged?displayProperty=fullName>   
 [Programmation avec les cellules, lignes et colonnes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)   
 [Procédure pas à pas : validation des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)