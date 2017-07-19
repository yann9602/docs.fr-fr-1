---
title: "Comment&#160;: d&#233;finir les styles de cellules par d&#233;faut pour le contr&#244;le DataGridView Windows&#160;Forms | Microsoft Docs"
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
  - "cellules, styles"
  - "grilles de données, styles de cellules"
  - "DataGridView (contrôle Windows Forms), styles de cellules"
ms.assetid: 1aaaca43-5340-447e-99c0-9177d9776aa1
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Comment&#160;: d&#233;finir les styles de cellules par d&#233;faut pour le contr&#244;le DataGridView Windows&#160;Forms
Avec le contrôle <xref:System.Windows.Forms.DataGridView>, vous pouvez spécifier des styles de cellules par défaut pour le contrôle entier et pour des colonnes et des lignes spécifiques.  Ces valeurs par défaut sont propagées du niveau contrôle au niveau colonne, puis au niveau ligne, et enfin au niveau cellule.  Si une propriété <xref:System.Windows.Forms.DataGridViewCellStyle> spécifique n'est pas définie au niveau de la cellule, le paramètre de propriété par défaut au niveau de la ligne est utilisé.  Si la propriété n'est pas définie non plus au niveau de la ligne, le paramètre de colonne par défaut est utilisé.  Pour finir, si la propriété n'est pas non plus définie au niveau de la colonne, le paramètre <xref:System.Windows.Forms.DataGridView> par défaut est utilisé.  Avec ce paramètre, vous pouvez éviter de devoir dupliquer les paramètres de propriétés à plusieurs niveaux.  À chaque niveau, il vous suffit de spécifier les styles qui diffèrent des niveaux au\-dessus de lui.  Pour plus d'informations, consultez [Styles de cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 Cette tâche est très bien prise en charge dans Visual Studio.  Consultez également [Comment : définir des styles de cellules et des formats de données par défaut pour le contrôle DataGridView Windows Forms à l'aide du concepteur](http://msdn.microsoft.com/library/95y5fz2x%20\(v=vs.110\)).  
  
### Pour définir les styles de cellules par défaut par programmation  
  
1.  Définissez les propriétés du <xref:System.Windows.Forms.DataGridViewCellStyle> récupéré via la propriété <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#141](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#141)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#141](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#141)]  
  
2.  Créez et initialisez de nouveaux objets <xref:System.Windows.Forms.DataGridViewCellStyle> pour une utilisation par plusieurs lignes et colonnes.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#142](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#142)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#142](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#142)]  
  
3.  Définissez la propriété `DefaultCellStyle` de lignes et de colonnes spécifiques.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#143](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#143)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#143](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#143)]  
  
## Exemple  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#140)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#140)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;  
  
-   des références aux assemblys <xref:System?displayProperty=fullName>, <xref:System.Drawing?displayProperty=fullName> et <xref:System.Windows.Forms?displayProperty=fullName>.  
  
## Programmation fiable  
 Pour bénéficier d'une extensibilité maximale quand vous travaillez avec des jeux de données très volumineux, vous devez partager des objets <xref:System.Windows.Forms.DataGridViewCellStyle> sur plusieurs lignes, colonnes ou cellules qui utilisent les mêmes styles, plutôt que définir séparément les propriétés de style pour les différents éléments.  En outre, vous devez créer des lignes partagées et y accéder à l'aide de la propriété <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=fullName>.  Pour plus d'informations, consultez [Meilleures pratiques pour la mise à l'échelle du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewCellStyle>   
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=fullName>   
 [Mises en forme et styles de base dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)   
 [Styles de cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)   
 [Meilleures pratiques pour la mise à l'échelle du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)   
 [Comment : définir des styles de lignes en alternance pour le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)