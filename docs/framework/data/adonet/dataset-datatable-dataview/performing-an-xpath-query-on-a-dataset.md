---
title: "Ex&#233;cution d&#39;une requ&#234;te XPath sur un DataSet | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7e828566-fffe-4d38-abb2-4d68fd73f663
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Ex&#233;cution d&#39;une requ&#234;te XPath sur un DataSet
La relation qui existe entre un objet <xref:System.Data.DataSet> et un objet <xref:System.Xml.XmlDataDocument> synchronisés vous permet de disposer de services XML, tels que les requêtes XPath \(XML Path Language\), qui accèdent au **XmlDataDocument** et peuvent réaliser certaines opérations plus facilement qu'en accédant directement au **DataSet**.  Par exemple, au lieu d'utiliser la méthode **Select** d'un objet <xref:System.Data.DataTable> pour suivre les liens vers d'autres tables d'un **DataSet**, vous pouvez exécuter une requête XPath sur un **XmlDataDocument** synchronisé avec le **DataSet** afin d'obtenir une liste d'éléments XML sous la forme d'un objet <xref:System.Xml.XmlNodeList>.  Les nœuds du **XmlNodeList**, castés en tant que nœuds de l'objet <xref:System.Xml.XmlElement>, peuvent alors être passés à la méthode **GetRowFromElement** du **XmlDataDocument**, afin de retourner les références de l'objet <xref:System.Data.DataRow> correspondantes aux lignes de la table du **DataSet** synchronisé.  
  
 Ainsi, l'exemple de code suivant exécute une requête XPath « petit\-enfant ».  Le **DataSet** est rempli avec trois tables : **Customers**, **Orders** et **OrderDetails**.  Dans l'exemple, une relation parent\-enfant est créée d'abord entre les tables **Customers** et **Orders**, puis entre les tables **Orders** et **OrderDetails**.  Puis une requête XPath est effectuée pour retourner un **XmlNodeList** de nœuds **Customers** où un nœud petit\-enfant **OrderDetails** a un nœud **ProductID** d'une valeur de 43.  Fondamentalement, l'exemple utilise la requête XPath pour déterminer quels sont les clients qui ont commandé le produit portant le **ProductID** 43.  
  
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
  
## Voir aussi  
 [Synchronisation des objets DataSet et XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)