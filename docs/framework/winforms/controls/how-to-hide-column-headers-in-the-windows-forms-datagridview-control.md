---
title: "Comment&#160;: masquer les en-t&#234;tes de colonnes dans le contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "en-têtes de colonnes, masquer"
  - "colonnes (Windows Forms), masquer les en-têtes de colonnes"
  - "DataGridView (contrôle Windows Forms), en-têtes de colonnes"
ms.assetid: e4ad5f68-50d2-4b9e-93ee-9d622423a8ab
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: masquer les en-t&#234;tes de colonnes dans le contr&#244;le DataGridView Windows Forms
Quelquefois vous souhaiterez afficher un <xref:System.Windows.Forms.DataGridView> sans en\-têtes de colonne.  Dans le contrôle <xref:System.Windows.Forms.DataGridView>, la valeur de propriété <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> détermine si les en\-têtes de colonne sont affichés.  
  
### Pour masquer les en\-têtes de colonne  
  
-   Affectez à la propriété <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A?displayProperty=fullName> la valeur `false`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#062](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#062)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#062](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#062)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;  
  
-   Références aux assemblys <xref:System?displayProperty=fullName> et <xref:System.Windows.Forms?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A?displayProperty=fullName>   
 [Fonctionnalités de base liées aux colonnes, lignes et cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)