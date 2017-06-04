---
title: "Comment&#160;: modifier les styles de bordures et de quadrillage dans le contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "grilles de données, modifier les styles de bordure"
  - "grilles de données, modifier les styles de lignes de grille"
  - "DataGridView (contrôle Windows Forms), styles de bordures"
  - "DataGridView (contrôle Windows Forms), styles de lignes de grille"
  - "lignes de grille, modifier les styles"
ms.assetid: 2f413c7a-4025-4171-8e3a-66ef908ea583
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: modifier les styles de bordures et de quadrillage dans le contr&#244;le DataGridView Windows Forms
Avec le contrôle <xref:System.Windows.Forms.DataGridView>, vous pouvez personnaliser l'apparence de la bordure et le quadrillage du contrôle pour améliorer l'expérience de l'utilisateur.  Vous pouvez modifier la couleur de quadrillage et le style de bordure du contrôle en plus des styles des bordures des cellules dans le contrôle.  Vous pouvez également appliquer des styles de bordures de cellules différents pour les cellules ordinaires, les cellules d'en\-tête de ligne et les cellules d'en\-tête de colonne.  
  
> [!NOTE]
>  La couleur de quadrillage est utilisée uniquement avec les valeurs <xref:System.Windows.Forms.DataGridViewCellBorderStyle>, <xref:System.Windows.Forms.DataGridViewCellBorderStyle> et <xref:System.Windows.Forms.DataGridViewCellBorderStyle> de l'énumération <xref:System.Windows.Forms.DataGridViewCellBorderStyle> et la valeur <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> de l'énumération <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>.  Les autres valeurs de ces énumérations utilisent des couleurs spécifiées par le système d'exploitation.  En outre, lorsque les styles visuels sont activés sur Windows XP et la famille Windows Server 2003 par le biais de la méthode <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=fullName>, la valeur de propriété <xref:System.Windows.Forms.DataGridView.GridColor%2A> n'est pas utilisée.  
  
### Pour modifier la couleur de quadrillage par programme  
  
-   Définissez la propriété <xref:System.Windows.Forms.DataGridView.GridColor%2A>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#031](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#031)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#031](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#031)]  
  
### Pour modifier par programme le style de bordure du contrôle DataGridView entier  
  
-   Attribuez à la propriété <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> l'une des valeurs d'énumération <xref:System.Windows.Forms.BorderStyle>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#032](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#032)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#032](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#032)]  
  
### Pour modifier par programme les styles de bordure pour les cellules DataGridView  
  
-   Définissez les propriétés <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>, <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A> et <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#033](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#033)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#033](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#033)]  
  
## Exemple  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#030](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#030)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#030](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#030)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;  
  
-   Références aux assemblys <xref:System?displayProperty=fullName>, <xref:System.Windows.Forms?displayProperty=fullName> et <xref:System.Drawing?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.BorderStyle>   
 <xref:System.Windows.Forms.DataGridView.BorderStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.GridColor%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewCellBorderStyle>   
 <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>   
 [Mises en forme et styles de base dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)