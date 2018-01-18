---
title: Imbrication de DataRelations
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
ms.assetid: 9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c057e836e8903fc2f5cb28f74858be97d2ffcc14
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="nesting-datarelations"></a>Imbrication de DataRelations
Dans une représentation relationnelle des données, chaque table contient des lignes reliées aux lignes d'autres tables par une colonne ou un ensemble de colonnes. Dans l'objet <xref:System.Data.DataSet> ADO.NET, la relation entre les tables est implémentée à l'aide d'un objet <xref:System.Data.DataRelation>. Lorsque vous créez un **DataRelation**, les relations parent-enfant des colonnes sont managées uniquement via la relation. Les tables et les colonnes constituent des entités distinctes. Dans la représentation hiérarchique des données proposée par XML, les relations parent-enfant sont représentés sous forme d'éléments parents contenant des éléments enfants imbriqués.  
  
 Pour faciliter l’imbrication des objets enfants quand un **DataSet** est synchronisé avec une <xref:System.Xml.XmlDataDocument> ou écrit sous forme de XML à l’aide de données **WriteXml**, le **DataRelation** expose un **Nested** propriété. Définissant le **Nested** propriété d’un **DataRelation** à **true** entraîne des lignes de la relation d’imbrication dans la colonne parente lors de l’écriture en tant que données XML de l’enfant ou synchronisé avec un **XmlDataDocument**. Le **Nested** propriété de la **DataRelation** est **false**, par défaut.  
  
 Par exemple, considérez les éléments suivants **DataSet**.  
  
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
  
 Étant donné que la **Nested** propriété de la **DataRelation** objet n’est pas défini sur **true** pour ce **DataSet**, les objets enfants ne sont pas imbriqués dans les éléments parents lorsque ce **DataSet** est représenté sous forme de données XML. Transformation de la représentation XML d’un **DataSet** contenant connexes **DataSet**connexes avec des relations de données non imbriquées peut entraîner un ralentissement des performances. Il est recommandé d'imbriquer les relations de données. Pour ce faire, définissez la **Nested** propriété **true**. Puis, écrivez le code dans la feuille de style XSLT qui utilise des expressions de requête XPath hiérarchisées de haut en bas pour rechercher et transformer les données.  
  
 L’exemple de code suivant montre le résultat de l’appel **WriteXml** sur la **DataSet**.  
  
```xml  
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
  
 Notez que la **clients** élément et la **commandes** éléments sont présentés en tant qu’éléments frères. Si vous souhaitiez le **commandes** éléments s’affichent en tant qu’enfants de leurs éléments parents respectifs, le **Nested** propriété de la **DataRelation** devra être définie à **true** et ajouter les éléments suivants :  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 Le code suivant montre ce que le résultat ressemble à, avec le **commandes** les éléments imbriqués dans leurs éléments parents respectifs.  
  
```xml  
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
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de XML dans un DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Ajout de DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)  
 [DataSets, DataTables et DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
