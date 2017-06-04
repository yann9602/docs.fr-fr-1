---
title: "Imbrication de DataRelations | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Imbrication de DataRelations
Dans une représentation relationnelle des données, chaque table contient des lignes reliées aux lignes d'autres tables par une colonne ou un ensemble de colonnes.  Dans l'objet <xref:System.Data.DataSet> ADO.NET, la relation entre les tables est implémentée à l'aide d'un objet <xref:System.Data.DataRelation>.  Lorsque vous créez un **DataRelation**, les relations parent\-enfant des colonnes sont managées uniquement via la relation.  Les tables et les colonnes constituent des entités distinctes.  Dans la représentation hiérarchique des données proposée par XML, les relations parent\-enfant sont représentés sous forme d'éléments parents contenant des éléments enfants imbriqués.  
  
 Pour faciliter l'imbrication des objets enfants lorsqu'un **DataSet** est synchronisé avec un objet <xref:System.Xml.XmlDataDocument> ou écrit sous forme de données XML à l'aide de **WriteXml**, le **DataRelation** expose une propriété **Nested**.  Lorsqu'il est écrit sous forme de données XML ou synchronisé avec un **XmlDataDocument**, le fait d'assigner la valeur **true** à la propriété **Nested** d'un **DataRelation** entraîne l'imbrication dans la colonne parent des lignes enfants de la relation.  Par défaut, la propriété **Nested** du **DataRelation** a la valeur **false**.  
  
 Examinons, par exemple, le **DataSet** suivant.  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT OrderID, CustomerID, OrderDate FROM Orders", connection)  
  
connection.Open()  
  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
customerAdapter.Fill(dataSet, "Customers")  
orderAdapter.Fill(dataSet, "Orders")  
  
connection.Close()  
  
Dim customerOrders As DataRelation = dataSet.Relations.Add( _  
  "CustOrders", dataSet.Tables("Customers").Columns("CustomerID"), _  
  dataSet.Tables("Orders").Columns("CustomerID"))  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT OrderID, CustomerID, OrderDate FROM Orders", connection);  
  
connection.Open();  
  
DataSet dataSet = new DataSet("CustomerOrders");  
customerAdapter.Fill(dataSet, "Customers");  
orderAdapter.Fill(dataSet, "Orders");  
  
connection.Close();  
  
DataRelation customerOrders = dataSet.Relations.Add(  
  "CustOrders", dataSet.Tables["Customers"].Columns["CustomerID"],  
  dataSet.Tables["Orders"].Columns["CustomerID"]);  
```  
  
 Étant donné que la propriété **Nested** de l'objet **DataRelation** n'a pas la valeur **true** pour ce **DataSet**, les objets enfants ne sont pas imbriqués dans les éléments parents lorsque ce **DataSet** est représenté sous forme de données XML.  La transformation de la représentation XML d'un **DataSet** contenant des **DataSets** connexes avec des relations de données non imbriquées peut entraîner un ralentissement des performances.  Il est recommandé d'imbriquer les relations de données.  Pour cela, attribuez à la propriété **Nested** la valeur  **true**.  Puis, écrivez le code dans la feuille de style XSLT qui utilise des expressions de requête XPath hiérarchisées de haut en bas pour rechercher et transformer les données.  
  
 L'exemple de code suivant illustre le résultat obtenu après appel du **WriteXml** sur le **DataSet**.  
  
```  
<CustomerOrders>  
  <Customers>  
    <CustomerID>ALFKI</CustomerID>  
    <CompanyName>Alfreds Futterkiste</CompanyName>  
  </Customers>  
  <Customers>  
    <CustomerID>ANATR</CustomerID>  
    <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
  </Customers>  
  <Orders>  
    <OrderID>10643</OrderID>  
    <CustomerID>ALFKI</CustomerID>  
    <OrderDate>1997-08-25T00:00:00</OrderDate>  
  </Orders>  
  <Orders>  
    <OrderID>10692</OrderID>  
    <CustomerID>ALFKI</CustomerID>  
    <OrderDate>1997-10-03T00:00:00</OrderDate>  
  </Orders>  
  <Orders>  
    <OrderID>10308</OrderID>  
    <CustomerID>ANATR</CustomerID>  
    <OrderDate>1996-09-18T00:00:00</OrderDate>  
  </Orders>  
</CustomerOrders>  
```  
  
 Notez que l'élément **Customers** et les éléments **Orders** sont représentés en tant qu'éléments frères.  Si vous souhaitiez que les éléments **Orders** apparaissent comme les enfants de leurs éléments parents respectifs, vous devez assigner la valeur **true** à la propriété **Nested** du **DataRelation** et ajouter ce qui suit :  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 Le code suivant montre la sortie que vous obtiendriez, avec les éléments **Orders** imbriqués dans leurs éléments parents respectifs.  
  
```  
<CustomerOrders>  
  <Customers>  
    <CustomerID>ALFKI</CustomerID>  
    <Orders>  
      <OrderID>10643</OrderID>  
      <CustomerID>ALFKI</CustomerID>  
      <OrderDate>1997-08-25T00:00:00</OrderDate>  
    </Orders>  
    <Orders>  
      <OrderID>10692</OrderID>  
      <CustomerID>ALFKI</CustomerID>  
      <OrderDate>1997-10-03T00:00:00</OrderDate>  
    </Orders>  
    <CompanyName>Alfreds Futterkiste</CompanyName>  
  </Customers>  
  <Customers>  
    <CustomerID>ANATR</CustomerID>  
    <Orders>  
      <OrderID>10308</OrderID>  
      <CustomerID>ANATR</CustomerID>  
      <OrderDate>1996-09-18T00:00:00</OrderDate>  
    </Orders>  
    <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
  </Customers>  
</CustomerOrders>  
```  
  
## Voir aussi  
 [Utilisation de XML dans un DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)   
 [Ajout d'objets DataRelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)   
 [Objets DataSet, DataTable et DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)