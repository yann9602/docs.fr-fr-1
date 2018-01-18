---
title: "Exécution d’une requête XPath sur un DataSet"
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
ms.assetid: 7e828566-fffe-4d38-abb2-4d68fd73f663
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 3a13d6ee9345731e097d0bdc9b6e59772d29b554
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="performing-an-xpath-query-on-a-dataset"></a>Exécution d’une requête XPath sur un DataSet
La relation entre un synchronisé <xref:System.Data.DataSet> et <xref:System.Xml.XmlDataDocument> vous permet d’utiliser des données XML, services, tels que les requêtes XML Path Language (XPath), qui accèdent à la **XmlDataDocument** et peuvent réaliser certaines opérations plus facilement qu’en accédant le **DataSet** directement. Par exemple, au lieu d’utiliser le **sélectionnez** méthode d’un <xref:System.Data.DataTable> Explorer des relations à d’autres tables dans un **DataSet**, vous pouvez effectuer une requête XPath sur un **XmlDataDocument**  qui est synchronisé avec le **DataSet**, afin d’obtenir une liste d’éléments XML sous la forme d’un <xref:System.Xml.XmlNodeList>. Les nœuds dans le **XmlNodeList**, castés en tant que <xref:System.Xml.XmlElement> nœuds, peuvent alors être passés à la **GetRowFromElement** méthode de la **XmlDataDocument**, afin de retourner la mise en correspondance <xref:System.Data.DataRow> références aux lignes de la table synchronisée **DataSet**.  
  
 Ainsi, l’exemple de code suivant exécute une requête XPath « petit-enfant ». Le **DataSet** est rempli avec trois tables : **clients**, **commandes**, et **OrderDetails**. Dans l’exemple, une relation parent-enfant est tout d’abord créée entre la **clients** et **commandes** tables et entre le **commandes** et **OrderDetails** tables. Une requête XPath est ensuite exécutée pour retourner un **XmlNodeList** de **clients** nœuds où un petit-enfant **OrderDetails** nœud possède un **ProductID**nœud avec la valeur de 43. Fondamentalement, l’exemple utilise la requête XPath pour déterminer quels clients ont commandé le produit qui a le **ProductID** 43.  
  
```vb  
' Assumes that connection is a valid SqlConnection.  
connection.Open()  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Customers", connection)  
customerAdapter.Fill(dataSet, "Customers")  
  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Orders", connection)  
orderAdapter.Fill(dataSet, "Orders")  
  
Dim detailAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM [Order Details]", connection)  
detailAdapter.Fill(dataSet, "OrderDetails")  
  
connection.Close()  
  
dataSet.Relations.Add("CustOrders", _  
dataSet.Tables("Customers").Columns("CustomerID"), _  
dataSet.Tables("Orders").Columns("CustomerID")).Nested = true  
  
dataSet.Relations.Add("OrderDetail", _  
  dataSet.Tables("Orders").Columns("OrderID"), _  
dataSet.Tables("OrderDetails").Columns("OrderID"), false).Nested = true  
  
Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)   
  
Dim nodeList As XmlNodeList = xmlDoc.DocumentElement.SelectNodes( _  
  "descendant::Customers[*/OrderDetails/ProductID=43]")  
  
Dim dataRow As DataRow  
Dim xmlNode As XmlNode  
  
For Each xmlNode In nodeList  
  dataRow = xmlDoc.GetRowFromElement(CType(xmlNode, XmlElement))  
  
  If Not dataRow Is Nothing then Console.WriteLine(xmlRow(0).ToString())  
Next  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection.  
connection.Open();  
  
DataSet dataSet = new DataSet("CustomerOrders");  
  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT * FROM Customers", connection);  
customerAdapter.Fill(dataSet, "Customers");  
  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT * FROM Orders", connection);  
orderAdapter.Fill(dataSet, "Orders");  
  
SqlDataAdapter detailAdapter = new SqlDataAdapter(  
  "SELECT * FROM [Order Details]", connection);  
detailAdapter.Fill(dataSet, "OrderDetails");  
  
connection.Close();  
  
dataSet.Relations.Add("CustOrders",  
  dataSet.Tables["Customers"].Columns["CustomerID"],  
 dataSet.Tables["Orders"].Columns["CustomerID"]).Nested = true;  
  
dataSet.Relations.Add("OrderDetail",  
  dataSet.Tables["Orders"].Columns["OrderID"],  
  dataSet.Tables["OrderDetails"].Columns["OrderID"],   
  false).Nested = true;  
  
XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);   
  
XmlNodeList nodeList = xmlDoc.DocumentElement.SelectNodes(  
  "descendant::Customers[*/OrderDetails/ProductID=43]");  
  
DataRow dataRow;  
foreach (XmlNode xmlNode in nodeList)  
{  
  dataRow = xmlDoc.GetRowFromElement((XmlElement)xmlNode);  
  if (dataRow != null)  
    Console.WriteLine(dataRow[0]);  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Synchronisation DataSet et XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
