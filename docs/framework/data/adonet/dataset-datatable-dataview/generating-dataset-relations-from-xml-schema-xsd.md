---
title: "Génération de relations de DataSet à partir du schéma XML (XSD)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 916b9ad24c2ae2334635760a520116b4c19df314
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a><span data-ttu-id="c4020-102">Génération de relations de DataSet à partir du schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="c4020-102">Generating DataSet Relations from XML Schema (XSD)</span></span>
<span data-ttu-id="c4020-103">Dans un objet <xref:System.Data.DataSet>, vous créez une association entre deux ou plusieurs colonnes en établissant une relation parent-enfant.</span><span class="sxs-lookup"><span data-stu-id="c4020-103">In a <xref:System.Data.DataSet>, you form an association between two or more columns by creating a parent-child relation.</span></span> <span data-ttu-id="c4020-104">Il existe trois façons pour représenter un **DataSet** relation au sein d’un schéma XML Schema definition language (XSD) :</span><span class="sxs-lookup"><span data-stu-id="c4020-104">There are three ways to represent a **DataSet** relation within an XML Schema definition language (XSD) schema:</span></span>  
  
-   <span data-ttu-id="c4020-105">spécifier des types complexes imbriqués ;</span><span class="sxs-lookup"><span data-stu-id="c4020-105">Specify nested complex types.</span></span>  
  
-   <span data-ttu-id="c4020-106">Utilisez le **msdata : Relationship** annotation.</span><span class="sxs-lookup"><span data-stu-id="c4020-106">Use the **msdata:Relationship** annotation.</span></span>  
  
-   <span data-ttu-id="c4020-107">Spécifiez un **xs : keyref** sans le **msdata : ConstraintOnly** annotation.</span><span class="sxs-lookup"><span data-stu-id="c4020-107">Specify an **xs:keyref** without the **msdata:ConstraintOnly** annotation.</span></span>  
  
## <a name="nested-complex-types"></a><span data-ttu-id="c4020-108">Types complexes imbriqués</span><span class="sxs-lookup"><span data-stu-id="c4020-108">Nested Complex Types</span></span>  
 <span data-ttu-id="c4020-109">Les définitions de types complexes imbriqués dans un schéma indiquent les relations parent-enfant des éléments.</span><span class="sxs-lookup"><span data-stu-id="c4020-109">Nested complex type definitions in a schema indicate the parent-child relationships of the elements.</span></span> <span data-ttu-id="c4020-110">Le fragment de schéma XML suivant montre que **OrderDetail** est un élément enfant de le **commande** élément.</span><span class="sxs-lookup"><span data-stu-id="c4020-110">The following XML Schema fragment shows that **OrderDetail** is a child element of the **Order** element.</span></span>  
  
```xml  
<xs:element name="Order">  
  <xs:complexType>  
     <xs:sequence>          
       <xs:element name="OrderDetail" />  
           <xs:complexType>               
           </xs:complexType>  
     </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="c4020-111">Le processus de mappage du schéma XML crée les tables dans le **DataSet** qui correspondent aux types complexes imbriqués dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="c4020-111">The XML Schema mapping process creates tables in the **DataSet** that correspond to the nested complex types in the schema.</span></span> <span data-ttu-id="c4020-112">Il crée également des colonnes supplémentaires qui sont utilisés en tant que parent**-**colonnes enfants pour les tables générées.</span><span class="sxs-lookup"><span data-stu-id="c4020-112">It also creates additional columns that are used as parent**-**child columns for the generated tables.</span></span> <span data-ttu-id="c4020-113">Notez que ces parent**-**colonnes enfant spécifient des relations, qui n’est pas identique à la spécification de contraintes de clé étrangère/clé primaire.</span><span class="sxs-lookup"><span data-stu-id="c4020-113">Note that these parent**-**child columns specify relationships, which is not the same as specifying primary key/foreign key constraints.</span></span>  
  
## <a name="msdatarelationship-annotation"></a><span data-ttu-id="c4020-114">Annotation msdata:Relationship</span><span class="sxs-lookup"><span data-stu-id="c4020-114">msdata:Relationship Annotation</span></span>  
 <span data-ttu-id="c4020-115">Le **msdata : Relationship** annotation vous permet de spécifier explicitement les relations parent-enfant entre des éléments qui ne sont pas imbriqués dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="c4020-115">The **msdata:Relationship** annotation allows you to explicitly specify parent-child relationships between elements in the schema that are not nested.</span></span> <span data-ttu-id="c4020-116">L’exemple suivant montre la structure de la **relation** élément.</span><span class="sxs-lookup"><span data-stu-id="c4020-116">The following example shows the structure of the **Relationship** element.</span></span>  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 <span data-ttu-id="c4020-117">Les attributs de la **msdata : Relationship** annotation identifient les éléments impliqués dans la relation parent-enfant, ainsi que les **parentkey** et **childkey** les éléments et attributs impliqués dans la relation.</span><span class="sxs-lookup"><span data-stu-id="c4020-117">The attributes of the **msdata:Relationship** annotation identify the elements involved in the parent-child relationship, as well as the **parentkey** and **childkey** elements and attributes involved in the relationship.</span></span> <span data-ttu-id="c4020-118">Le processus de mappage utilise ces informations pour générer des tables dans le **DataSet** et pour créer la relation clé primaire/étrangère clée entre ces tables.</span><span class="sxs-lookup"><span data-stu-id="c4020-118">The mapping process uses this information to generate tables in the **DataSet** and to create the primary key/foreign key relationship between these tables.</span></span>  
  
 <span data-ttu-id="c4020-119">Par exemple, le fragment de schéma suivant spécifie **commande** et **OrderDetail** éléments au même niveau (ne pas imbriqués).</span><span class="sxs-lookup"><span data-stu-id="c4020-119">For example, the following schema fragment specifies **Order** and **OrderDetail** elements at the same level (not nested).</span></span> <span data-ttu-id="c4020-120">Le schéma spécifie un **msdata : Relationship** annotation, qui spécifie la relation parent-enfant entre ces deux éléments.</span><span class="sxs-lookup"><span data-stu-id="c4020-120">The schema specifies an **msdata:Relationship** annotation, which specifies the parent-child relationship between these two elements.</span></span> <span data-ttu-id="c4020-121">Dans ce cas, une relation explicite doit être spécifiée à l’aide de la **msdata : Relationship** annotation.</span><span class="sxs-lookup"><span data-stu-id="c4020-121">In this case, an explicit relationship must be specified using the **msdata:Relationship** annotation.</span></span>  
  
```xml  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
        <xs:element name="OrderDetail">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
       <xs:element name="Order">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
    </xs:choice>  
  </xs:complexType>  
</xs:element>  
   <xs:annotation>  
     <xs:appinfo>  
       <msdata:Relationship name="OrdOrdDetailRelation"  
          msdata:parent="Order"  
          msdata:child="OrderDetail"   
          msdata:parentkey="OrderNumber"  
          msdata:childkey="OrderNo"/>  
     </xs:appinfo>  
  </xs:annotation>  
```  
  
 <span data-ttu-id="c4020-122">Le processus de mappage utilise le **relation** élément pour créer une relation parent-enfant entre les **OrderNumber** colonne dans la **commande** table et la **OrderNo** colonne dans la **OrderDetail** de table dans le **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="c4020-122">The mapping process uses the **Relationship** element to create a parent-child relationship between the **OrderNumber** column in the **Order** table and the **OrderNo** column in the **OrderDetail** table in the **DataSet**.</span></span> <span data-ttu-id="c4020-123">Il ne spécifie que la relation ; il ne spécifie pas automatiquement de contraintes sur les valeurs de ces colonnes comme le font des contraintes de clé primaire/clé étrangère dans des bases de données relationnelles.</span><span class="sxs-lookup"><span data-stu-id="c4020-123">The mapping process only specifies the relationship; it does not automatically specify any constraints on the values in these columns, as do the primary key/foreign key constraints in relational databases.</span></span>  
  
### <a name="in-this-section"></a><span data-ttu-id="c4020-124">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c4020-124">In This Section</span></span>  
 [<span data-ttu-id="c4020-125">Mapper les relations implicites entre éléments de schéma imbriqués</span><span class="sxs-lookup"><span data-stu-id="c4020-125">Map Implicit Relations Between Nested Schema Elements</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md)  
 <span data-ttu-id="c4020-126">Décrit les contraintes et relations implicitement créées dans un **DataSet** lorsque les éléments imbriqués sont rencontrées dans le schéma XML.</span><span class="sxs-lookup"><span data-stu-id="c4020-126">Describes the constraints and relations that are implicitly created in a **DataSet** when nested elements are encountered in XML Schema.</span></span>  
  
 [<span data-ttu-id="c4020-127">Mapper les relations spécifiées pour les éléments imbriqués</span><span class="sxs-lookup"><span data-stu-id="c4020-127">Map Relations Specified for Nested Elements</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-relations-specified-for-nested-elements.md)  
 <span data-ttu-id="c4020-128">Explique comment définir explicitement des relations un **DataSet** pour les éléments imbriqués dans le schéma XML.</span><span class="sxs-lookup"><span data-stu-id="c4020-128">Describes how to explicitly set relations in a **DataSet** for nested elements in XML Schema.</span></span>  
  
 [<span data-ttu-id="c4020-129">Spécifier les relations entre éléments sans imbrication</span><span class="sxs-lookup"><span data-stu-id="c4020-129">Specify Relations Between Elements with No Nesting</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/specify-relations-between-elements-with-no-nesting.md)  
 <span data-ttu-id="c4020-130">Décrit comment créer des relations dans un **DataSet** entre les éléments de schéma XML qui ne sont pas imbriqués.</span><span class="sxs-lookup"><span data-stu-id="c4020-130">Describes how to create relations in a **DataSet** between XML Schema elements that are not nested.</span></span>  
  
### <a name="related-sections"></a><span data-ttu-id="c4020-131">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="c4020-131">Related Sections</span></span>  
 [<span data-ttu-id="c4020-132">Dérivation de la structure relationnelle des DataSets à partir du schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="c4020-132">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="c4020-133">Décrit la structure relationnelle, ou schéma, d’un **DataSet** qui est créé à partir du schéma de langage (XSD XML) de définition de schéma XML.</span><span class="sxs-lookup"><span data-stu-id="c4020-133">Describes the relational structure, or schema, of a **DataSet** that is created from XML Schema definition language (XSD) schema.</span></span>  
  
 [<span data-ttu-id="c4020-134">Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="c4020-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="c4020-135">Décrit les éléments de schéma XML utilisés pour créer des contraintes de clé étrangères et uniques dans un **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="c4020-135">Describes the XML Schema elements used to create unique and foreign key constraints in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4020-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4020-136">See Also</span></span>  
 [<span data-ttu-id="c4020-137">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="c4020-137">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
