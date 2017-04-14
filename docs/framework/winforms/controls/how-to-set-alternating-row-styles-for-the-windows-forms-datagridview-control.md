---
title: "Comment&#160;: d&#233;finir des styles de lignes en alternance pour le contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "grilles de données, styles de lignes"
  - "DataGridView (contrôle Windows Forms), styles de lignes"
  - "lignes, grilles de données"
ms.assetid: 699ef759-458c-426d-ac87-7c7e71b018ae
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: d&#233;finir des styles de lignes en alternance pour le contr&#244;le DataGridView Windows Forms
Les données sous forme de tableau sont souvent présentées aux utilisateurs dans un format de type livre comptable où les lignes en alternance ont des couleurs d'arrière\-plan différentes.  Avec ce format, il est facile pour les utilisateurs de déterminer quelle cellule appartient à quelle ligne, en particulier dans les tableaux larges qui ont beaucoup de colonnes.  
  
 Avec le contrôle <xref:System.Windows.Forms.DataGridView>, vous pouvez spécifier des informations de style complètes pour les lignes en alternance.  Cela vous permet d'utiliser des caractéristiques de style comme la couleur de premier plan et la police, en plus de la couleur d'arrière\-plan, pour différencier les lignes en alternance.  
  
 Cette tâche est prise en charge dans Visual Studio.  Consultez également [Comment : définir des styles de ligne en alternance pour le contrôle DataGridView Windows Forms à l'aide du concepteur](http://msdn.microsoft.com/library/3z9sk148%20\(v=vs.110\)).  
  
### Pour définir des styles de ligne en alternance par programmation  
  
-   Définissez les propriétés des objets <xref:System.Windows.Forms.DataGridViewCellStyle> retournés par les propriétés <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> et <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> de <xref:System.Windows.Forms.DataGridView>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#068](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#068)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#068](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#068)]  
  
    > [!NOTE]
    >  Les styles spécifiés à l'aide des propriétés <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> et <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> remplacent ceux spécifiés au niveau de la colonne et du <xref:System.Windows.Forms.DataGridView>, mais sont remplacés par ceux définis au niveau de la ligne et de la cellule.  Pour plus d'informations, consultez [Styles de cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;  
  
-   des références aux assemblys <xref:System?displayProperty=fullName>, <xref:System.Drawing?displayProperty=fullName> et <xref:System.Windows.Forms?displayProperty=fullName>.  
  
## Programmation fiable  
 Pour bénéficier d'une extensibilité maximale, vous devez partager des objets <xref:System.Windows.Forms.DataGridViewCellStyle> sur plusieurs lignes, colonnes ou cellules qui utilisent les mêmes styles, plutôt que définir séparément les propriétés de style pour chaque élément séparément.  Pour plus d'informations, consultez [Meilleures pratiques pour la mise à l'échelle du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewCellStyle>   
 [Mises en forme et styles de base dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)   
 [Styles de cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)   
 [Meilleures pratiques pour la mise à l'échelle du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)   
 [Comment : définir des styles de police et de couleur dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)