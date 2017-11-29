---
title: "Spécifier les relations entre éléments sans imbrication"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e31325da-7691-4d33-acf4-99fccca67006
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 036085160e9e4817964754a85db627e4d4ba8654
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="specify-relations-between-elements-with-no-nesting"></a><span data-ttu-id="ca09d-102">Spécifier les relations entre éléments sans imbrication</span><span class="sxs-lookup"><span data-stu-id="ca09d-102">Specify Relations Between Elements with No Nesting</span></span>
<span data-ttu-id="ca09d-103">Lorsque des éléments ne sont pas imbriqués, aucune relation implicite n'est créée.</span><span class="sxs-lookup"><span data-stu-id="ca09d-103">When elements are not nested, no implicit relations are created.</span></span> <span data-ttu-id="ca09d-104">Toutefois, vous pouvez spécifier explicitement des relations entre des éléments qui ne sont pas imbriqués à l’aide de la **msdata : Relationship** annotation.</span><span class="sxs-lookup"><span data-stu-id="ca09d-104">You can, however, explicitly specify relations between elements that are not nested by using the **msdata:Relationship** annotation.</span></span>  
  
 <span data-ttu-id="ca09d-105">L’exemple suivant montre un schéma XML dans lequel le **msdata : Relationship** annotation est spécifiée entre la **commande** et **OrderDetail** éléments qui ne sont pas imbriquées.</span><span class="sxs-lookup"><span data-stu-id="ca09d-105">The following example shows an XML Schema in which the **msdata:Relationship** annotation is specified between the **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="ca09d-106">Le **msdata : Relationship** annotation est spécifiée en tant qu’élément enfant de le **schéma** élément.</span><span class="sxs-lookup"><span data-stu-id="ca09d-106">The **msdata:Relationship** annotation is specified as the child element of the **Schema** element.</span></span>  
  
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
           <xs:element name="OrderNo" type="xs:string" />  
           <xs:element name="ItemNo" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
      <xs:element name="Order">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNumber" type="xs:string" />  
           <xs:element name="EmpNumber" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  </xs:element>  
   <xs:annotation>  
     <xs:appinfo>  
       <msdata:Relationship name="OrdOrderDetailRelation"  
                            msdata:parent="Order"   
                            msdata:child="OrderDetail"   
                            msdata:parentkey="OrderNumber"   
                            msdata:childkey="OrderNo"/>  
     </xs:appinfo>  
  </xs:annotation>  
</xs:schema>  
```  
  
 <span data-ttu-id="ca09d-107">Le processus de mappage de schéma XML Schema definition langage (XSD XML) crée un <xref:System.Data.DataSet> avec **commande** et **OrderDetail** tables et une relation est spécifiée entre ces deux tables, comme indiqué ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="ca09d-107">The XML Schema definition language (XSD) schema mapping process creates a <xref:System.Data.DataSet> with **Order** and **OrderDetail** tables and a relationship specified between these two tables, as shown below.</span></span>  
  
```  
RelationName: OrdOrderDetailRelation  
ParentTable: Order  
ParentColumns: OrderNumber   
ChildTable: OrderDetail  
ChildColumns: OrderNo   
Nested: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="ca09d-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca09d-108">See Also</span></span>  
 [<span data-ttu-id="ca09d-109">Génération des Relations d’un DataSet à partir de schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="ca09d-109">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="ca09d-110">Mappage de schéma (XSD) des contraintes aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="ca09d-110">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="ca09d-111">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="ca09d-111">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
