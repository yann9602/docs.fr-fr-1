---
title: "Proc&#233;dure&#160;: lier un objet DataView &#224; un contr&#244;le DataGridView Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2b73d60a-6049-446a-85a7-3e5a68b183e2
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: lier un objet DataView &#224; un contr&#244;le DataGridView Windows Forms
Le contrôle <xref:System.Windows.Forms.DataGridView> offre un moyen puissant et flexible d'afficher des données sous forme de tableau.  Le contrôle <xref:System.Windows.Forms.DataGridView> prend en charge le modèle de liaison de données Windows Forms standard ; il peut donc créer une liaison avec <xref:System.Data.DataView> et diverses autres sources de données.  Dans la plupart des cas, toutefois, vous créerez une liaison avec un composant <xref:System.Windows.Forms.BindingSource> qui gérera les détails de l'interaction avec la source de données.  
  
 Pour plus d'informations sur le contrôle <xref:System.Windows.Forms.DataGridView>, voir [Vue d'ensemble du contrôle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).  
  
### Pour connecter un contrôle DataGridView à un DataView  
  
1.  Implémentez une méthode pour gérer les détails de la récupération des données d'une base de données.  L'exemple de code suivant implémente une méthode `GetData` qui initialise un composant <xref:System.Data.SqlClient.SqlDataAdapter> et l'utilise pour remplir un <xref:System.Data.DataSet>.  Veillez à définir la variable `connectionString` avec une valeur appropriée pour votre base de données.  Vous devrez accéder à un serveur sur lequel est installé l'exemple de base de données SQL Server AdventureWorks.  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1getdata)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1getdata)]  
  
2.  Dans le gestionnaire d'événements <xref:System.Windows.Forms.Form.Load> de votre formulaire, liez le contrôle <xref:System.Windows.Forms.DataGridView> au composant <xref:System.Windows.Forms.BindingSource> et appelez la méthode `GetData` pour récupérer les données de la base de données.  L'objet <xref:System.Data.DataView> est créé à partir d'une requête [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sur la <xref:System.Data.DataTable> Contact et est ensuite lié au composant <xref:System.Windows.Forms.BindingSource>.  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1formload)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1formload)]  
  
## Voir aussi  
 [Liaison de données et LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)