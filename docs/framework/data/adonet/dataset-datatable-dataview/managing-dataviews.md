---
title: Gestion des DataViews
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 0b67fab5-1722-4d2b-bfc1-247a75f0f1ee
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3cf89cd378d19b5de64a733e80ec757c7e3bdb89
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="managing-dataviews"></a><span data-ttu-id="2a69c-102">Gestion des DataViews</span><span class="sxs-lookup"><span data-stu-id="2a69c-102">Managing DataViews</span></span>
<span data-ttu-id="2a69c-103">Vous pouvez utiliser un objet <xref:System.Data.DataViewManager> pour gérer les paramètres de vue pour toutes les tables d'un objet <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="2a69c-103">You can use a <xref:System.Data.DataViewManager> to manage view settings for all the tables in a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="2a69c-104">Si vous avez un contrôle que vous souhaitez lier à plusieurs tables, comme une grille qui parcourt des relations, un **DataViewManager** est idéale.</span><span class="sxs-lookup"><span data-stu-id="2a69c-104">If you have a control that you want to bind to multiple tables, such as a grid that navigates relationships, a **DataViewManager** is ideal.</span></span>  
  
 <span data-ttu-id="2a69c-105">Le **DataViewManager** contient une collection de <xref:System.Data.DataViewSetting> les objets qui sont utilisées pour définir les paramètres de vue des tables de la <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="2a69c-105">The **DataViewManager** contains a collection of <xref:System.Data.DataViewSetting> objects that are used to set the view setting of the tables in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="2a69c-106">Le <xref:System.Data.DataViewSettingCollection> contient un <xref:System.Data.DataViewSetting> objet pour chaque table dans un **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="2a69c-106">The <xref:System.Data.DataViewSettingCollection> contains one <xref:System.Data.DataViewSetting> object for each table in a **DataSet**.</span></span> <span data-ttu-id="2a69c-107">Vous pouvez définir la valeur par défaut **ApplyDefaultSort**, **tri**, **RowFilter**, et **RowStateFilter** propriétés de la table référencée par à l’aide de son **DataViewSetting**.</span><span class="sxs-lookup"><span data-stu-id="2a69c-107">You can set the default **ApplyDefaultSort**, **Sort**, **RowFilter**, and **RowStateFilter** properties of the referenced table by using its **DataViewSetting**.</span></span> <span data-ttu-id="2a69c-108">Vous pouvez référencer le **DataViewSetting** pour une table particulière par nom ou référence ordinale, ou en passant une référence à cet objet de table spécifique.</span><span class="sxs-lookup"><span data-stu-id="2a69c-108">You can reference the **DataViewSetting** for a particular table by name or ordinal reference, or by passing a reference to that specific table object.</span></span> <span data-ttu-id="2a69c-109">Vous pouvez accéder à la collection de **DataViewSetting** des objets dans une **DataViewManager** à l’aide de la **DataViewSettings** propriété.</span><span class="sxs-lookup"><span data-stu-id="2a69c-109">You can access the collection of **DataViewSetting** objects in a **DataViewManager** by using the **DataViewSettings** property.</span></span>  
  
 <span data-ttu-id="2a69c-110">Le code suivant exemple remplit un **DataSet** avec SQL Server **Northwind** tables de base de données **clients**, **commandes**et  **Détails des commandes**, crée les relations entre les tables, utilise un **DataViewManager** pour définir la valeur par défaut **DataView** paramètres et lie un **DataGrid**  à la **DataViewManager**.</span><span class="sxs-lookup"><span data-stu-id="2a69c-110">The following code example fills a **DataSet** with the SQL Server **Northwind** database tables **Customers**, **Orders**, and **Order Details**, creates the relationships between the tables, uses a **DataViewManager** to set default **DataView** settings, and binds a **DataGrid** to the **DataViewManager**.</span></span> <span data-ttu-id="2a69c-111">L’exemple définit la valeur par défaut **DataView** paramètres pour toutes les tables dans le **DataSet** pour trier par la clé primaire de la table (**ApplyDefaultSort**  =  **true**), puis modifie l’ordre de tri de la **clients** table à trier **CompanyName**.</span><span class="sxs-lookup"><span data-stu-id="2a69c-111">The example sets the default **DataView** settings for all tables in the **DataSet** to sort by the primary key of the table (**ApplyDefaultSort** = **true**), and then modifies the sort order of the **Customers** table to sort by **CompanyName**.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection to Northwind.  
' Create a Connection, DataAdapters, and a DataSet.  
Dim custDA As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
Dim orderDA As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT OrderID, CustomerID FROM Orders", connection)  
Dim ordDetDA As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT OrderID, ProductID, Quantity FROM [Order Details]", connection)  
  
Dim custDS As DataSet = New DataSet()  
  
' Open the Connection.  
connection.Open()  
  
    ' Fill the DataSet with schema information and data.  
    custDA.MissingSchemaAction = MissingSchemaAction.AddWithKey  
    orderDA.MissingSchemaAction = MissingSchemaAction.AddWithKey  
    ordDetDA.MissingSchemaAction = MissingSchemaAction.AddWithKey  
  
    custDA.Fill(custDS, "Customers")  
    orderDA.Fill(custDS, "Orders")  
    ordDetDA.Fill(custDS, "OrderDetails")  
  
    ' Close the Connection.  
    connection.Close()  
  
    ' Create relationships.  
    custDS.Relations.Add("CustomerOrders", _  
          custDS.Tables("Customers").Columns("CustomerID"), _  
          custDS.Tables("Orders").Columns("CustomerID"))  
  
    custDS.Relations.Add("OrderDetails", _  
          custDS.Tables("Orders").Columns("OrderID"), _  
          custDS.Tables("OrderDetails").Columns("OrderID"))  
  
' Create default DataView settings.  
Dim viewManager As DataViewManager = New DataViewManager(custDS)  
  
Dim viewSetting As DataViewSetting  
For Each viewSetting In viewManager.DataViewSettings  
  viewSetting.ApplyDefaultSort = True  
Next  
  
viewManager.DataViewSettings("Customers").Sort = "CompanyName"  
  
' Bind to a DataGrid.  
Dim grid As System.Windows.Forms.DataGrid = New System.Windows.Forms.DataGrid()  
grid.SetDataBinding(viewManager, "Customers")  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection to Northwind.  
// Create a Connection, DataAdapters, and a DataSet.  
SqlDataAdapter custDA = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
SqlDataAdapter orderDA = new SqlDataAdapter(  
  "SELECT OrderID, CustomerID FROM Orders", connection);  
SqlDataAdapter ordDetDA = new SqlDataAdapter(  
  "SELECT OrderID, ProductID, Quantity FROM [Order Details]", connection);  
  
DataSet custDS = new DataSet();  
  
// Open the Connection.  
connection.Open();  
  
    // Fill the DataSet with schema information and data.  
    custDA.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
    orderDA.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
    ordDetDA.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
  
    custDA.Fill(custDS, "Customers");  
    orderDA.Fill(custDS, "Orders");  
    ordDetDA.Fill(custDS, "OrderDetails");  
  
    // Close the Connection.  
    connection.Close();  
  
    // Create relationships.  
    custDS.Relations.Add("CustomerOrders",  
          custDS.Tables["Customers"].Columns["CustomerID"],  
          custDS.Tables["Orders"].Columns["CustomerID"]);  
  
    custDS.Relations.Add("OrderDetails",  
          custDS.Tables["Orders"].Columns["OrderID"],  
          custDS.Tables["OrderDetails"].Columns["OrderID"]);  
  
// Create default DataView settings.  
DataViewManager viewManager = new DataViewManager(custDS);  
  
foreach (DataViewSetting viewSetting in viewManager.DataViewSettings)  
  viewSetting.ApplyDefaultSort = true;  
  
viewManager.DataViewSettings["Customers"].Sort = "CompanyName";  
  
// Bind to a DataGrid.  
System.Windows.Forms.DataGrid grid = new System.Windows.Forms.DataGrid();  
grid.SetDataBinding(viewManager, "Customers");  
```  
  
## <a name="see-also"></a><span data-ttu-id="2a69c-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a69c-112">See Also</span></span>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataViewManager>  
 <xref:System.Data.DataViewSetting>  
 <xref:System.Data.DataViewSettingCollection>  
 [<span data-ttu-id="2a69c-113">DataViews</span><span class="sxs-lookup"><span data-stu-id="2a69c-113">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="2a69c-114">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="2a69c-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
