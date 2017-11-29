---
title: "Mapper les contraintes clés de schéma XML (XSD) aux contraintes de DataSet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f5247d0ccfd2ceec641ff29d29b889a55c1a5e12
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="11fd0-102">Mapper les contraintes clés de schéma XML (XSD) aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="11fd0-102">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="11fd0-103">Dans un schéma, vous pouvez spécifier une contrainte de clé sur un élément ou d’attribut à l’aide de la **clé** élément.</span><span class="sxs-lookup"><span data-stu-id="11fd0-103">In a schema, you can specify a key constraint on an element or attribute using the **key** element.</span></span> <span data-ttu-id="11fd0-104">L'élément ou attribut sur lequel une contrainte de clé est spécifiée doit avoir des valeurs uniques dans toute instance du schéma et ne peut pas avoir de valeurs null.</span><span class="sxs-lookup"><span data-stu-id="11fd0-104">The element or attribute on which a key constraint is specified must have unique values in any schema instance, and cannot have null values.</span></span>  
  
 <span data-ttu-id="11fd0-105">La contrainte de clé est similaire à la contrainte unique, si ce n'est que la colonne sur laquelle une contrainte de clé est définie ne peut pas comporter de valeurs null.</span><span class="sxs-lookup"><span data-stu-id="11fd0-105">The key constraint is similar to the unique constraint, except that the column on which a key constraint is defined cannot have null values.</span></span>  
  
 <span data-ttu-id="11fd0-106">Le tableau suivant décrit les **msdata** les attributs que vous pouvez spécifier dans le **clé** élément.</span><span class="sxs-lookup"><span data-stu-id="11fd0-106">The following table outlines the **msdata** attributes that you can specify in the **key** element.</span></span>  
  
|<span data-ttu-id="11fd0-107">Nom d'attribut</span><span class="sxs-lookup"><span data-stu-id="11fd0-107">Attribute name</span></span>|<span data-ttu-id="11fd0-108">Description</span><span class="sxs-lookup"><span data-stu-id="11fd0-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="11fd0-109">**msdata : ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="11fd0-109">**msdata:ConstraintName**</span></span>|<span data-ttu-id="11fd0-110">Si cet attribut est spécifié, sa valeur est utilisée comme nom de la contrainte.</span><span class="sxs-lookup"><span data-stu-id="11fd0-110">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="11fd0-111">Dans le cas contraire, le **nom** attribut fournit la valeur de la contrainte.</span><span class="sxs-lookup"><span data-stu-id="11fd0-111">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="11fd0-112">**msdata : PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="11fd0-112">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="11fd0-113">Si `PrimaryKey="true"` est présent, le **IsPrimaryKey** contrainte est définie sur **true**, ce qui rend une clé primaire.</span><span class="sxs-lookup"><span data-stu-id="11fd0-113">If `PrimaryKey="true"` is present, the **IsPrimaryKey** constraint property is set to **true**, thus making it a primary key.</span></span> <span data-ttu-id="11fd0-114">Le **AllowDBNull** colonne est définie sur **false**, car les clés primaires ne peuvent pas avoir de valeurs null.</span><span class="sxs-lookup"><span data-stu-id="11fd0-114">The **AllowDBNull** column property is set to **false**, because primary keys cannot have null values.</span></span>|  
  
 <span data-ttu-id="11fd0-115">En convertissant un schéma dans lequel une contrainte de clé est spécifiée, le processus de mappage crée une contrainte unique sur la table avec la **AllowDBNull** propriété column définie sur **false** pour chaque colonne dans le contrainte.</span><span class="sxs-lookup"><span data-stu-id="11fd0-115">In converting schema in which a key constraint is specified, the mapping process creates a unique constraint on the table with the **AllowDBNull** column property set to **false** for each column in the constraint.</span></span> <span data-ttu-id="11fd0-116">Le **IsPrimaryKey** de la contrainte unique est également définie sur **false** , sauf si vous avez spécifié `msdata:PrimaryKey="true"` sur la **clé** élément.</span><span class="sxs-lookup"><span data-stu-id="11fd0-116">The **IsPrimaryKey** property of the unique constraint is also set to **false** unless you have specified `msdata:PrimaryKey="true"` on the **key** element.</span></span> <span data-ttu-id="11fd0-117">Ce mode de fonctionnement est identique à celui d'une contrainte unique dans le schéma faisant apparaître `PrimaryKey="true"`.</span><span class="sxs-lookup"><span data-stu-id="11fd0-117">This is identical to a unique constraint in the schema in which `PrimaryKey="true"`.</span></span>  
  
 <span data-ttu-id="11fd0-118">Dans l’exemple qui suit, la **clé** élément spécifie la contrainte de clé sur le **CustomerID** élément.</span><span class="sxs-lookup"><span data-stu-id="11fd0-118">In the following schema example, the **key** element specifies the key constraint on the **CustomerID** element.</span></span>  
  
```xml  
<xs:schema id="cod"  
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
        <xs:element name="CompanyName" type="xs:string" minOccurs="0" />  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
<xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:key  msdata:PrimaryKey="true"  
       msdata:ConstraintName="KeyCustID"  
          name="KeyConstCustomerID" >  
     <xs:selector xpath=".//Customers" />  
     <xs:field xpath="CustomerID" />  
    </xs:key>  
 </xs:element>  
</xs:schema>   
```  
  
 <span data-ttu-id="11fd0-119">Le **clé** élément spécifie que les valeurs de la **CustomerID** élément enfant de le **clients** élément doivent avoir des valeurs uniques et ne peut pas avoir de valeurs null.</span><span class="sxs-lookup"><span data-stu-id="11fd0-119">The **key** element specifies that the values of the **CustomerID** child element of the **Customers** element must have unique values and cannot have null values.</span></span> <span data-ttu-id="11fd0-120">En convertissant le schéma en langage XSD (XML Schema Definition), le processus de mappage crée la table suivante :</span><span class="sxs-lookup"><span data-stu-id="11fd0-120">In translating the XML Schema definition language (XSD) schema, the mapping process creates the following table:</span></span>  
  
```  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="11fd0-121">Le mappage de schéma XML crée également un **UniqueConstraint** sur la **CustomerID** colonne, comme le montre l’exemple suivant <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="11fd0-121">The XML Schema mapping also creates a **UniqueConstraint** on the **CustomerID** column, as shown in the following <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="11fd0-122">(Par souci de simplicité, seules les propriétés pertinentes sont représentées.)</span><span class="sxs-lookup"><span data-stu-id="11fd0-122">(For simplicity, only relevant properties are shown.)</span></span>  
  
```  
      DataSetName: MyDataSet  
TableName: customers  
  ColumnName: CustomerID  
      AllowDBNull: False  
      Unique: True  
  ConstraintName: KeyCustID  
      Table: customers  
      Columns: CustomerID   
      IsPrimaryKey: True  
```  
  
 <span data-ttu-id="11fd0-123">Dans le **DataSet** qui est généré, le **IsPrimaryKey** propriété de la **UniqueConstraint** a la valeur **true** , car le schéma Spécifie `msdata:PrimaryKey="true"` dans les **clé** élément.</span><span class="sxs-lookup"><span data-stu-id="11fd0-123">In the **DataSet** that is generated, the **IsPrimaryKey** property of the **UniqueConstraint** is set to **true** because the schema specifies `msdata:PrimaryKey="true"` in the **key** element.</span></span>  
  
 <span data-ttu-id="11fd0-124">La valeur de la **ConstraintName** propriété de la **UniqueConstraint** dans les **DataSet** est la valeur de la **msdata : ConstraintName** attribut spécifié dans le **clé** élément dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="11fd0-124">The value of the **ConstraintName** property of the **UniqueConstraint** in the **DataSet** is the value of the **msdata:ConstraintName** attribute specified in the **key** element in the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11fd0-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11fd0-125">See Also</span></span>  
 [<span data-ttu-id="11fd0-126">Mappage de schéma (XSD) des contraintes aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="11fd0-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="11fd0-127">Génération des Relations d’un DataSet à partir de schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="11fd0-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="11fd0-128">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="11fd0-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
