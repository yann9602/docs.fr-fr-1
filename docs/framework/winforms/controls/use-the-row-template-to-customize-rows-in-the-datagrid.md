---
title: "Comment&#160;: utiliser le mod&#232;le de ligne pour personnaliser les lignes du contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "grilles de données, personnaliser les lignes"
  - "DataGridView (contrôle Windows Forms), personnaliser les lignes"
ms.assetid: 6db61607-7e57-4a84-8d63-9d6a7ed7f9ff
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: utiliser le mod&#232;le de ligne pour personnaliser les lignes du contr&#244;le DataGridView Windows Forms
Le contrôle <xref:System.Windows.Forms.DataGridView> utilise le modèle de ligne comme base pour toutes les lignes qu'il ajoute au contrôle via la liaison de données ou lorsque vous appelez la méthode <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=fullName> sans spécifier une ligne existante à utiliser.  
  
 Le modèle de ligne vous donne un contrôle supérieur sur l'apparence et le comportement des lignes que la propriété <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>.  Avec le modèle de ligne, vous pouvez définir toutes les propriétés <xref:System.Windows.Forms.DataGridViewRow>, y compris <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>.  
  
 Il y a des situations où vous devez utiliser le modèle de ligne pour réaliser un effet particulier.  Par exemple, les informations de hauteur de ligne ne pouvant pas être stockées dans un <xref:System.Windows.Forms.DataGridViewCellStyle>, vous donc devez utiliser un modèle de ligne pour modifier la hauteur par défaut utilisée par toutes les lignes.  Le modèle de ligne est également utile lorsque vous créez vos propres classes dérivées de <xref:System.Windows.Forms.DataGridViewRow> et que vous souhaitez utiliser votre type personnalisé lorsque de nouvelles lignes sont ajoutées au contrôle.  
  
> [!NOTE]
>  Le modèle de ligne est utilisé uniquement lorsque des lignes sont ajoutées.  Vous ne pouvez pas modifier des lignes existantes en modifiant le modèle de ligne.  
  
### Pour utiliser le modèle de ligne  
  
-   Définissez les propriétés sur l'objet récupéré de la propriété <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=fullName>.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;  
  
-   Références aux assemblys <xref:System?displayProperty=fullName>, <xref:System.Drawing?displayProperty=fullName> et <xref:System.Windows.Forms?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewCellStyle>   
 <xref:System.Windows.Forms.DataGridViewRow>   
 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=fullName>   
 [Mises en forme et styles de base dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)   
 [Styles de cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)