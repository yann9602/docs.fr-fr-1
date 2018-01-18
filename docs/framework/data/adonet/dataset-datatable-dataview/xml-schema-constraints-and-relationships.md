---
title: "Contraintes et relations du schéma XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e450954e4b0e51057e98dd329fe26c38f0ebbb05
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="xml-schema-constraints-and-relationships"></a>Contraintes et relations du schéma XML
Dans un schéma de langage (XSD XML) de définition de schéma XML, vous pouvez spécifier des contraintes (unique, contraintes key et keyref) et des relations (à l’aide de la **msdata : Relationship** annotation). Cette rubrique explique comment les contraintes et relations spécifiées dans un schéma XML sont interprétées pour générer l'objet <xref:System.Data.DataSet>.  
  
 En général, dans un schéma XML, vous spécifiez la **msdata : Relationship** annotation si vous souhaitez générer uniquement des relations dans le **DataSet**. Pour plus d’informations, consultez [génération de Relations d’un DataSet à partir de XSD (XML Schema)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md). Vous spécifiez des contraintes (unique, key et keyref) si vous souhaitez générer des contraintes dans la **DataSet**. Notez que les contraintes key et keyref peuvent aussi servir à générer des relations, comme expliqué plus loin dans cette rubrique.  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a>Génération d'une relation à partir des contraintes key et keyref  
 Au lieu de spécifier le **msdata : Relationship** annotation, vous pouvez spécifier des contraintes key et keyref, qui sont utilisés pendant le processus de mappage de schéma XML pour générer les contraintes, mais aussi la relation dans le  **Jeu de données**. Toutefois, si vous spécifiez `msdata:ConstraintOnly="true"` dans les **keyref** élément, le **DataSet** n’inclura que les contraintes et n’inclut pas la relation.  
  
 L’exemple suivant montre un schéma XML qui inclut **commande** et **OrderDetail** éléments qui ne sont pas imbriqués. Le schéma spécifie également des contraintes key et keyref.  
  
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
  
 Le **DataSet** qui est généré pendant le schéma XML inclut des processus de mappage du **commande** et **OrderDetail** tables. En outre, le **DataSet** inclut des relations et contraintes. L'exemple suivant illustre ces relations et contraintes. Notez que le schéma ne spécifie pas le **msdata : Relationship** annotation ; au lieu de cela, les contraintes key et keyref sont utilisées pour générer la relation.  
  
```  
....ConstraintName: OrderNumberKey  
....Type: UniqueConstraint  
....Table: Order  
....Columns: OrderNumber  
....IsPrimaryKey: False  
  
....ConstraintName: OrderNoRef  
....Type: ForeignKeyConstraint  
....Table: OrderDetail  
....Columns: OrderNo  
....RelatedTable: Order  
....RelatedColumns: OrderNumber  
  
..RelationName: OrderNoRef  
..ParentTable: Order  
..ParentColumns: OrderNumber  
..ChildTable: OrderDetail  
..ChildColumns: OrderNo  
..ParentKeyConstraint: OrderNumberKey  
..ChildKeyConstraint: OrderNoRef  
..Nested: False  
```  
  
 Dans l’exemple de schéma précédent, le **commande** et **OrderDetail** éléments ne sont pas imbriqués. Ils le sont dans l'exemple qui suit. Toutefois, aucune **msdata : Relationship** annotation est spécifiée ; par conséquent, une relation implicite est supposée. Pour plus d’informations, consultez [mappage implicite des Relations entre imbriqués éléments de schéma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md). Le schéma spécifie également des contraintes key et keyref.  
  
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
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
  
            <xs:element name="OrderDetail">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="OrderNo" type="xs:integer" />  
                  <xs:element name="ItemNo" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
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
  
 Le **DataSet** résultant du processus de mappage du schéma XML comprend deux tables :  
  
```  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 Le **DataSet** inclut également les deux relations (une basée sur le **msdata : Relationship** annotation et l’autre selon les contraintes key et keyref) ainsi que diverses contraintes. L'exemple suivant illustre ces relations et contraintes.  
  
```  
..RelationName: Order_OrderDetail  
..ParentTable: Order  
..ParentColumns: Order_Id  
..ChildTable: OrderDetail  
..ChildColumns: Order_Id  
..ParentKeyConstraint: Constraint1  
..ChildKeyConstraint: Order_OrderDetail  
..Nested: True  
  
..RelationName: OrderNoRef  
..ParentTable: Order  
..ParentColumns: OrderNumber  
..ChildTable: OrderDetail  
..ChildColumns: OrderNo  
..ParentKeyConstraint: OrderNumberKey  
..ChildKeyConstraint: OrderNoRef  
..Nested: False  
  
..ConstraintName: OrderNumberKey  
..Type: UniqueConstraint  
..Table: Order  
..Columns: OrderNumber  
..IsPrimaryKey: False  
  
..ConstraintName: Constraint1  
..Type: UniqueConstraint  
..Table: Order  
..Columns: Order_Id  
..IsPrimaryKey: True  
  
..ConstraintName: Order_OrderDetail  
..Type: ForeignKeyConstraint  
..Table: OrderDetail  
..Columns: Order_Id  
..RelatedTable: Order  
..RelatedColumns: Order_Id  
  
..ConstraintName: OrderNoRef  
..Type: ForeignKeyConstraint  
..Table: OrderDetail  
..Columns: OrderNo  
..RelatedTable: Order  
..RelatedColumns: OrderNumber  
```  
  
 Si une contrainte keyref faisant référence à une table imbriquée contient la **msdata : IsNested = « true »** annotation, le **DataSet** créera une seule relation imbriquée qui est basée sur la contrainte keyref et la contrainte de clé unique/connexe.  
  
## <a name="see-also"></a>Voir aussi  
 [Dérivation de la structure relationnelle des DataSets à partir du schéma XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
