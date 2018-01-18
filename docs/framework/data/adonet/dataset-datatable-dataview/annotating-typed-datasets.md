---
title: "Annotation de DataSet typés"
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
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: cc09f3f9b43b70b7f9b302d7a9d75428b5a0e6c7
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="annotating-typed-datasets"></a><span data-ttu-id="804e7-102">Annotation de DataSet typés</span><span class="sxs-lookup"><span data-stu-id="804e7-102">Annotating Typed DataSets</span></span>
<span data-ttu-id="804e7-103">Les annotations vous permettent de modifier le nom des éléments de votre objet <xref:System.Data.DataSet> typé sans pour autant modifier le schéma sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="804e7-103">Annotations enable you to modify the names of the elements in your typed <xref:System.Data.DataSet> without modifying the underlying schema.</span></span> <span data-ttu-id="804e7-104">Modifier les noms des éléments de votre schéma sous-jacent provoquerait typées **DataSet** pour faire référence aux objets que vous ne pas exister dans la source de données, ainsi que perdrait des références aux objets qui existent dans la source de données.</span><span class="sxs-lookup"><span data-stu-id="804e7-104">Modifying the names of the elements in your underlying schema would cause the typed **DataSet** to refer to objects that do not exist in the data source, as well as lose a reference to the objects that do exist in the data source.</span></span>  
  
 <span data-ttu-id="804e7-105">À l’aide des annotations, vous pouvez personnaliser les noms des objets dans votre typé **DataSet** avec des noms plus explicites, rendre le code plus lisible et votre typé **DataSet** plus facile pour les clients à utiliser, en laissant schéma sous-jacent intact.</span><span class="sxs-lookup"><span data-stu-id="804e7-105">Using annotations, you can customize the names of objects in your typed **DataSet** with more meaningful names, making code more readable and your typed **DataSet** easier for clients to use, while leaving underlying schema intact.</span></span> <span data-ttu-id="804e7-106">Par exemple, l’élément de schéma suivant pour la **clients** table de la **Northwind** entraînerait la base de données un **DataRow** nom d’objet du  **CustomersRow** et un <xref:System.Data.DataRowCollection> nommé **clients**.</span><span class="sxs-lookup"><span data-stu-id="804e7-106">For example, the following schema element for the **Customers** table of the **Northwind** database would result in a **DataRow** object name of **CustomersRow** and a <xref:System.Data.DataRowCollection> named **Customers**.</span></span>  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="804e7-107">A **DataRowCollection** nom de **clients** est significative dans le code client, mais un **DataRow** nom de **CustomersRow** est trompeur s’agissant d’un objet unique.</span><span class="sxs-lookup"><span data-stu-id="804e7-107">A **DataRowCollection** name of **Customers** is meaningful in client code, but a **DataRow** name of **CustomersRow** is misleading because it is a single object.</span></span> <span data-ttu-id="804e7-108">En outre, en commun des scénarios, l’objet est désigné sans le **ligne** identificateur et à la place est simplement désigné comme un **client** objet.</span><span class="sxs-lookup"><span data-stu-id="804e7-108">Also, in common scenarios, the object would be referred to without the **Row** identifier and instead would be simply referred to as a **Customer** object.</span></span> <span data-ttu-id="804e7-109">La solution consiste à annoter le schéma et à identifier de nouveaux noms pour les **DataRow** et **DataRowCollection** objets.</span><span class="sxs-lookup"><span data-stu-id="804e7-109">The solution is to annotate the schema and identify new names for the **DataRow** and **DataRowCollection** objects.</span></span> <span data-ttu-id="804e7-110">Voici une version annotée du précédent schéma.</span><span class="sxs-lookup"><span data-stu-id="804e7-110">Following is the annotated version of the previous schema.</span></span>  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="804e7-111">En spécifiant un **typedName** valeur **client** entraîne une **DataRow** nom de l’objet de **client**.</span><span class="sxs-lookup"><span data-stu-id="804e7-111">Specifying a **typedName** value of **Customer** will result in a **DataRow** object name of **Customer**.</span></span> <span data-ttu-id="804e7-112">En spécifiant un **typedPlural** valeur **clients** conserve la **DataRowCollection** nom de **clients**.</span><span class="sxs-lookup"><span data-stu-id="804e7-112">Specifying a **typedPlural** value of **Customers** preserves the **DataRowCollection** name of **Customers**.</span></span>  
  
 <span data-ttu-id="804e7-113">Le tableau suivant présente les différentes annotations disponibles.</span><span class="sxs-lookup"><span data-stu-id="804e7-113">The following table shows the annotations available for use.</span></span>  
  
|<span data-ttu-id="804e7-114">Annotation</span><span class="sxs-lookup"><span data-stu-id="804e7-114">Annotation</span></span>|<span data-ttu-id="804e7-115">Description</span><span class="sxs-lookup"><span data-stu-id="804e7-115">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="804e7-116">**typedName**</span><span class="sxs-lookup"><span data-stu-id="804e7-116">**typedName**</span></span>|<span data-ttu-id="804e7-117">Nom de l'objet.</span><span class="sxs-lookup"><span data-stu-id="804e7-117">Name of the object.</span></span>|  
|<span data-ttu-id="804e7-118">**typedPlural**</span><span class="sxs-lookup"><span data-stu-id="804e7-118">**typedPlural**</span></span>|<span data-ttu-id="804e7-119">Nom d’une collection d’objets.</span><span class="sxs-lookup"><span data-stu-id="804e7-119">Name of a collection of objects.</span></span>|  
|<span data-ttu-id="804e7-120">**typedParent**</span><span class="sxs-lookup"><span data-stu-id="804e7-120">**typedParent**</span></span>|<span data-ttu-id="804e7-121">Nom de l'objet lorsqu'il y est fait référence dans une relation parente.</span><span class="sxs-lookup"><span data-stu-id="804e7-121">Name of the object when referred to in a parent relationship.</span></span>|  
|<span data-ttu-id="804e7-122">**typedChildren**</span><span class="sxs-lookup"><span data-stu-id="804e7-122">**typedChildren**</span></span>|<span data-ttu-id="804e7-123">Nom de la méthode permettant de retourner des objets d'une relation enfant.</span><span class="sxs-lookup"><span data-stu-id="804e7-123">Name of the method to return objects from a child relationship.</span></span>|  
|<span data-ttu-id="804e7-124">**nullValue**</span><span class="sxs-lookup"><span data-stu-id="804e7-124">**nullValue**</span></span>|<span data-ttu-id="804e7-125">Valeur si la valeur sous-jacente est **DBNull**.</span><span class="sxs-lookup"><span data-stu-id="804e7-125">Value if the underlying value is **DBNull**.</span></span> <span data-ttu-id="804e7-126">Consultez le tableau suivant pour **nullValue** annotations.</span><span class="sxs-lookup"><span data-stu-id="804e7-126">See the following table for **nullValue** annotations.</span></span> <span data-ttu-id="804e7-127">La valeur par défaut est **_throw**.</span><span class="sxs-lookup"><span data-stu-id="804e7-127">The default is **_throw**.</span></span>|  
  
 <span data-ttu-id="804e7-128">Le tableau suivant montre les valeurs qui peuvent être spécifiés pour le **nullValue** annotation.</span><span class="sxs-lookup"><span data-stu-id="804e7-128">The following table shows the values that can be specified for the **nullValue** annotation.</span></span>  
  
|<span data-ttu-id="804e7-129">Valeur nullValue</span><span class="sxs-lookup"><span data-stu-id="804e7-129">nullValue Value</span></span>|<span data-ttu-id="804e7-130">Description</span><span class="sxs-lookup"><span data-stu-id="804e7-130">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="804e7-131">*Valeur de remplacement*</span><span class="sxs-lookup"><span data-stu-id="804e7-131">*Replacement Value*</span></span>|<span data-ttu-id="804e7-132">Spécifier une valeur à retourner.</span><span class="sxs-lookup"><span data-stu-id="804e7-132">Specify a value to be returned.</span></span> <span data-ttu-id="804e7-133">La valeur retournée doit correspondre au type de l'élément.</span><span class="sxs-lookup"><span data-stu-id="804e7-133">The returned value must match the type of the element.</span></span> <span data-ttu-id="804e7-134">Par exemple, utilisez `nullValue="0"` pour retourner 0 pour les champs de type null integer (entier nul).</span><span class="sxs-lookup"><span data-stu-id="804e7-134">For example, use `nullValue="0"` to return 0 for null integer fields.</span></span>|  
|<span data-ttu-id="804e7-135">**_throw**</span><span class="sxs-lookup"><span data-stu-id="804e7-135">**_throw**</span></span>|<span data-ttu-id="804e7-136">Levée d'une exception.</span><span class="sxs-lookup"><span data-stu-id="804e7-136">Throw an exception.</span></span> <span data-ttu-id="804e7-137">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="804e7-137">This is the default.</span></span>|  
|<span data-ttu-id="804e7-138">**_null**</span><span class="sxs-lookup"><span data-stu-id="804e7-138">**_null**</span></span>|<span data-ttu-id="804e7-139">Retourner une référence null ou lever une exception si un type primitif est rencontré.</span><span class="sxs-lookup"><span data-stu-id="804e7-139">Return a null reference or throw an exception if a primitive type is encountered.</span></span>|  
|<span data-ttu-id="804e7-140">**_empty**</span><span class="sxs-lookup"><span data-stu-id="804e7-140">**_empty**</span></span>|<span data-ttu-id="804e7-141">Pour les chaînes, retourner **String.Empty**, sinon retourne un objet créé à partir d’un constructeur vide.</span><span class="sxs-lookup"><span data-stu-id="804e7-141">For strings, return **String.Empty**, otherwise return an object created from an empty constructor.</span></span> <span data-ttu-id="804e7-142">Si un type primitif est rencontré, lever une exception.</span><span class="sxs-lookup"><span data-stu-id="804e7-142">If a primitive type is encountered, throw an exception.</span></span>|  
  
 <span data-ttu-id="804e7-143">Le tableau suivant présente les valeurs par défaut pour les objets dans un typé **DataSet** et les annotations disponibles.</span><span class="sxs-lookup"><span data-stu-id="804e7-143">The following table shows default values for objects in a typed **DataSet** and the available annotations.</span></span>  
  
|<span data-ttu-id="804e7-144">Objet/méthode/événement</span><span class="sxs-lookup"><span data-stu-id="804e7-144">Object/Method/Event</span></span>|<span data-ttu-id="804e7-145">Par défaut</span><span class="sxs-lookup"><span data-stu-id="804e7-145">Default</span></span>|<span data-ttu-id="804e7-146">Annotation</span><span class="sxs-lookup"><span data-stu-id="804e7-146">Annotation</span></span>|  
|---------------------------|-------------|----------------|  
|<span data-ttu-id="804e7-147">**DataTable**</span><span class="sxs-lookup"><span data-stu-id="804e7-147">**DataTable**</span></span>|<span data-ttu-id="804e7-148">TableNameDataTable</span><span class="sxs-lookup"><span data-stu-id="804e7-148">TableNameDataTable</span></span>|<span data-ttu-id="804e7-149">typedPlural</span><span class="sxs-lookup"><span data-stu-id="804e7-149">typedPlural</span></span>|  
|<span data-ttu-id="804e7-150">**DataTable** méthodes</span><span class="sxs-lookup"><span data-stu-id="804e7-150">**DataTable** Methods</span></span>|<span data-ttu-id="804e7-151">NewTableNameRow</span><span class="sxs-lookup"><span data-stu-id="804e7-151">NewTableNameRow</span></span><br /><br /> <span data-ttu-id="804e7-152">AddTableNameRow</span><span class="sxs-lookup"><span data-stu-id="804e7-152">AddTableNameRow</span></span><br /><br /> <span data-ttu-id="804e7-153">DeleteTableNameRow</span><span class="sxs-lookup"><span data-stu-id="804e7-153">DeleteTableNameRow</span></span>|<span data-ttu-id="804e7-154">typedName</span><span class="sxs-lookup"><span data-stu-id="804e7-154">typedName</span></span>|  
|<span data-ttu-id="804e7-155">**DataRowCollection**</span><span class="sxs-lookup"><span data-stu-id="804e7-155">**DataRowCollection**</span></span>|<span data-ttu-id="804e7-156">TableName</span><span class="sxs-lookup"><span data-stu-id="804e7-156">TableName</span></span>|<span data-ttu-id="804e7-157">typedPlural</span><span class="sxs-lookup"><span data-stu-id="804e7-157">typedPlural</span></span>|  
|<span data-ttu-id="804e7-158">**DataRow**</span><span class="sxs-lookup"><span data-stu-id="804e7-158">**DataRow**</span></span>|<span data-ttu-id="804e7-159">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="804e7-159">TableNameRow</span></span>|<span data-ttu-id="804e7-160">typedName</span><span class="sxs-lookup"><span data-stu-id="804e7-160">typedName</span></span>|  
|<span data-ttu-id="804e7-161">**DataColumn**</span><span class="sxs-lookup"><span data-stu-id="804e7-161">**DataColumn**</span></span>|<span data-ttu-id="804e7-162">DataTable.ColumnNameColumn</span><span class="sxs-lookup"><span data-stu-id="804e7-162">DataTable.ColumnNameColumn</span></span><br /><br /> <span data-ttu-id="804e7-163">DataRow.ColumnName</span><span class="sxs-lookup"><span data-stu-id="804e7-163">DataRow.ColumnName</span></span>|<span data-ttu-id="804e7-164">typedName</span><span class="sxs-lookup"><span data-stu-id="804e7-164">typedName</span></span>|  
|<span data-ttu-id="804e7-165">**Property**</span><span class="sxs-lookup"><span data-stu-id="804e7-165">**Property**</span></span>|<span data-ttu-id="804e7-166">PropertyName</span><span class="sxs-lookup"><span data-stu-id="804e7-166">PropertyName</span></span>|<span data-ttu-id="804e7-167">typedName</span><span class="sxs-lookup"><span data-stu-id="804e7-167">typedName</span></span>|  
|<span data-ttu-id="804e7-168">**Enfant** accesseur</span><span class="sxs-lookup"><span data-stu-id="804e7-168">**Child** Accessor</span></span>|<span data-ttu-id="804e7-169">GetChildTableNameRows</span><span class="sxs-lookup"><span data-stu-id="804e7-169">GetChildTableNameRows</span></span>|<span data-ttu-id="804e7-170">typedChildren</span><span class="sxs-lookup"><span data-stu-id="804e7-170">typedChildren</span></span>|  
|<span data-ttu-id="804e7-171">**Parent** Accessor</span><span class="sxs-lookup"><span data-stu-id="804e7-171">**Parent** Accessor</span></span>|<span data-ttu-id="804e7-172">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="804e7-172">TableNameRow</span></span>|<span data-ttu-id="804e7-173">typedParent</span><span class="sxs-lookup"><span data-stu-id="804e7-173">typedParent</span></span>|  
|<span data-ttu-id="804e7-174">**Jeu de données** événements</span><span class="sxs-lookup"><span data-stu-id="804e7-174">**DataSet** Events</span></span>|<span data-ttu-id="804e7-175">TableNameRowChangeEvent</span><span class="sxs-lookup"><span data-stu-id="804e7-175">TableNameRowChangeEvent</span></span><br /><br /> <span data-ttu-id="804e7-176">TableNameRowChangeEventHandler</span><span class="sxs-lookup"><span data-stu-id="804e7-176">TableNameRowChangeEventHandler</span></span>|<span data-ttu-id="804e7-177">typedName</span><span class="sxs-lookup"><span data-stu-id="804e7-177">typedName</span></span>|  
  
 <span data-ttu-id="804e7-178">Pour utiliser typées **DataSet** annotations, vous devez inclure les éléments suivants **xmlns** référence dans votre schéma XML Schema definition language (XSD).</span><span class="sxs-lookup"><span data-stu-id="804e7-178">To use typed **DataSet** annotations, you must include the following **xmlns** reference in your XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="804e7-179">(Pour créer un schéma xsd à partir des tables de base de données, consultez <xref:System.Data.DataSet.WriteXmlSchema%2A> ou [utilisation de Datasets dans Visual Studio](http://msdn.microsoft.com/library/8bw9ksd6.aspx)).</span><span class="sxs-lookup"><span data-stu-id="804e7-179">(To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](http://msdn.microsoft.com/library/8bw9ksd6.aspx)).</span></span>  
  
```  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 <span data-ttu-id="804e7-180">Voici un exemple de schéma annoté qui expose la **clients** table de la **Northwind** base de données avec une relation à la **commandes** table incluse.</span><span class="sxs-lookup"><span data-stu-id="804e7-180">The following is a sample annotated schema that exposes the **Customers** table of the **Northwind** database with a relation to the **Orders** table included.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet"   
      xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
      xmlns=""   
      xmlns:xs="http://www.w3.org/2001/XMLSchema"   
      xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID" type="xs:string" minOccurs="0" />  
              <xs:element name="CompanyName"  
codegen:typedName="CompanyName" type="xs:string" minOccurs="0" />  
              <xs:element name="Phone" codegen:typedName="Phone" codegen:nullValue="" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
        <xs:element name="Orders" codegen:typedName="Order" codegen:typedPlural="Orders">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="OrderID" codegen:typedName="OrderID"  
type="xs:int" minOccurs="0" />  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID"                  codegen:nullValue="" type="xs:string" minOccurs="0" />  
              <xs:element name="EmployeeID"  
codegen:typedName="EmployeeID" codegen:nullValue="0"   
type="xs:int" minOccurs="0" />  
              <xs:element name="OrderAdapter"  
codegen:typedName="OrderAdapter" codegen:nullValue="1980-01-01T00:00:00"   
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
  
 <span data-ttu-id="804e7-181">L’exemple de code suivant utilise fortement typé **DataSet** créé à partir de l’exemple de schéma.</span><span class="sxs-lookup"><span data-stu-id="804e7-181">The following code example uses a strongly typed **DataSet** created from the sample schema.</span></span> <span data-ttu-id="804e7-182">Il utilise un <xref:System.Data.SqlClient.SqlDataAdapter> pour remplir le **clients** table et une autre <xref:System.Data.SqlClient.SqlDataAdapter> pour remplir le **commandes** table.</span><span class="sxs-lookup"><span data-stu-id="804e7-182">It uses one <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Customers** table and another <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Orders** table.</span></span> <span data-ttu-id="804e7-183">Fortement typé **DataSet** définit le **DataRelations**.</span><span class="sxs-lookup"><span data-stu-id="804e7-183">The strongly typed **DataSet** defines the **DataRelations**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="804e7-184">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="804e7-184">See Also</span></span>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataSet>  
 [<span data-ttu-id="804e7-185">Datasets typés</span><span class="sxs-lookup"><span data-stu-id="804e7-185">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [<span data-ttu-id="804e7-186">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="804e7-186">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="804e7-187">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="804e7-187">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
