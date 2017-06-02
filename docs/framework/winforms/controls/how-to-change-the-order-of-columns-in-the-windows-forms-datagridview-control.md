---
title: "Comment&#160;: modifier l&#39;ordre des colonnes dans le contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "colonnes (Windows Forms), ordre de modification"
  - "grilles de données, modifier l'ordre des colonnes"
  - "DataGridView (contrôle Windows Forms), ordre des colonnes"
ms.assetid: 5e9ac3bc-b0f0-48cb-a3d5-b005af905395
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Comment&#160;: modifier l&#39;ordre des colonnes dans le contr&#244;le DataGridView Windows Forms
Quand vous utilisez un <xref:System.Windows.Forms.DataGridView> pour afficher des données à partir d'une source de données, les colonnes du schéma de la source de données apparaissent parfois dans un ordre différent de celui souhaité.  Vous pouvez modifier l'ordre des colonnes à l'aide de la propriété <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> de la classe <xref:System.Windows.Forms.DataGridViewColumn>.  
  
 L'exemple de code suivant repositionne quelques\-unes des colonnes générées automatiquement lors de la liaison à la table Customers dans l'exemple de base de données Northwind.  Pour plus d'informations sur la façon de lier le contrôle <xref:System.Windows.Forms.DataGridView> à une table de base de données, consultez [Comment : lier des données au contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
 Cette tâche est prise en charge dans Visual Studio.  Consultez également [Comment : modifier l'ordre des colonnes dans le contrôle DataGridView Windows Forms](http://msdn.microsoft.com/library/hb1dk7ax\(v=vs.110\)).  
  
## Exemple  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#040](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#040)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#040](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#040)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   un contrôle <xref:System.Windows.Forms.DataGridView> nommé `customersDataGridView` qui est lié à une table avec les noms de colonnes indiqués, comme la table `Customers` dans la base de données Northwind ;  
  
-   des références aux assemblys <xref:System?displayProperty=fullName>, <xref:System.Windows.Forms?displayProperty=fullName>, <xref:System.Data?displayProperty=fullName> et <xref:System.Xml?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewColumn>   
 <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=fullName>   
 [Affichage des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)   
 [Comment : lier des données au contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)