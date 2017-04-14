---
title: "Annotation de DataSets typ&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# Annotation de DataSets typ&#233;s
Les annotations vous permettent de modifier le nom des éléments de votre objet <xref:System.Data.DataSet> typé sans pour autant modifier le schéma sous\-jacent.  Si vous modifiiez le nom des éléments de votre schéma sous\-jacent, le **DataSet** typé ferait référence à des objets qui n'existent pas dans la source de données et perdrait des références vers des objets qui existent bien dans la source de données.  
  
 En utilisant des annotations, vous pouvez personnaliser le nom des objets de votre **DataSet** typé au profit de noms plus évocateurs qui rendront le code plus aisé à lire et votre **DataSet** typé plus facile à utiliser par les clients, tout en laissant intact le schéma sous\-jacent.  Par exemple, l'élément de schéma suivant pour la table **Customers** de la base de données **Northwind** donnerait un objet **DataRow** nommé **CustomersRow** et un objet <xref:System.Data.DataRowCollection> nommé **Customers**.  
  
```  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 Le nom **Customers** pour un **DataRowCollection** est évocateur dans un code client, mais le nom **CustomersRow** pour un **DataRow** est équivoque car il s'agit d'un objet unique.  C'est pourquoi, dans un scénario classique, il serait fait référence à l'objet sans l'identificateur **Row**, pour donner simplement **Customer**.  La solution consiste à annoter le schéma et à identifier de nouveaux noms pour les objets **DataRow** et **DataRowCollection**.  Voici une version annotée du précédent schéma.  
  
```  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 En assignant à **typedName** la valeur **Customer**, vous obtenez un objet **DataRow** nommé **Customer**.  En assignant à **typedPlural** la valeur **Customers**, vous conservez le nom **Customers** pour le **DataRowCollection**.  
  
 Le tableau suivant présente les différentes annotations disponibles.  
  
|Annotation|Description|  
|----------------|-----------------|  
|**typedName**|Nom de l'objet.|  
|**typedPlural**|Nom d'une collection d'objets.|  
|**typedParent**|Nom de l'objet lorsqu'il y est fait référence dans une relation parente.|  
|**typedChildren**|Nom de la méthode permettant de retourner des objets d'une relation enfant.|  
|**nullValue**|Valeur à utiliser si la valeur sous\-jacente est **DBNull**.  Consultez le tableau suivant pour les annotations **nullValue**.  La valeur par défaut est **\_throw**.|  
  
 Le tableau suivant présente les valeurs qui peuvent être spécifiées pour l'annotation **nullValue**.  
  
|Valeur nullValue|Description|  
|----------------------|-----------------|  
|*Replacement Value*|Spécifier une valeur à retourner.  La valeur retournée doit correspondre au type de l'élément.  Par exemple, utilisez `nullValue="0"` pour retourner 0 pour les champs de type null integer \(entier nul\).|  
|**\_throw**|Levée d'une exception.  Il s'agit de la valeur par défaut.|  
|**\_null**|Retourner une référence null ou lever une exception si un type primitif est rencontré.|  
|**\_empty**|Pour des chaînes, retourner **String.Empty**, dans les autres cas, retourner un objet créé à partir d'un constructeur vide.  Si un type primitif est rencontré, lever une exception.|  
  
 Le tableau suivant présente les valeurs par défaut pour les objets d'un **DataSet** typé et les annotations disponibles.  
  
|Objet\/méthode\/événement|Par défaut|Annotation|  
|-------------------------------|----------------|----------------|  
|**DataTable**|TableNameDataTable|typedPlural|  
|Méthodes de **DataTable**|NewTableNameRow<br /><br /> AddTableNameRow<br /><br /> DeleteTableNameRow|typedName|  
|**DataRowCollection**|TableName|typedPlural|  
|**DataRow**|TableNameRow|typedName|  
|**DataColumn**|DataTable.ColumnNameColumn<br /><br /> DataRow.ColumnName|typedName|  
|**Propriété**|PropertyName|typedName|  
|Accesseur **Child**|GetChildTableNameRows|typedChildren|  
|Accesseur **Parent**|TableNameRow|typedParent|  
|Événements de **DataSet**|TableNameRowChangeEvent<br /><br /> TableNameRowChangeEventHandler|typedName|  
  
 Pour utiliser des annotations de **DataSet** typé, vous devez inclure la référence **xmlns** suivante dans votre schéma en langage XSD \(XML Schema Definition\).  \(Pour créer une définition XSD à partir de tables de base de données, consultez <xref:System.Data.DataSet.WriteXmlSchema%2A> ou [Utilisation de datasets dans Visual Studio](http://msdn.microsoft.com/library/8bw9ksd6.aspx).\)  
  
```  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 L'exemple suivant est un schéma annoté qui expose la table **Customers** de la base de données **Northwind** et inclut une relation avec la table **Orders**.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet"   
      xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
      xmlns=""   
      xmlns:xs="http://www.w3.org/2001/XMLSchema"   
      xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers" codegen:typedName="Customer"  
codegen:typedPlural="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID" type="xs:string" minOccurs="0" />  
              <xs:element name="CompanyName"  
codegen:typedName="CompanyName" type="xs:string" minOccurs="0" />  
              <xs:element name="Phone" codegen:typedName="Phone"  
codegen:nullValue="" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
        <xs:element name="Orders" codegen:typedName="Order"  
codegen:typedPlural="Orders">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="OrderID" codegen:typedName="OrderID"  
type="xs:int" minOccurs="0" />  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID"  
                 codegen:nullValue="" type="xs:string" minOccurs="0" />  
              <xs:element name="EmployeeID"  
codegen:typedName="EmployeeID" codegen:nullValue="0"   
type="xs:int" minOccurs="0" />  
              <xs:element name="OrderAdapter"  
codegen:typedName="OrderAdapter"  
codegen:nullValue="1980-01-01T00:00:00"   
type="xs:dateTime" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
    <xs:unique name="Constraint1">  
      <xs:selector xpath=".//Customers" />  
      <xs:field xpath="CustomerID" />  
    </xs:unique>  
    <xs:keyref name="CustOrders" refer="Constraint1"  
codegen:typedParent="Customer" codegen:typedChildren="GetOrders">  
      <xs:selector xpath=".//Orders" />  
      <xs:field xpath="CustomerID" />  
    </xs:keyref>  
  </xs:element>  
</xs:schema>  
```  
  
 L'exemple de code suivant utilise un **DataSet** fortement typé créé à partir du schéma précédent.  Il utilise un objet <xref:System.Data.SqlClient.SqlDataAdapter> pour remplir la table **Customers** et un autre objet <xref:System.Data.SqlClient.SqlDataAdapter> pour remplir la table **Orders**.  Le **DataSet** fortement typé définit le **DataRelations**.  
  
```vb  
' Assumes a valid SqlConnection object named connection.  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT CustomerID, CompanyName, Phone FROM Customers", &  
    connection)  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders", &  
    connection)  
  
' Populate a strongly typed DataSet.  
connection.Open()  
Dim customers As CustomerDataSet = New CustomerDataSet()  
customerAdapter.Fill(customers, "Customers")  
orderAdapter.Fill(customers, "Orders")  
connection.Close()  
  
' Add a strongly typed event.  
AddHandler customers.Customers.CustomerChanged, &  
    New CustomerDataSet.CustomerChangeEventHandler( _  
    AddressOf OnCustomerChanged)  
  
' Add a strongly typed DataRow.  
Dim newCustomer As CustomerDataSet.Customer = _  
    customers.Customers.NewCustomeromer()  
newCustomer.CustomerID = "NEW01"  
newCustomer.CompanyName = "My New Company"  
customers.Customers.AddCustomer(newCustomer)  
  
' Navigate the child relation.  
Dim customer As CustomerDataSet.Customer  
Dim order As CustomerDataSet.Order  
  
For Each customer In customers.Customers  
  Console.WriteLine(customer.CustomerID)  
  For Each order In customer.GetOrders()  
    Console.WriteLine(vbTab & order.OrderID)  
  Next  
Next  
  
Private Shared Sub OnCustomerChanged( _  
    sender As Object, e As CustomerDataSet.CustomerChangeEvent)  
  
End Sub  
  
```  
  
```csharp  
// Assumes a valid SqlConnection object named connection.  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
    "SELECT CustomerID, CompanyName, Phone FROM Customers",  
    connection);  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders",   
    connection);  
  
// Populate a strongly typed DataSet.  
connection.Open();  
CustomerDataSet customers = new CustomerDataSet();  
customerAdapter.Fill(customers, "Customers");  
orderAdapter.Fill(customers, "Orders");  
connection.Close();  
  
// Add a strongly typed event.  
customers.Customers.CustomerChanged += new   
  CustomerDataSet.CustomerChangeEventHandler(OnCustomerChanged);  
  
// Add a strongly typed DataRow.  
CustomerDataSet.Customer newCustomer =   
    customers.Customers.NewCustomeromer();  
newCustomer.CustomerID = "NEW01";  
newCustomer.CompanyName = "My New Company";  
customers.Customers.AddCustomer(newCustomer);  
  
// Navigate the child relation.  
foreach(CustomerDataSet.Customer customer in customers.Customers)  
{  
  Console.WriteLine(customer.CustomerID);  
  foreach(CustomerDataSet.Order order in customer.GetOrders())  
    Console.WriteLine("\t" + order.OrderID);  
}  
  
protected static void OnCustomerChanged(object sender, CustomerDataSet.CustomerChangeEvent e)  
    {  
  
    }  
```  
  
## Voir aussi  
 <xref:System.Data.DataColumnCollection>   
 <xref:System.Data.DataSet>   
 [DataSets typés](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)   
 [Objets DataSet, DataTable et DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)