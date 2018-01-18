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
# <a name="nesting-datarelations"></a><span data-ttu-id="fb8cd-102">Imbrication de DataRelations</span><span class="sxs-lookup"><span data-stu-id="fb8cd-102">Nesting DataRelations</span></span>
<span data-ttu-id="fb8cd-103">Dans une représentation relationnelle des données, chaque table contient des lignes reliées aux lignes d'autres tables par une colonne ou un ensemble de colonnes.</span><span class="sxs-lookup"><span data-stu-id="fb8cd-103">In a relational representation of data, individual tables contain rows that are related to one another using a column or set of columns.</span></span> <span data-ttu-id="fb8cd-104">Dans l'objet <xref:System.Data.DataSet> ADO.NET, la relation entre les tables est implémentée à l'aide d'un objet <xref:System.Data.DataRelation>.</span><span class="sxs-lookup"><span data-stu-id="fb8cd-104">In the ADO.NET <xref:System.Data.DataSet>, the relationship between tables is implemented using a <xref:System.Data.DataRelation>.</span></span> <span data-ttu-id="fb8cd-105">Lorsque vous créez un **DataRelation**, les relations parent-enfant des colonnes sont managées uniquement via la relation.</span><span class="sxs-lookup"><span data-stu-id="fb8cd-105">When you create a **DataRelation**, the parent-child relationships of the columns are managed only through the relation.</span></span> <span data-ttu-id="fb8cd-106">Les tables et les colonnes constituent des entités distinctes.</span><span class="sxs-lookup"><span data-stu-id="fb8cd-106">The tables and columns are separate entities.</span></span> <span data-ttu-id="fb8cd-107">Dans la représentation hiérarchique des données proposée par XML, les relations parent-enfant sont représentés sous forme d'éléments parents contenant des éléments enfants imbriqués.</span><span class="sxs-lookup"><span data-stu-id="fb8cd-107">In the hierarchical representation of data that XML provides, the parent-child relationships are represented by parent elements that contain nested child elements.</span></span>  
  
 <span data-ttu-id="fb8cd-108">Pour faciliter l’imbrication des objets enfants quand un **DataSet** est synchronisé avec une <xref:System.Xml.XmlDataDocument> ou écrit sous forme de XML à l’aide de données **WriteXml**, le **DataRelation** expose un **Nested** propriété.</span><span class="sxs-lookup"><span data-stu-id="fb8cd-108">To facilitate the nesting of child objects when a **DataSet** is synchronized with an <xref:System.Xml.XmlDataDocument> or written as XML data using **WriteXml**, the **DataRelation** exposes a **Nested** property.</span></span> <span data-ttu-id="fb8cd-109">Définissant le **Nested** propriété d’un **DataRelation** à **true** entraîne des lignes de la relation d’imbrication dans la colonne parente lors de l’écriture en tant que données XML de l’enfant ou synchronisé avec un **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="fb8cd-109">Setting the **Nested** property of a **DataRelation** to **true** causes the child rows of the relation to be nested within the parent column when written as XML data or synchronized with an **XmlDataDocument**.</span></span> <span data-ttu-id="fb8cd-110">Le **Nested** propriété de la **DataRelation** est **false**, par défaut.</span><span class="sxs-lookup"><span data-stu-id="fb8cd-110">The **Nested** property of the **DataRelation** is **false**, by default.</span></span>  
  
 <span data-ttu-id="fb8cd-111">Par exemple, considérez les éléments suivants **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="fb8cd-111">For example, consider the following **DataSet**.</span></span>  
  
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
  
 <span data-ttu-id="fb8cd-112">Étant donné que la **Nested** propriété de la **DataRelation** objet n’est pas défini sur **true** pour ce **DataSet**, les objets enfants ne sont pas imbriqués dans les éléments parents lorsque ce **DataSet** est représenté sous forme de données XML.</span><span class="sxs-lookup"><span data-stu-id="fb8cd-112">Because the **Nested** property of the **DataRelation** object is not set to **true** for this **DataSet**, the child objects are not nested within the parent elements when this **DataSet** is represented as XML data.</span></span> <span data-ttu-id="fb8cd-113">Transformation de la représentation XML d’un **DataSet** contenant connexes **DataSet**connexes avec des relations de données non imbriquées peut entraîner un ralentissement des performances.</span><span class="sxs-lookup"><span data-stu-id="fb8cd-113">Transforming the XML representation of a **DataSet** that contains related **DataSet**s with non-nested data relations can cause slow performance.</span></span> <span data-ttu-id="fb8cd-114">Il est recommandé d'imbriquer les relations de données.</span><span class="sxs-lookup"><span data-stu-id="fb8cd-114">We recommend that you nest the data relations.</span></span> <span data-ttu-id="fb8cd-115">Pour ce faire, définissez la **Nested** propriété **true**.</span><span class="sxs-lookup"><span data-stu-id="fb8cd-115">To do this, set the **Nested** property to **true**.</span></span> <span data-ttu-id="fb8cd-116">Puis, écrivez le code dans la feuille de style XSLT qui utilise des expressions de requête XPath hiérarchisées de haut en bas pour rechercher et transformer les données.</span><span class="sxs-lookup"><span data-stu-id="fb8cd-116">Then write code in the XSLT style sheet that uses top-down hierarchical XPath query expressions to locate and transform the data.</span></span>  
  
 <span data-ttu-id="fb8cd-117">L’exemple de code suivant montre le résultat de l’appel **WriteXml** sur la **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="fb8cd-117">The following code example shows the result from calling **WriteXml** on the **DataSet**.</span></span>  
  
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
  
 <span data-ttu-id="fb8cd-118">Notez que la **clients** élément et la **commandes** éléments sont présentés en tant qu’éléments frères.</span><span class="sxs-lookup"><span data-stu-id="fb8cd-118">Note that the **Customers** element and the **Orders** elements are shown as sibling elements.</span></span> <span data-ttu-id="fb8cd-119">Si vous souhaitiez le **commandes** éléments s’affichent en tant qu’enfants de leurs éléments parents respectifs, le **Nested** propriété de la **DataRelation** devra être définie à **true** et ajouter les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="fb8cd-119">If you wanted the **Orders** elements to show up as children of their respective parent elements, the **Nested** property of the **DataRelation** would need to be set to **true** and you would add the following:</span></span>  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 <span data-ttu-id="fb8cd-120">Le code suivant montre ce que le résultat ressemble à, avec le **commandes** les éléments imbriqués dans leurs éléments parents respectifs.</span><span class="sxs-lookup"><span data-stu-id="fb8cd-120">The following code shows what the resulting output would look like, with the **Orders** elements nested within their respective parent elements.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fb8cd-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fb8cd-121">See Also</span></span>  
 [<span data-ttu-id="fb8cd-122">Utilisation de XML dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="fb8cd-122">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="fb8cd-123">Ajout de DataRelations</span><span class="sxs-lookup"><span data-stu-id="fb8cd-123">Adding DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)  
 [<span data-ttu-id="fb8cd-124">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="fb8cd-124">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="fb8cd-125">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="fb8cd-125">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
