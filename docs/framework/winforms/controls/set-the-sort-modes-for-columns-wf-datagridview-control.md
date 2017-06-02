---
title: "Comment&#160;: d&#233;finir les modes de tri des colonnes du contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "grilles de données, trier les données"
  - "DataGridView (contrôle Windows Forms), mode de tri"
  - "trier, grilles de données"
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: d&#233;finir les modes de tri des colonnes du contr&#244;le DataGridView Windows Forms
Dans le contrôle <xref:System.Windows.Forms.DataGridView>, les colonnes de zone de texte utilisent le tri automatique par défaut, tandis que d'autres types de colonne ne sont pas triés automatiquement.  Vous pouvez substituer ces valeurs par défaut.  Par exemple, vous pouvez afficher des images à la place de texte, de nombres ou de valeurs de cellules d'énumération.  Si les images ne peuvent pas être triées, les valeurs sous\-jacentes qu'elles représentent peuvent être triées.  
  
 Dans le contrôle <xref:System.Windows.Forms.DataGridView>, la valeur de propriété <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> d'une colonne détermine son comportement de tri.  
  
 La procédure suivante affiche la colonne `Priority` de [Comment : personnaliser la mise en forme des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  Cette colonne est une colonne d'image et n'est pas triable par défaut.  Elle contient, toutefois, des valeurs de cellules réelles qui sont des chaînes, afin qu'elles puissent être triées automatiquement.  
  
### Pour définir le mode de tri d'une colonne  
  
-   Définissez la propriété <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=fullName>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` qui contient une colonne nommée `Priority`.  
  
-   Références aux assemblys <xref:System?displayProperty=fullName> et <xref:System.Windows.Forms?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=fullName>   
 [Tri des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)   
 [Modes de tri des colonnes du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)   
 [Comment : personnaliser le tri dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)