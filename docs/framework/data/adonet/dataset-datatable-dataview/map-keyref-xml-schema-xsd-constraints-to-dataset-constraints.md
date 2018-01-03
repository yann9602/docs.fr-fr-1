---
title: "Mapper les contraintes keyref de schéma XML (XSD) aux contraintes de DataSet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f888a682510dbf768e5eab2ffdd530e2ac7cf635
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="9ab0c-102">Mapper les contraintes keyref de schéma XML (XSD) aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="9ab0c-102">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="9ab0c-103">Le **keyref** élément vous permet d’établir des liens entre des éléments dans un document.</span><span class="sxs-lookup"><span data-stu-id="9ab0c-103">The **keyref** element allows you to establish links between elements within a document.</span></span> <span data-ttu-id="9ab0c-104">Le résultat est similaire à une relation de clé étrangère dans une base de données relationnelle.</span><span class="sxs-lookup"><span data-stu-id="9ab0c-104">This is similar to a foreign key relationship in a relational database.</span></span> <span data-ttu-id="9ab0c-105">Si un schéma spécifie le **keyref** élément, l’élément est converti pendant le processus de mappage de schéma pour une contrainte de clé étrangère correspondante sur les colonnes dans les tables de la <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="9ab0c-105">If a schema specifies the **keyref** element, the element is converted during the schema mapping process to a corresponding foreign key constraint on the columns in the tables of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="9ab0c-106">Par défaut, le **keyref** élément génère aussi une relation, avec les **ParentTable**, **ChildTable**, **ParentColumn**et  **ChildColumn** propriétés spécifiées sur la relation.</span><span class="sxs-lookup"><span data-stu-id="9ab0c-106">By default, the **keyref** element also generates a relation, with the **ParentTable**, **ChildTable**, **ParentColumn**, and **ChildColumn** properties specified on the relation.</span></span>  
  
 <span data-ttu-id="9ab0c-107">Le tableau suivant décrit les **msdata** attributs que vous pouvez spécifier dans le **keyref** élément.</span><span class="sxs-lookup"><span data-stu-id="9ab0c-107">The following table outlines the **msdata** attributes you can specify in the **keyref** element.</span></span>  
  
|<span data-ttu-id="9ab0c-108">Nom d'attribut</span><span class="sxs-lookup"><span data-stu-id="9ab0c-108">Attribute name</span></span>|<span data-ttu-id="9ab0c-109">Description</span><span class="sxs-lookup"><span data-stu-id="9ab0c-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="9ab0c-110">**msdata : ConstraintOnly**</span><span class="sxs-lookup"><span data-stu-id="9ab0c-110">**msdata:ConstraintOnly**</span></span>|<span data-ttu-id="9ab0c-111">Si **ConstraintOnly = « true »** est spécifié sur le **keyref** élément dans le schéma, une contrainte est créée, mais aucune relation est créée.</span><span class="sxs-lookup"><span data-stu-id="9ab0c-111">If **ConstraintOnly="true"** is specified on the **keyref** element in the schema, a constraint is created, but no relation is created.</span></span> <span data-ttu-id="9ab0c-112">Si cet attribut n’est pas spécifié (ou a la valeur **False**), la contrainte et la relation sont créés dans le **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="9ab0c-112">If this attribute is not specified (or is set to **False**), both the constraint and the relation are created in the **DataSet**.</span></span>|  
|<span data-ttu-id="9ab0c-113">**msdata : ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="9ab0c-113">**msdata:ConstraintName**</span></span>|<span data-ttu-id="9ab0c-114">Si le **ConstraintName** attribut est spécifié, sa valeur est utilisée comme nom de la contrainte.</span><span class="sxs-lookup"><span data-stu-id="9ab0c-114">If the **ConstraintName** attribute is specified, its value is used as the name of the constraint.</span></span> <span data-ttu-id="9ab0c-115">Dans le cas contraire, le **nom** attribut de la **keyref** élément dans le schéma fournit le nom de la contrainte dans le **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="9ab0c-115">Otherwise, the **name** attribute of the **keyref** element in the schema provides the constraint name in the **DataSet**.</span></span>|  
|<span data-ttu-id="9ab0c-116">**msdata:UpdateRule**</span><span class="sxs-lookup"><span data-stu-id="9ab0c-116">**msdata:UpdateRule**</span></span>|<span data-ttu-id="9ab0c-117">Si le **UpdateRule** attribut est spécifié dans le **keyref** élément dans le schéma, sa valeur est assignée à la **UpdateRule** propriété contrainte dans le  **Jeu de données**.</span><span class="sxs-lookup"><span data-stu-id="9ab0c-117">If the **UpdateRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **UpdateRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="9ab0c-118">Dans le cas contraire le **UpdateRule** est définie sur **Cascade**.</span><span class="sxs-lookup"><span data-stu-id="9ab0c-118">Otherwise the **UpdateRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="9ab0c-119">**msdata:DeleteRule**</span><span class="sxs-lookup"><span data-stu-id="9ab0c-119">**msdata:DeleteRule**</span></span>|<span data-ttu-id="9ab0c-120">Si le **DeleteRule** attribut est spécifié dans le **keyref** élément dans le schéma, sa valeur est assignée à la **DeleteRule** propriété contrainte dans le  **Jeu de données**.</span><span class="sxs-lookup"><span data-stu-id="9ab0c-120">If the **DeleteRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **DeleteRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="9ab0c-121">Dans le cas contraire le **DeleteRule** est définie sur **Cascade**.</span><span class="sxs-lookup"><span data-stu-id="9ab0c-121">Otherwise the **DeleteRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="9ab0c-122">**msdata:AcceptRejectRule**</span><span class="sxs-lookup"><span data-stu-id="9ab0c-122">**msdata:AcceptRejectRule**</span></span>|<span data-ttu-id="9ab0c-123">Si le **AcceptRejectRule** attribut est spécifié dans le **keyref** élément dans le schéma, sa valeur est assignée à la **AcceptRejectRule** propriété contrainte dans le  **Jeu de données**.</span><span class="sxs-lookup"><span data-stu-id="9ab0c-123">If the **AcceptRejectRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **AcceptRejectRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="9ab0c-124">Dans le cas contraire le **AcceptRejectRule** est définie sur **aucun**.</span><span class="sxs-lookup"><span data-stu-id="9ab0c-124">Otherwise the **AcceptRejectRule** property is set to **None**.</span></span>|  
  
 <span data-ttu-id="9ab0c-125">L’exemple suivant contient un schéma qui spécifie le **clé** et **keyref** des relations entre les **OrderNumber** élément enfant de le **ordre**  élément et la **OrderNo** élément enfant de le **OrderDetail** élément.</span><span class="sxs-lookup"><span data-stu-id="9ab0c-125">The following example contains a schema that specifies the **key** and **keyref** relationships between the **OrderNumber** child element of the **Order** element and the **OrderNo** child element of the **OrderDetail** element.</span></span>  
  
 <span data-ttu-id="9ab0c-126">Dans l’exemple, le **OrderNumber** élément enfant de le **OrderDetail** élément fait référence à la **OrderNo** élément enfant clé de la **commande**élément.</span><span class="sxs-lookup"><span data-stu-id="9ab0c-126">In the example, the **OrderNumber** child element of the **OrderDetail** element refers to the **OrderNo** key child element of the **Order** element.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element name="OrderDetail">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNo" type="xs:integer" />  
           <xs:element name="ItemNo" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
      <xs:element name="Order">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:key name="OrderNumberKey"  >  
    <xs:selector xpath=".//Order" />  
    <xs:field xpath="OrderNumber" />  
  </xs:key>  
  
  <xs:keyref name="OrderNoRef" refer="OrderNumberKey">  
    <xs:selector xpath=".//OrderDetail" />  
    <xs:field xpath="OrderNo" />  
  </xs:keyref>  
 </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="9ab0c-127">Le processus de mappage de schéma XML Schema definition langage (XSD XML) génère les éléments suivants **DataSet** avec deux tables :</span><span class="sxs-lookup"><span data-stu-id="9ab0c-127">The XML Schema definition language (XSD) schema mapping process produces the following **DataSet** with two tables:</span></span>  
  
```  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 <span data-ttu-id="9ab0c-128">En outre, le **DataSet** définit les contraintes suivantes :</span><span class="sxs-lookup"><span data-stu-id="9ab0c-128">In addition, the **DataSet** defines the following constraints:</span></span>  
  
-   <span data-ttu-id="9ab0c-129">Une contrainte unique sur la **commande** table.</span><span class="sxs-lookup"><span data-stu-id="9ab0c-129">A unique constraint on the **Order** table.</span></span>  
  
    ```  
              Table: Order  
    Columns: OrderNumber   
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
-   <span data-ttu-id="9ab0c-130">Une relation entre la **commande** et **OrderDetail** tables.</span><span class="sxs-lookup"><span data-stu-id="9ab0c-130">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="9ab0c-131">Le **Nested** est définie sur **False** , car les deux éléments ne sont pas imbriqués dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="9ab0c-131">The **Nested** property is set to **False** because the two elements are not nested in the schema.</span></span>  
  
    ```  
              ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    ParentKeyConstraint: OrderNumberKey  
    ChildKeyConstraint: OrderNoRef  
    RelationName: OrderNoRef  
    Nested: False  
    ```  
  
-   <span data-ttu-id="9ab0c-132">Une contrainte de clé étrangère sur la **OrderDetail** table.</span><span class="sxs-lookup"><span data-stu-id="9ab0c-132">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo   
    RelatedTable: Order  
    RelatedColumns: OrderNumber   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9ab0c-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ab0c-133">See Also</span></span>  
 [<span data-ttu-id="9ab0c-134">Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="9ab0c-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="9ab0c-135">Génération de relations de DataSet à partir du schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="9ab0c-135">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="9ab0c-136">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="9ab0c-136">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
