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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 740d45c47f46c311ed703fa11ec86a9739930944
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a>Mapper les relations implicites entre éléments de schéma imbriqués
Un schéma en langage XSD (XML Schema Definition) peut présenter des types complexes imbriqués les uns dans les autres. Dans ce cas, le processus de mappage applique le mappage par défaut et crée les différents éléments suivants dans l'objet <xref:System.Data.DataSet> :  
  
-   Une table pour chacun des types complexes (parent et enfant).  
  
-   Si aucune contrainte unique n’existe sur le parent, une colonne de clé primaire supplémentaire par la définition de la table nommée *TableName*_Id où *TableName* est le nom de la table parente.  
  
-   Une contrainte de clé primaire sur la table parente, identifiant la colonne supplémentaire en tant que la clé primaire (en définissant le **IsPrimaryKey** propriété **True**). La contrainte est nommée contrainte *#*  où  *#*  est 1, 2, 3 et ainsi de suite. Par exemple, le nom par défaut de la première contrainte est Constraint1.  
  
-   Une contrainte de clé étrangère sur la table enfant, qui identifie la colonne supplémentaire en tant que clé étrangère faisant référence à la clé primaire de la table parente. La contrainte est nommée *ParentTable_ChildTable* où *ParentTable* est le nom de la table parente et *ChildTable* est le nom de la table enfant.  
  
-   Une relation de données entre les tables parente et enfant.  
  
 L’exemple suivant montre un schéma dans lequel **OrderDetail** est un élément enfant de **commande**.  
  
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
  
 Le processus de mappage du schéma XML crée les éléments suivants dans le **DataSet**:  
  
-   Un **commande** et un **OrderDetail** table.  
  
    ```  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
-   Une contrainte unique sur la **commande** table. Notez que la **IsPrimaryKey** est définie sur **True**.  
  
    ```  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
-   Une contrainte de clé étrangère sur la **OrderDetail** table.  
  
    ```  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
-   Une relation entre la **commande** et **OrderDetail** tables. Le **Nested** pour cette relation est définie sur **True** , car le **commande** et **OrderDetail** éléments sont imbriqués dans le schéma .  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Génération de relations de DataSet à partir du schéma XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
