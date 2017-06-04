---
title: "Comment&#160;: d&#233;finir le mode de s&#233;lection du contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "grilles de données, mode de sélection"
  - "DataGridView (contrôle Windows Forms), mode de sélection"
  - "sélection, modes dans le contrôle DataGridView"
ms.assetid: 2f241643-7f82-4583-8757-03494f63b465
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: d&#233;finir le mode de s&#233;lection du contr&#244;le DataGridView Windows Forms
L'exemple de code suivant montre comment configurer un contrôle <xref:System.Windows.Forms.DataGridView> afin que le clic n'importe où dans une ligne sélectionne automatiquement la ligne entière, et afin qu'une seule ligne puisse être sélectionnée à la fois.  
  
## Exemple  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#065](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#065)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#065](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#065)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;  
  
-   Références aux assemblys <xref:System?displayProperty=fullName> et <xref:System.Windows.Forms?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>   
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>   
 <xref:System.Windows.Forms.DataGridViewSelectionMode>   
 [Sélection et utilisation du Presse\-papiers avec le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)   
 [Modes de sélection dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)