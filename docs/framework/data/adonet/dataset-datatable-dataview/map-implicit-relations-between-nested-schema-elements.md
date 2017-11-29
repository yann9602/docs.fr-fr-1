---
title: "Mapper les relations implicites entre éléments de schéma imbriqués"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b3e3243384bd1dd55661a87ee67cc3052b94e923
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a><span data-ttu-id="b01f9-102">Mapper les relations implicites entre éléments de schéma imbriqués</span><span class="sxs-lookup"><span data-stu-id="b01f9-102">Map Implicit Relations Between Nested Schema Elements</span></span>
<span data-ttu-id="b01f9-103">Un schéma en langage XSD (XML Schema Definition) peut présenter des types complexes imbriqués les uns dans les autres.</span><span class="sxs-lookup"><span data-stu-id="b01f9-103">An XML Schema definition language (XSD) schema can have complex types nested inside one another.</span></span> <span data-ttu-id="b01f9-104">Dans ce cas, le processus de mappage applique le mappage par défaut et crée les différents éléments suivants dans l'objet <xref:System.Data.DataSet> :</span><span class="sxs-lookup"><span data-stu-id="b01f9-104">In this case, the mapping process applies default mapping and creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
-   <span data-ttu-id="b01f9-105">Une table pour chacun des types complexes (parent et enfant).</span><span class="sxs-lookup"><span data-stu-id="b01f9-105">One table for each of the complex types (parent and child).</span></span>  
  
-   <span data-ttu-id="b01f9-106">Si aucune contrainte unique n’existe sur le parent, une colonne de clé primaire supplémentaire par la définition de la table nommée *TableName*_Id où *TableName* est le nom de la table parente.</span><span class="sxs-lookup"><span data-stu-id="b01f9-106">If no unique constraint exists on the parent, one additional primary key column per table definition named *TableName*_Id where *TableName* is the name of the parent table.</span></span>  
  
-   <span data-ttu-id="b01f9-107">Une contrainte de clé primaire sur la table parente, identifiant la colonne supplémentaire en tant que la clé primaire (en définissant le **IsPrimaryKey** propriété **True**).</span><span class="sxs-lookup"><span data-stu-id="b01f9-107">A primary key constraint on the parent table identifying the additional column as the primary key (by setting the **IsPrimaryKey** property to **True**).</span></span> <span data-ttu-id="b01f9-108">La contrainte est nommée contrainte *#*  où  *#*  est 1, 2, 3 et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="b01f9-108">The constraint is named Constraint*#* where *#* is 1, 2, 3, and so on.</span></span> <span data-ttu-id="b01f9-109">Par exemple, le nom par défaut de la première contrainte est Constraint1.</span><span class="sxs-lookup"><span data-stu-id="b01f9-109">For example, the default name for the first constraint is Constraint1.</span></span>  
  
-   <span data-ttu-id="b01f9-110">Une contrainte de clé étrangère sur la table enfant, qui identifie la colonne supplémentaire en tant que clé étrangère faisant référence à la clé primaire de la table parente.</span><span class="sxs-lookup"><span data-stu-id="b01f9-110">A foreign key constraint on the child table identifying the additional column as the foreign key referring to the primary key of the parent table.</span></span> <span data-ttu-id="b01f9-111">La contrainte est nommée *ParentTable_ChildTable* où *ParentTable* est le nom de la table parente et *ChildTable* est le nom de la table enfant.</span><span class="sxs-lookup"><span data-stu-id="b01f9-111">The constraint is named *ParentTable_ChildTable* where *ParentTable* is the name of the parent table and *ChildTable* is the name of the child table.</span></span>  
  
-   <span data-ttu-id="b01f9-112">Une relation de données entre les tables parente et enfant.</span><span class="sxs-lookup"><span data-stu-id="b01f9-112">A data relation between the parent and child tables.</span></span>  
  
 <span data-ttu-id="b01f9-113">L’exemple suivant montre un schéma dans lequel **OrderDetail** est un élément enfant de **commande**.</span><span class="sxs-lookup"><span data-stu-id="b01f9-113">The following example shows a schema where **OrderDetail** is a child element of **Order**.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
   <xs:complexType>  
     <xs:choice maxOccurs="unbounded">  
       <xs:element name="Order">  
         <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:string" />  
            <xs:element name="EmpNumber" type="xs:string" />  
            <xs:element name="OrderDetail">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="OrderNo" type="xs:string" />  
                  <xs:element name="ItemNo" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
          </xs:sequence>  
         </xs:complexType>  
       </xs:element>  
     </xs:choice>  
   </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="b01f9-114">Le processus de mappage du schéma XML crée les éléments suivants dans le **DataSet**:</span><span class="sxs-lookup"><span data-stu-id="b01f9-114">The XML Schema mapping process creates the following in the **DataSet**:</span></span>  
  
-   <span data-ttu-id="b01f9-115">Un **commande** et un **OrderDetail** table.</span><span class="sxs-lookup"><span data-stu-id="b01f9-115">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
-   <span data-ttu-id="b01f9-116">Une contrainte unique sur la **commande** table.</span><span class="sxs-lookup"><span data-stu-id="b01f9-116">A unique constraint on the **Order** table.</span></span> <span data-ttu-id="b01f9-117">Notez que la **IsPrimaryKey** est définie sur **True**.</span><span class="sxs-lookup"><span data-stu-id="b01f9-117">Note that the **IsPrimaryKey** property is set to **True**.</span></span>  
  
    ```  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
-   <span data-ttu-id="b01f9-118">Une contrainte de clé étrangère sur la **OrderDetail** table.</span><span class="sxs-lookup"><span data-stu-id="b01f9-118">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
-   <span data-ttu-id="b01f9-119">Une relation entre la **commande** et **OrderDetail** tables.</span><span class="sxs-lookup"><span data-stu-id="b01f9-119">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="b01f9-120">Le **Nested** pour cette relation est définie sur **True** , car le **commande** et **OrderDetail** éléments sont imbriqués dans le schéma .</span><span class="sxs-lookup"><span data-stu-id="b01f9-120">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```  
    ParentTable: Order  
    ParentColumns: Order_Id   
    ChildTable: OrderDetail  
    ChildColumns: Order_Id   
    ParentKeyConstraint: Constraint1  
    ChildKeyConstraint: Order_OrderDetail  
    RelationName: Order_OrderDetail  
    Nested: True  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b01f9-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b01f9-121">See Also</span></span>  
 [<span data-ttu-id="b01f9-122">Génération des Relations d’un DataSet à partir de schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="b01f9-122">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="b01f9-123">Mappage de schéma (XSD) des contraintes aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="b01f9-123">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="b01f9-124">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="b01f9-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
