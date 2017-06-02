---
title: "Comment&#160;: d&#233;finir des styles de police et de couleur dans le contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "grilles de données, styles de couleur"
  - "grilles de données, personnaliser des cellules"
  - "grilles de données, styles de police"
  - "DataGridView (contrôle Windows Forms), personnalisation des cellules"
ms.assetid: 588f2c57-d963-41b1-9c1d-d02d71818113
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: d&#233;finir des styles de police et de couleur dans le contr&#244;le DataGridView Windows Forms
Vous pouvez spécifier l'apparence visuelle des cellules dans un contrôle <xref:System.Windows.Forms.DataGridView> en définissant les propriétés de la classe <xref:System.Windows.Forms.DataGridViewCellStyle>.  Vous pouvez récupérer des instances de cette classe à partir de différentes propriétés de la classe <xref:System.Windows.Forms.DataGridView> et de ses classes auxiliaires ou vous pouvez instancier des objets <xref:System.Windows.Forms.DataGridViewCellStyle> à assigner à ces propriétés.  
  
 Les procédures suivantes illustrent la personnalisation de base de l'apparence des cellules à l'aide de la propriété <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>.  Chaque cellule du contrôle hérite des styles spécifiés via cette propriété, sauf s'ils sont substitués au niveau de la cellule, de la ligne ou de la colonne.  Pour obtenir un exemple d'héritage de style, consultez [Comment : définir les styles de cellules par défaut pour le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).  Pour plus d'informations sur les autres utilisations de la classe <xref:System.Windows.Forms.DataGridViewCellStyle>, consultez les rubriques répertoriées dans la section Voir aussi.  
  
 Cette tâche est très bien prise en charge dans Visual Studio.  Consultez également [Comment : définir des styles de cellules et des formats de données par défaut pour le contrôle DataGridView Windows Forms à l'aide du concepteur](http://msdn.microsoft.com/library/95y5fz2x%20\(v=vs.110\)).  
  
### Pour spécifier la police utilisée par les cellules DataGridView  
  
-   Définissez la propriété <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> d'un <xref:System.Windows.Forms.DataGridViewCellStyle>.  L'exemple de code suivant utilise la propriété <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName> pour définir la police pour l'ensemble du contrôle.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#101](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#101)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#101](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#101)]  
  
### Pour spécifier les couleurs de premier plan et d'arrière\-plan des cellules DataGridView  
  
-   Définissez les propriétés <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> et <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> d'un <xref:System.Windows.Forms.DataGridViewCellStyle>.  L'exemple de code suivant utilise la propriété <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName> pour définir ces styles pour l'ensemble du contrôle.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#102](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#102)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#102](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#102)]  
  
### Pour spécifier les couleurs de premier plan et d'arrière\-plan des cellules DataGridView sélectionnées  
  
-   Définissez les propriétés <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A> et <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> d'un <xref:System.Windows.Forms.DataGridViewCellStyle>.  L'exemple de code suivant utilise la propriété <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName> pour définir ces styles pour l'ensemble du contrôle.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#103](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#103)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#103](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#103)]  
  
## Exemple  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#100)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;  
  
-   des références aux assemblys <xref:System?displayProperty=fullName>, <xref:System.Drawing?displayProperty=fullName> et <xref:System.Windows.Forms?displayProperty=fullName>.  
  
## Programmation fiable  
 Pour bénéficier d'une extensibilité maximale, vous devez partager des objets <xref:System.Windows.Forms.DataGridViewCellStyle> sur plusieurs lignes, colonnes ou cellules qui utilisent les mêmes styles, plutôt que définir séparément les propriétés de style pour chaque élément séparément.  Pour plus d'informations, consultez [Meilleures pratiques pour la mise à l'échelle du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewCellStyle>   
 [Mises en forme et styles de base dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)   
 [Styles de cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)