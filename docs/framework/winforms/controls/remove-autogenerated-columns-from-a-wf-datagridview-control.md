---
title: "Comment&#160;: supprimer les colonnes g&#233;n&#233;r&#233;es automatiquement d&#39;un contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "colonnes (Windows Forms), supprimer"
  - "DataGridView (contrôle Windows Forms), supprimer des colonnes"
ms.assetid: 92e28d98-95a3-446c-9150-41b7c7e5be15
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: supprimer les colonnes g&#233;n&#233;r&#233;es automatiquement d&#39;un contr&#244;le DataGridView Windows Forms
Lorsque votre contrôle <xref:System.Windows.Forms.DataGridView> est défini de façon à générer automatiquement ses colonnes selon des données provenant de sa source de données, vous pouvez omettre sélectivement certaines colonnes.  Pour ce faire, appelez la méthode <xref:System.Windows.Forms.DataGridViewColumnCollection.Remove%2A> sur la collection <xref:System.Windows.Forms.DataGridView.Columns%2A>.  Vous pouvez également masquer des colonnes de la vue en attribuant à la propriété <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> la valeur `false`.  Cette technique est utile lorsque vous souhaitez afficher les colonnes cachées dans certaines conditions, ou lorsque vous devez accéder aux données dans les colonnes sans l'afficher.  
  
### Pour supprimer des colonnes générées automatiquement  
  
-   Appelez la méthode <xref:System.Windows.Forms.DataGridViewColumnCollection.Remove%2A> sur la collection <xref:System.Windows.Forms.DataGridView.Columns%2A>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#111](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#111)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#111](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#111)]  
  
### Pour masquer des colonnes générées automatiquement  
  
-   Affectez la valeur `false` à la propriété <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> de la colonne.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#112](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#112)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#112](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#112)]  
  
## Exemple  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#110)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#110)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` lié à une table qui contient des colonnes `Fax` et `CustomerID`, telles que la table `Customers` dans l'exemple de base de données Northwind.  
  
-   Références aux assemblys <xref:System?displayProperty=fullName> et <xref:System.Windows.Forms?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumnCollection.Remove%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=fullName>   
 [Affichage des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)