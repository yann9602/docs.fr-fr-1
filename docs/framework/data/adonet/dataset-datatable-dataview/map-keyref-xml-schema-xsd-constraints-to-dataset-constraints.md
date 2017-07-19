---
title: "Mapper des contraintes de sch&#233;ma XML (XSD) keyref sur des contraintes de DataSet | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Mapper des contraintes de sch&#233;ma XML (XSD) keyref sur des contraintes de DataSet
L'élément **keyref** vous permet d'établir des liens entre différents éléments figurant dans un document.  Le résultat est similaire à une relation de clé étrangère dans une base de données relationnelle.  Si un schéma spécifie l'élément **keyref**, au cours du processus de mappage du schéma, l'élément est converti en une contrainte de clé étrangère correspondante sur les colonnes des tables de l'objet <xref:System.Data.DataSet>.  Par défaut, l'élément **keyref** génère aussi une relation, avec les propriétés **ParentTable**, **ChildTable**, **ParentColumn** et **ChildColumn** spécifiées pour la relation.  
  
 Le tableau suivant présente les attributs **msdata** que vous pouvez spécifier dans l'élément **keyref**.  
  
|Nom d'attribut|Description|  
|--------------------|-----------------|  
|**msdata:ConstraintOnly**|Si **ConstraintOnly\="true"** est spécifié sur l'élément **keyref** du schéma, une contrainte est créée, mais aucune relation ne l'est.  Si cet attribut n'est pas spécifié \(ou s'il a la valeur **False**\), la contrainte et la relation sont toutes deux créées dans le **DataSet**.|  
|**msdata:ConstraintName**|Si l'attribut **ConstraintName** est spécifié, sa valeur est utilisée comme nom de la contrainte.  Sinon, l'attribut **name** de l'élément **keyref** du schéma fournit le nom de la contrainte dans le **DataSet**.|  
|**msdata:UpdateRule**|Si l'attribut **UpdateRule** est spécifié dans l'élément **keyref** du schéma, sa valeur est assignée à la propriété **UpdateRule** de la contrainte dans le **DataSet**.  Sinon, la propriété **UpdateRule** a la valeur **Cascade**.|  
|**msdata:DeleteRule**|Si l'attribut **DeleteRule** est spécifié dans l'élément **keyref** du schéma, sa valeur est assignée à la propriété **DeleteRule** de la contrainte dans le **DataSet**.  Sinon, la propriété **DeleteRule** a la valeur **Cascade**.|  
|**msdata:AcceptRejectRule**|Si l'attribut **AcceptRejectRule** est spécifié dans l'élément **keyref** du schéma, sa valeur est assignée à la propriété **AcceptRejectRule** de la contrainte dans le **DataSet**.  Sinon, la propriété **AcceptRejectRule** a la valeur **None**.|  
  
 L'exemple suivant contient un schéma qui spécifie les relations **key** et **keyref** entre l'élément enfant **OrderNumber** de l'élément **Order** et l'élément enfant **OrderNo** de l'élément **OrderDetail**.  
  
 Dans cet exemple, l'élément enfant **OrderNumber** de l'élément **OrderDetail** fait référence à l'élément enfant clé **OrderNo** de l'élément **Order**.  
  
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
  
 Le processus de mappage du schéma en langage XSD \(XML Schema Definition\) produit le **DataSet** suivant, qui comporte deux tables :  
  
```  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 En outre, le **DataSet** définit les contraintes suivantes :  
  
-   Une contrainte unique sur la table **Order**.  
  
    ```  
  
              Table: Order  
    Columns: OrderNumber   
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
-   Une relation entre les tables **Order** et **OrderDetail**.  La propriété **Nested** a la valeur **False** car les deux éléments ne sont pas imbriqués dans le schéma.  
  
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
  
-   Une contrainte de clé étrangère sur la table **OrderDetail**.  
  
    ```  
  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo   
    RelatedTable: Order  
    RelatedColumns: OrderNumber   
    ```  
  
## Voir aussi  
 [Mappage de contraintes de schéma XML \(XSD\) à des contraintes de DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)   
 [Génération des relations d'un DataSet à partir d'un schéma XSD \(XML Schema Definition\)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)