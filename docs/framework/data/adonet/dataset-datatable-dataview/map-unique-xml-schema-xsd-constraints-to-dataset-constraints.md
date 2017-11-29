---
title: "Mapper les contraintes uniques de schéma XML (XSD) aux contraintes de DataSet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 66183768b5b48608dc69a4021b27816595c43b4b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="b032f-102">Mapper les contraintes uniques de schéma XML (XSD) aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="b032f-102">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="b032f-103">Dans un schéma de langage (XSD XML) de définition de schéma XML, le **unique** élément spécifie la contrainte d’unicité sur un élément ou attribut.</span><span class="sxs-lookup"><span data-stu-id="b032f-103">In an XML Schema definition language (XSD) schema, the **unique** element specifies the uniqueness constraint on an element or attribute.</span></span> <span data-ttu-id="b032f-104">Dans le processus de conversion d'un schéma XML en schéma relationnel, la contrainte unique spécifiée sur un élément ou un attribut du schéma XML est mappée à une contrainte unique dans l'objet <xref:System.Data.DataTable> de l'objet <xref:System.Data.DataSet> correspondant qui est généré.</span><span class="sxs-lookup"><span data-stu-id="b032f-104">In the process of translating an XML Schema into a relational schema, the unique constraint specified on an element or attribute in the XML Schema is mapped to a unique constraint in the <xref:System.Data.DataTable> in the corresponding <xref:System.Data.DataSet> that is generated.</span></span>  
  
 <span data-ttu-id="b032f-105">Le tableau suivant décrit les **msdata** les attributs que vous pouvez spécifier dans le **unique** élément.</span><span class="sxs-lookup"><span data-stu-id="b032f-105">The following table outlines the **msdata** attributes that you can specify in the **unique** element.</span></span>  
  
|<span data-ttu-id="b032f-106">Nom d'attribut</span><span class="sxs-lookup"><span data-stu-id="b032f-106">Attribute name</span></span>|<span data-ttu-id="b032f-107">Description</span><span class="sxs-lookup"><span data-stu-id="b032f-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="b032f-108">**msdata : ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="b032f-108">**msdata:ConstraintName**</span></span>|<span data-ttu-id="b032f-109">Si cet attribut est spécifié, sa valeur est utilisée comme nom de la contrainte.</span><span class="sxs-lookup"><span data-stu-id="b032f-109">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="b032f-110">Dans le cas contraire, le **nom** attribut fournit la valeur de la contrainte.</span><span class="sxs-lookup"><span data-stu-id="b032f-110">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="b032f-111">**msdata : PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="b032f-111">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="b032f-112">Si `PrimaryKey="true"` est présent dans le **unique** élément, une contrainte unique est créée avec le **IsPrimaryKey** propriété **true**.</span><span class="sxs-lookup"><span data-stu-id="b032f-112">If `PrimaryKey="true"` is present in the **unique** element, a unique constraint is created with the **IsPrimaryKey** property set to **true**.</span></span>|  
  
 <span data-ttu-id="b032f-113">L’exemple suivant montre un schéma XML qui utilise le **unique** élément pour spécifier une contrainte d’unicité.</span><span class="sxs-lookup"><span data-stu-id="b032f-113">The following example shows an XML Schema that uses the **unique** element to specify a uniqueness constraint.</span></span>  
  
```xml  
<xs:schema id="SampleDataSet"   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:integer"   
           minOccurs="0"/>  
        <xs:element name="CompanyName" type="xs:string"   
           minOccurs="0"/>  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
  
 <xs:element name="SampleDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:unique     msdata:ConstraintName="UCustID"     name="UniqueCustIDConstr" >       <xs:selector xpath=".//Customers" />       <xs:field xpath="CustomerID" />     </xs:unique>  
</xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="b032f-114">Le **unique** élément dans le schéma spécifie que, pour toutes les **clients** éléments dans un document d’instance, la valeur de la **CustomerID** élément enfant doit être unique.</span><span class="sxs-lookup"><span data-stu-id="b032f-114">The **unique** element in the schema specifies that for all **Customers** elements in a document instance, the value of the **CustomerID** child element must be unique.</span></span> <span data-ttu-id="b032f-115">Dans la construction du **DataSet**, le processus de mappage lit ce schéma et crée la table suivante :</span><span class="sxs-lookup"><span data-stu-id="b032f-115">In building the **DataSet**, the mapping process reads this schema and generates the following table:</span></span>  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="b032f-116">Le processus de mappage crée aussi une contrainte unique sur la **CustomerID** colonne, comme le montre l’exemple suivant **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="b032f-116">The mapping process also creates a unique constraint on the **CustomerID** column, as shown in the following **DataSet**.</span></span> <span data-ttu-id="b032f-117">(Par souci de simplicité, seules les propriétés pertinentes sont représentées.)</span><span class="sxs-lookup"><span data-stu-id="b032f-117">(For simplicity, only relevant properties are shown.)</span></span>  
  
```  
      DataSetName: MyDataSet  
TableName: Customers  
  ColumnName: CustomerID  
      AllowDBNull: True  
      Unique: True  
  ConstraintName: UcustID       Type: UniqueConstraint  
      Table: Customers  
      Columns: CustomerID   
      IsPrimaryKey: False  
```  
  
 <span data-ttu-id="b032f-118">Dans le **DataSet** qui est généré, le **IsPrimaryKey** est définie sur **False** pour la contrainte unique.</span><span class="sxs-lookup"><span data-stu-id="b032f-118">In the **DataSet** that is generated, the **IsPrimaryKey** property is set to **False** for the unique constraint.</span></span> <span data-ttu-id="b032f-119">Le **unique** sur la colonne indique que la **CustomerID** les valeurs de colonne doivent être uniques (mais elles peuvent être une référence null, comme spécifié par le **AllowDBNull** propriété de la colonne).</span><span class="sxs-lookup"><span data-stu-id="b032f-119">The **unique** property on the column indicates that the **CustomerID** column values must be unique (but they can be a null reference, as specified by the **AllowDBNull** property of the column).</span></span>  
  
 <span data-ttu-id="b032f-120">Si vous modifiez le schéma et définir le paramètre facultatif **msdata : PrimaryKey** valeur d’attribut **True**, la contrainte unique est créée sur la table.</span><span class="sxs-lookup"><span data-stu-id="b032f-120">If you modify the schema and set the optional **msdata:PrimaryKey** attribute value to **True**, the unique constraint is created on the table.</span></span> <span data-ttu-id="b032f-121">Le **AllowDBNull** colonne est définie sur **False**et le **IsPrimaryKey** propriétés de la contrainte de valeur **True**, faisant ainsi le **CustomerID** colonne une colonne clé primaire.</span><span class="sxs-lookup"><span data-stu-id="b032f-121">The **AllowDBNull** column property is set to **False**, and the **IsPrimaryKey** property of the constraint set to **True**, thus making the **CustomerID** column a primary key column.</span></span>  
  
 <span data-ttu-id="b032f-122">Vous pouvez spécifier une contrainte unique sur une combinaison d'éléments ou d'attributs dans le schéma XML.</span><span class="sxs-lookup"><span data-stu-id="b032f-122">You can specify a unique constraint on a combination of elements or attributes in the XML Schema.</span></span> <span data-ttu-id="b032f-123">L’exemple suivant montre comment spécifier qu’une combinaison de **CustomerID** et **CompanyName** valeurs doivent être uniques pour tous les **clients** dans n’importe quelle instance, par Ajout d’un autre **xs : Field** élément dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="b032f-123">The following example demonstrates how to specify that a combination of **CustomerID** and **CompanyName** values must be unique for all **Customers** in any instance, by adding another **xs:field** element in the schema.</span></span>  
  
```xml  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 <span data-ttu-id="b032f-124">Ceci est la contrainte qui est créée dans la boîte **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="b032f-124">This is the constraint that is created in the resulting **DataSet**.</span></span>  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="b032f-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b032f-125">See Also</span></span>  
 [<span data-ttu-id="b032f-126">Mappage de schéma (XSD) des contraintes aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="b032f-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="b032f-127">Génération des Relations d’un DataSet à partir de schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="b032f-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="b032f-128">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="b032f-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
