---
title: "Comment&#160;: obtenir les cellules, lignes et colonnes s&#233;lectionn&#233;es dans le contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "DataGridView (contrôle Windows Forms), obtenir une sélection"
  - "obtenir une sélection, DataGridView (contrôle Windows Forms)"
  - "sélection, DataGridView (contrôle Windows Forms)"
ms.assetid: d93c4b5b-498e-49bc-982a-2229d61778e4
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Comment&#160;: obtenir les cellules, lignes et colonnes s&#233;lectionn&#233;es dans le contr&#244;le DataGridView Windows Forms
Vous pouvez obtenir les cellules, lignes ou colonnes sélectionnées d'un contrôle <xref:System.Windows.Forms.DataGridView> en utilisant les propriétés correspondantes : <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> et <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.  Dans les procédures suivantes, vous obtiendrez les cellules sélectionnées et afficherez leurs index de lignes et de colonnes dans un <xref:System.Windows.Forms.MessageBox>.  
  
### Pour placer les cellules sélectionnées dans un contrôle DataGridView  
  
-   Utilisez la propriété <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>.  
  
    > [!NOTE]
    >  Utilisez la méthode <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> pour éviter d'afficher un nombre potentiellement important de cellules.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### Pour placer les lignes sélectionnées dans un contrôle DataGridView  
  
-   Utilisez la propriété <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>.  Pour permettre aux utilisateurs de sélectionner des lignes, vous devez attribuer à la propriété <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> la valeur <xref:System.Windows.Forms.DataGridViewSelectionMode> ou <xref:System.Windows.Forms.DataGridViewSelectionMode>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### Pour placer les colonnes sélectionnées dans un contrôle DataGridView  
  
-   Utilisez la propriété <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.  Pour permettre aux utilisateurs de sélectionner des colonnes, vous devez attribuer à la propriété <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> la valeur <xref:System.Windows.Forms.DataGridViewSelectionMode> ou <xref:System.Windows.Forms.DataGridViewSelectionMode>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Des contrôles <xref:System.Windows.Forms.Button> nommés `selectedCellsButton`nommé, `selectedRowsButton` et `selectedColumnsButton`, chacun avec les gestionnaires pour l'événement <xref:System.Windows.Forms.Control.Click> joint.  
  
-   un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;  
  
-   Références aux assemblys <xref:System?displayProperty=fullName>, <xref:System.Windows.Forms?displayProperty=fullName> et <xref:System.Text?displayProperty=fullName>.  
  
## Programmation fiable  
 Les collections décrites dans cette rubrique ne s'exécutent pas efficacement lorsque de grands nombres de cellules, de lignes, ou de colonnes sont sélectionnées.  Pour plus d'informations sur l'utilisation de ces collections avec de grandes quantités de données, consultez [Meilleures pratiques pour la mise à l'échelle du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>   
 <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>   
 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>   
 <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>   
 <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>   
 [Sélection et utilisation du Presse\-papiers avec le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)