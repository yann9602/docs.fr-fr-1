---
title: "Synchronisation d’un DataSet et d’un XmlDataDocument"
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
ms.assetid: fbc96fa9-b5d1-4f97-b099-c89b0e14ce2c
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: bea557d8a09ba874fb4b6a3f3a54c09dac4778cc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="synchronizing-a-dataset-with-an-xmldatadocument"></a><span data-ttu-id="184c0-102">Synchronisation d’un DataSet et d’un XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="184c0-102">Synchronizing a DataSet with an XmlDataDocument</span></span>
<span data-ttu-id="184c0-103">Cette section décrit l'une des étapes du traitement d'un bon de commande à l'aide d'un objet <xref:System.Data.DataSet> fortement typé, synchronisé avec un objet <xref:System.Xml.XmlDataDocument>.</span><span class="sxs-lookup"><span data-stu-id="184c0-103">This section demonstrates one step in the processing of a purchase order, using a strongly typed <xref:System.Data.DataSet> synchronized with an <xref:System.Xml.XmlDataDocument>.</span></span> <span data-ttu-id="184c0-104">Les exemples suivants créent un **DataSet** avec un schéma minimal correspondant uniquement une partie du document XML source.</span><span class="sxs-lookup"><span data-stu-id="184c0-104">The examples that follow create a **DataSet** with a minimized schema that matches only a portion of the source XML document.</span></span> <span data-ttu-id="184c0-105">Les exemples utilisent une **XmlDataDocument** pour préserver la fidélité du document XML source, l’activation de la **DataSet** à être utilisé pour exposer un sous-ensemble du document XML.</span><span class="sxs-lookup"><span data-stu-id="184c0-105">The examples use an **XmlDataDocument** to preserve the fidelity of the source XML document, enabling the **DataSet** to be used to expose a subset of the XML document.</span></span>  
  
 <span data-ttu-id="184c0-106">Le document XML suivant contient toutes les informations relatives à un bon de commande : les informations client, les articles commandés, les informations de livraison, etc.</span><span class="sxs-lookup"><span data-stu-id="184c0-106">The following XML document contains all the information pertaining to a purchase order: customer information, items ordered, shipping information, and so on.</span></span>  
  
```xml  
<?xml version="1.0" standalone="yes"?>  
<PurchaseOrder>  
  <Customers>  
    <CustomerID>CHOPS</CustomerID>  
    <Orders>  
      <OrderID>10966</OrderID>  
      <OrderDetails>  
        <OrderID>10966</OrderID>  
        <ProductID>37</ProductID>  
        <UnitPrice>26</UnitPrice>  
        <Quantity>8</Quantity>  
        <Discount>0</Discount>  
      </OrderDetails>  
      <OrderDetails>  
        <OrderID>10966</OrderID>  
        <ProductID>56</ProductID>  
        <UnitPrice>38</UnitPrice>  
        <Quantity>12</Quantity>  
        <Discount>0.15</Discount>  
      </OrderDetails>  
      <OrderDetails>  
        <OrderID>10966</OrderID>  
        <ProductID>62</ProductID>  
        <UnitPrice>49.3</UnitPrice>  
        <Quantity>12</Quantity>  
        <Discount>0.15</Discount>  
      </OrderDetails>  
      <CustomerID>CHOPS</CustomerID>  
      <EmployeeID>4</EmployeeID>  
      <OrderDate>1998-03-20T00:00:00.0000000</OrderDate>  
      <RequiredDate>1998-04-17T00:00:00.0000000</RequiredDate>  
      <ShippedDate>1998-04-08T00:00:00.0000000</ShippedDate>  
      <ShipVia>1</ShipVia>  
      <Freight>27.19</Freight>  
      <ShipName>Chop-suey Chinese</ShipName>  
      <ShipAddress>Hauptstr. 31</ShipAddress>  
      <ShipCity>Bern</ShipCity>  
      <ShipPostalCode>3012</ShipPostalCode>  
      <ShipCountry>Switzerland</ShipCountry>  
    </Orders>  
    <CompanyName>Chop-suey Chinese</CompanyName>  
    <ContactName>Yang Wang</ContactName>  
    <ContactTitle>Owner</ContactTitle>  
    <Address>Hauptstr. 29</Address>  
    <City>Bern</City>  
    <PostalCode>3012</PostalCode>  
    <Country>Switzerland</Country>  
    <Phone>0452-076545</Phone>  
  </Customers>  
  <Shippers>  
    <ShipperID>1</ShipperID>  
    <CompanyName>Speedy Express</CompanyName>  
    <Phone>(503) 555-0100</Phone>  
  </Shippers>  
  <Shippers>  
    <ShipperID>2</ShipperID>  
    <CompanyName>United Package</CompanyName>  
    <Phone>(503) 555-0101</Phone>  
  </Shippers>  
  <Shippers>  
    <ShipperID>3</ShipperID>  
    <CompanyName>Federal Shipping</CompanyName>  
    <Phone>(503) 555-0102</Phone>  
  </Shippers>  
  <Products>  
    <ProductID>37</ProductID>  
    <ProductName>Gravad lax</ProductName>  
    <QuantityPerUnit>12 - 500 g pkgs.</QuantityPerUnit>  
    <UnitsInStock>11</UnitsInStock>  
    <UnitsOnOrder>50</UnitsOnOrder>  
    <ReorderLevel>25</ReorderLevel>  
  </Products>  
  <Products>  
    <ProductID>56</ProductID>  
    <ProductName>Gnocchi di nonna Alice</ProductName>  
    <QuantityPerUnit>24 - 250 g pkgs.</QuantityPerUnit>  
    <UnitsInStock>21</UnitsInStock>  
    <UnitsOnOrder>10</UnitsOnOrder>  
    <ReorderLevel>30</ReorderLevel>  
  </Products>  
  <Products>  
    <ProductID>62</ProductID>  
    <ProductName>Tarte au sucre</ProductName>  
    <QuantityPerUnit>48 pies</QuantityPerUnit>  
    <UnitsInStock>17</UnitsInStock>  
    <UnitsOnOrder>0</UnitsOnOrder>  
    <ReorderLevel>0</ReorderLevel>  
  </Products>  
</PurchaseOrder>  
```  
  
 <span data-ttu-id="184c0-107">L'une des étapes du traitement des informations du bon de commande contenues dans le document XML précédent consiste à satisfaire la commande en allant chercher les articles dans le stock actuel de la société.</span><span class="sxs-lookup"><span data-stu-id="184c0-107">One step in processing the purchase order information contained in the preceding XML document is for the order to be filled from the company's current inventory.</span></span> <span data-ttu-id="184c0-108">L'employé chargé de cette tâche n'a pas besoin pour ce faire de voir l'intégralité du contenu du bon de commande ; il lui suffit de connaître les références des produits commandés.</span><span class="sxs-lookup"><span data-stu-id="184c0-108">The employee responsible for filling the order from the company's warehouse does not need to see the entire contents of the purchase order; they only need to see the product information for the order.</span></span> <span data-ttu-id="184c0-109">Pour exposer uniquement les informations de produit à partir du document XML, créer un fortement typées **DataSet** avec un schéma, écrit sous forme de schéma XML Schema definition language (XSD), qui corresponde aux produits et quantités commandés.</span><span class="sxs-lookup"><span data-stu-id="184c0-109">To expose only the product information from the XML document, create a strongly typed **DataSet** with a schema, written as XML Schema definition language (XSD) schema, that maps to the products and quantities ordered.</span></span> <span data-ttu-id="184c0-110">Pour plus d’informations sur fortement typées **DataSet** , consultez [typés](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="184c0-110">For more information about strongly typed **DataSet** objects, see [Typed DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span></span>  
  
 <span data-ttu-id="184c0-111">Le code suivant montre le schéma à partir de laquelle fortement typé **DataSet** est généré pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="184c0-111">The following code shows the schema from which the strongly typed **DataSet** is generated for this sample.</span></span>  
  
```xml  
<?xml version="1.0" standalone="yes"?>  
<xs:schema id="OrderDetail" xmlns=""   
                            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
                            xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"   
                            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="OrderDetail" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="OrderDetails" codegen:typedName="LineItem" codegen:typedPlural="LineItems">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="OrderID" type="xs:int" minOccurs="0" codegen:typedName="OrderID"/>  
              <xs:element name="Quantity" type="xs:short" minOccurs="0" codegen:typedName="Quantity"/>  
              <xs:element name="ProductID" type="xs:int" minOccurs="0" codegen:typedName="ProductID"/>  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
        <xs:element name="Products" codegen:typedName="Product" codegen:typedPlural="Products">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="ProductID" type="xs:int" minOccurs="0" codegen:typedName="ProductID"/>  
              <xs:element name="ProductName" type="xs:string" minOccurs="0" codegen:typedName="ProductName"/>  
              <xs:element name="QuantityPerUnit" type="xs:string" minOccurs="0" codegen:typedName="QuantityPerUnit"/>  
              <xs:element name="UnitsInStock" type="xs:short" minOccurs="0" codegen:typedName="UnitsInStock"/>  
              <xs:element name="UnitsOnOrder" type="xs:short" minOccurs="0" codegen:typedName="UnitsOnOrder"/>  
              <xs:element name="ReorderLevel" type="xs:short" minOccurs="0" codegen:typedName="ReorderLevel"/>  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
    <xs:unique name="Constraint1">  
      <xs:selector xpath=".//Products" />  
      <xs:field xpath="ProductID" />  
    </xs:unique>  
    <xs:keyref name="Relation1" refer="Constraint1" codegen:typedChildren="GetLineItems" codegen:typedParent="Product">  
      <xs:selector xpath=".//OrderDetails" />  
      <xs:field xpath="ProductID" />  
    </xs:keyref>  
  </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="184c0-112">Notez que seules les informations à partir de la **OrderDetails** et **produits** éléments du document XML d’origine sont inclus dans le schéma pour le **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="184c0-112">Notice that only information from the **OrderDetails** and **Products** elements of the original XML document are included in the schema for the **DataSet**.</span></span> <span data-ttu-id="184c0-113">Synchronisation de la **DataSet** avec un **XmlDataDocument** garantit que les éléments non inclus dans le **DataSet** seront conservés avec le document XML.</span><span class="sxs-lookup"><span data-stu-id="184c0-113">Synchronizing the **DataSet** with an **XmlDataDocument** ensures that the elements not included in the **DataSet** will persist with the XML document.</span></span>  
  
 <span data-ttu-id="184c0-114">Avec fortement typé **DataSet** généré à partir du schéma XML (avec un espace de noms **Northwind.FillOrder**), une partie du document XML d’origine peut être exposée en synchronisant le  **Jeu de données** avec la **XmlDataDocument** chargé à partir du document XML source.</span><span class="sxs-lookup"><span data-stu-id="184c0-114">With the strongly typed **DataSet** generated from the XML Schema (with a namespace of **Northwind.FillOrder**), a portion of the original XML document can be exposed by synchronizing the **DataSet** with the **XmlDataDocument** loaded from the source XML document.</span></span> <span data-ttu-id="184c0-115">Notez que la **DataSet** généré à partir du schéma contient la structure, mais aucune donnée.</span><span class="sxs-lookup"><span data-stu-id="184c0-115">Notice that the **DataSet** generated from the schema contains structure but no data.</span></span> <span data-ttu-id="184c0-116">Les données sont renseignées lorsque vous chargez le XML dans le **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="184c0-116">The data is filled in when you load the XML into the **XmlDataDocument**.</span></span> <span data-ttu-id="184c0-117">Si vous tentez de charger un **XmlDataDocument** qui a été synchronisé avec un **DataSet** qui contient déjà des données, une exception sera levée.</span><span class="sxs-lookup"><span data-stu-id="184c0-117">If you attempt to load an **XmlDataDocument** that has been synchronized with a **DataSet** that already contains data, an exception will be thrown.</span></span>  
  
 <span data-ttu-id="184c0-118">Après le **DataSet** (et **XmlDataDocument**) a été mis à jour, le **XmlDataDocument** peut écrire le document XML modifié avec les éléments ignorés par le **DataSet** intact, comme indiqué ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="184c0-118">After the **DataSet** (and the **XmlDataDocument**) has been updated, the **XmlDataDocument** can then write out the modified XML document with the elements ignored by the **DataSet** still intact, as shown below.</span></span> <span data-ttu-id="184c0-119">Dans le scénario du bon de commande, une fois que les articles commandés ont été sortis du magasin, le document XML modifié peut passer à l'étape suivante du traitement de la commande, peut-être au service livraison de la société.</span><span class="sxs-lookup"><span data-stu-id="184c0-119">In the purchase order scenario, after the order items have been filled, the modified XML document can then be passed on to the next step in the order process, perhaps to the company's shipping department.</span></span>  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Xml  
Imports Northwind.FillOrder  
  
Public class Sample  
  Public Shared Sub Main()  
  
    Dim orderDS As OrderDetail = New OrderDetail  
  
    Dim xmlDocument As XmlDataDocument = New XmlDataDocument(orderDS)   
  
    xmlDocument.Load("Order.xml")  
  
    Dim orderItem As OrderDetail.LineItem  
    Dim product As OrderDetail.Product  
  
    For Each orderItem In orderDS.LineItems  
      product = orderItem.Product  
  
      ' Remove quantity from the current stock.  
      product.UnitsInStock = CType(product.UnitsInStock - orderItem.Quantity, Short)  
  
      ' If the remaining stock is less than the reorder level, order more.  
      If ((product.UnitsInStock + product.UnitsOnOrder) < product.ReorderLevel) Then  
        product.UnitsOnOrder = CType(product.UnitsOnOrder + product.ReorderLevel, Short)  
      End If  
    Next  
  
    xmlDocument.Save("Order_out.xml")  
  End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Xml;  
using Northwind.FillOrder;  
  
public class Sample  
{  
  public static void Main()  
  {  
    OrderDetail orderDS = new OrderDetail();   
  
    XmlDataDocument xmlDocument = new XmlDataDocument(orderDS);   
  
    xmlDocument.Load("Order.xml");  
  
    foreach (OrderDetail.LineItem orderItem in orderDS.LineItems)  
    {  
      OrderDetail.Product product = orderItem.Product;  
  
      // Remove quantity from the current stock.  
      product.UnitsInStock = (short)(product.UnitsInStock - orderItem.Quantity);  
  
      // If the remaining stock is less than the reorder level, order more.  
      if ((product.UnitsInStock + product.UnitsOnOrder) < product.ReorderLevel)  
        product.UnitsOnOrder = (short)(product.UnitsOnOrder + product.ReorderLevel);  
    }  
  
    xmlDocument.Save("Order_out.xml");  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="184c0-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="184c0-120">See Also</span></span>  
 [<span data-ttu-id="184c0-121">Synchronisation DataSet et XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="184c0-121">DataSet and XmlDataDocument Synchronization</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)  
 [<span data-ttu-id="184c0-122">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="184c0-122">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
