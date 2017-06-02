---
title: "Comment&#160;: mettre en forme des donn&#233;es dans le contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "cellules, alignement de texte"
  - "valeurs monétaires, mettre en forme dans les grilles de données"
  - "données (Windows Forms), mettre en forme dans le contrôle DataGridView"
  - "grilles de données, valeurs monétaires"
  - "grilles de données, valeurs de dates"
  - "grilles de données, activer le retour automatique à la ligne"
  - "grilles de données, mettre en forme des données"
  - "grilles de données, alignement de texte"
  - "DataGridView (contrôle Windows Forms), mettre en forme des données"
ms.assetid: 8c33543c-9c08-4636-a65a-fdf714a529b7
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: mettre en forme des donn&#233;es dans le contr&#244;le DataGridView Windows Forms
Les procédures suivantes illustrent une mise en forme de base de valeurs de cellules à l'aide de la propriété <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> d'un contrôle <xref:System.Windows.Forms.DataGridView> et de colonnes spécifiques dans un contrôle.  Pour plus d'informations sur la mise en forme avancée de données, consultez [Comment : personnaliser la mise en forme des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
### Pour mettre en forme des valeurs monétaires et de date  
  
-   Définissez la propriété <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> d'un <xref:System.Windows.Forms.DataGridViewCellStyle>.  L'exemple de code suivant définit le format de colonnes spécifiques à l'aide de la propriété <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> des colonnes.  Les valeurs de la colonne  `UnitPrice`  apparaissent dans le format monétaire spécifique à la culture actuelle, les valeurs négatives étant mises entre parenthèses.  Les valeurs dans la colonne  `ShipDate`  apparaissent dans le format de date court spécifique à la culture actuelle.  Pour plus d'informations sur les valeurs <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A>, consultez [Mise en forme des types](../../../../docs/standard/base-types/formatting-types.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### Pour personnaliser l'affichage de valeurs de base de données nulles  
  
-   Définissez la propriété <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> d'un <xref:System.Windows.Forms.DataGridViewCellStyle>.  L'exemple de code suivant utilise la propriété <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName> pour afficher "no entry" dans toutes les cellules qui contiennent des valeurs égales à <xref:System.DBNull.Value?displayProperty=fullName>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### Pour activer le retour automatique à la ligne dans les cellules textuelles  
  
-   Attribuez à la propriété <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> d'un <xref:System.Windows.Forms.DataGridViewCellStyle> l'une des valeurs d'énumération <xref:System.Windows.Forms.DataGridViewTriState>.  L'exemple de code suivant utilise la propriété <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName> pour définir le mode habillage pour le contrôle entier.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### Pour spécifier l'alignement de texte des cellules DataGridView  
  
-   Attribuez à la propriété <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> d'un <xref:System.Windows.Forms.DataGridViewCellStyle> l'une des valeurs d'énumération <xref:System.Windows.Forms.DataGridViewContentAlignment>.  L'exemple de code suivant définit l'alignement pour une colonne spécifique à l'aide de la propriété <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> de la colonne.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## Exemple  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## Compilation du code  
 Ces exemples nécessitent :  
  
-   Un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` qui contient une colonne nommée `UnitPrice`, une colonne nommée `ShipDate` et une colonne nommée `CustomerName`.  
  
-   Références aux assemblys <xref:System?displayProperty=fullName>, <xref:System.Drawing?displayProperty=fullName> et <xref:System.Windows.Forms?displayProperty=fullName>.  
  
## Programmation fiable  
 Pour l'extensibilité maximale, vous devez partager des objets <xref:System.Windows.Forms.DataGridViewCellStyle> entre plusieurs lignes, colonnes ou cellules qui utilisent les mêmes styles, plutôt que de définir séparément les propriétés de style pour chaque élément.  Pour plus d'informations, consultez [Meilleures pratiques pour la mise à l'échelle du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewCellStyle>   
 [Mises en forme et styles de base dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)   
 [Styles de cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)   
 [Mise en forme de données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)   
 [Comment : personnaliser la mise en forme des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)   
 [Mise en forme des types](../../../../docs/standard/base-types/formatting-types.md)