---
title: "Comment&#160;: personnaliser l&#39;apparence des cellules du contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "cellules, personnaliser dans le contrôle DataGridView"
  - "grilles de données, personnaliser des cellules"
  - "DataGridView (contrôle Windows Forms), personnaliser des cellules"
ms.assetid: 478b20c9-625c-4116-9c5c-5a16e6f4ec67
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: personnaliser l&#39;apparence des cellules du contr&#244;le DataGridView Windows Forms
Vous pouvez personnaliser l'apparence de toute cellule en gérant l'événement <xref:System.Windows.Forms.DataGridView.CellPainting> du contrôle <xref:System.Windows.Forms.DataGridView>.  Vous pouvez extraire <xref:System.Drawing.Graphics> du contrôle <xref:System.Windows.Forms.DataGridView> de la propriété <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> du <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>.  Avec ce <xref:System.Drawing.Graphics>, vous pouvez affecter l'apparence du contrôle <xref:System.Windows.Forms.DataGridView> tout entier, mais vous souhaiterez habituellement affecter uniquement l'apparence de la cellule qui est peinte actuellement.  La propriété <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> du <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> vous permet de restreindre vos opérations de peinture à la cellule qui est peinte actuellement.  
  
 Dans l'exemple de code suivant, vous peindrez toutes les cellules dans une colonne `ContactName` à l'aide du modèle de couleurs du contrôle <xref:System.Windows.Forms.DataGridView>.  Le contenu de texte de chaque cellule est peint dans <xref:System.Drawing.Color.Crimson%2A>, et un rectangle intercalaire est dessiné dans la même couleur que la propriété <xref:System.Windows.Forms.DataGridView.GridColor%2A> du contrôle <xref:System.Windows.Forms.DataGridView>.  
  
## Exemple  
 [!code-csharp[System.Windows.Forms.DataGridViewCellPainting#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms.DataGridViewCellPainting#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/VB/form1.vb#10)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` avec une colonne `ContactName` telle que celle qui figure dans la table Customers de l'exemple de base de données Northwind.  
  
-   Références aux assemblys System, System.Windows.Forms et System.Drawing.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.CellPainting>   
 [Personnalisation du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)