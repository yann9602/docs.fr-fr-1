---
title: "Contraintes et relations de sch&#233;ma XML | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Contraintes et relations de sch&#233;ma XML
Dans un schéma en langage XSD \(XML Schema Definition\), vous pouvez spécifier des contraintes \(unique, key et keyref\) et des relations \(à l'aide de l'annotation **msdata:Relationship**\).  Cette rubrique explique comment les contraintes et relations spécifiées dans un schéma XML sont interprétées pour générer l'objet <xref:System.Data.DataSet>.  
  
 En règle générale, dans un schéma XML, vous spécifiez l'annotation **msdata:Relationship** si vous souhaitez générer uniquement des relations dans le **DataSet**.  Pour plus d'informations, consultez [Génération des relations d'un DataSet à partir d'un schéma XSD \(XML Schema Definition\)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md).  Vous spécifiez des contraintes \(unique, key et keyref\) si vous souhaitez générer des contraintes dans le **DataSet**.  Notez que les contraintes key et keyref peuvent aussi servir à générer des relations, comme expliqué plus loin dans cette rubrique.  
  
## Génération d'une relation à partir des contraintes key et keyref  
 Au lieu de spécifier l'annotation **msdata:Relationship**, vous pouvez spécifier des contraintes key et keyref qui servent, lors du processus de mappage du schéma XML, à générer non seulement les contraintes, mais aussi la relation au sein du **DataSet**.  Toutefois, si vous spécifiez `msdata:ConstraintOnly="true"` dans l'élément **keyref**, le **DataSet** n'inclura que les contraintes, et pas la relation.  
  
 L'exemple suivant représente un schéma XML comprenant les éléments **Order** et **OrderDetail**, non imbriqués.  Le schéma spécifie également des contraintes key et keyref.  
  
```  
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
  
 Le **DataSet** généré au cours du processus de mappage du schéma XML comprend les tables **Order** et **OrderDetail**.  En outre, le **DataSet** inclut des relations et des contraintes.  L'exemple suivant illustre ces relations et contraintes.  Notez que le schéma ne spécifie pas l'annotation **msdata:Relationship**, mais que des contraintes key et keyref sont utilisées pour générer la relation.  
  
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
  
 Dans l'exemple de schéma précédent, les éléments **Order** et **OrderDetail** ne sont pas imbriqués.  Ils le sont dans l'exemple qui suit.  Toutefois, aucune annotation **msdata:Relationship** n'étant spécifiée, une relation implicite est supposée exister.  Pour plus d'informations, consultez [Mapper les relations implicites entre les éléments imbriqués d'un schéma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md).  Le schéma spécifie également des contraintes key et keyref.  
  
```  
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
  
 Le **DataSet** obtenu suite au processus de mappage du schéma XML comprend deux tables :  
  
```  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 Le **DataSet** comprend également les deux relations \(l'une basée sur l'annotation **msdata:relationship**, l'autre sur les contraintes key et keyref\), ainsi que diverses contraintes.  L'exemple suivant illustre ces relations et contraintes.  
  
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
  
 Si une contrainte keyref faisant référence à une table imbriquée contient l'annotation **msdata:IsNested\="true"**, le **DataSet** crée une seule relation imbriquée, basée sur la contrainte keyref et la contrainte unique\/key connexe.  
  
## Voir aussi  
 [Dérivation de la structure relationnelle d'un DataSet à partir d'un schéma XML \(XSD\)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)