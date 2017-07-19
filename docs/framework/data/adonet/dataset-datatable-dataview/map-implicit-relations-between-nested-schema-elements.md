---
title: "Mapper les relations implicites entre les &#233;l&#233;ments imbriqu&#233;s d&#39;un sch&#233;ma | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Mapper les relations implicites entre les &#233;l&#233;ments imbriqu&#233;s d&#39;un sch&#233;ma
Un schéma en langage XSD \(XML Schema Definition\) peut présenter des types complexes imbriqués les uns dans les autres.  Dans ce cas, le processus de mappage applique le mappage par défaut et crée les différents éléments suivants dans l'objet <xref:System.Data.DataSet> :  
  
-   Une table pour chacun des types complexes \(parent et enfant\).  
  
-   Si aucune contrainte unique n'est définie pour le parent, chaque définition de table comprend une colonne clé primaire supplémentaire nommée selon le modèle *TableName*\_Id où *TableName* est le nom de la table parente.  
  
-   Une contrainte de clé primaire sur la table parente, identifiant la colonne supplémentaire en tant que clé primaire \(via l'assignation de la valeur **True** à la propriété **IsPrimaryKey**\).  La contrainte est nommée selon le modèle Constraint*\#*, où *\#* est 1, 2, 3, etc.  Par exemple, le nom par défaut de la première contrainte est Constraint1.  
  
-   Une contrainte de clé étrangère sur la table enfant, qui identifie la colonne supplémentaire en tant que clé étrangère faisant référence à la clé primaire de la table parente.  La contrainte est nommée sur le modèle *ParentTable\_ChildTable*, où *ParentTable* est le nom de la table parente et *ChildTable* celui de la table enfant.  
  
-   Une relation de données entre les tables parente et enfant.  
  
 L'exemple suivant représente un schéma où **OrderDetail** est un élément enfant de **Order**.  
  
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
  
 Le processus de mappage du schéma XML crée les éléments suivants dans le **DataSet**  :  
  
-   Les tables **Order** et **OrderDetail**.  
  
    ```  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
-   Une contrainte unique sur la table **Order**.  Notez que la propriété **IsPrimaryKey** a la valeur **True**.  
  
    ```  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
-   Une contrainte de clé étrangère sur la table **OrderDetail**.  
  
    ```  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
-   Une relation entre les tables **Order** et **OrderDetail**.  La propriété **Nested** de cette relation a la valeur **True** car les éléments **Order** et **OrderDetail** sont imbriqués dans le schéma.  
  
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
  
## Voir aussi  
 [Génération des relations d'un DataSet à partir d'un schéma XSD \(XML Schema Definition\)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)   
 [Mappage de contraintes de schéma XML \(XSD\) à des contraintes de DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)