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
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapper les contraintes keyref de schéma XML (XSD) aux contraintes de DataSet
Le **keyref** élément vous permet d’établir des liens entre des éléments dans un document. Le résultat est similaire à une relation de clé étrangère dans une base de données relationnelle. Si un schéma spécifie le **keyref** élément, l’élément est converti pendant le processus de mappage de schéma pour une contrainte de clé étrangère correspondante sur les colonnes dans les tables de la <xref:System.Data.DataSet>. Par défaut, le **keyref** élément génère aussi une relation, avec les **ParentTable**, **ChildTable**, **ParentColumn**et  **ChildColumn** propriétés spécifiées sur la relation.  
  
 Le tableau suivant décrit les **msdata** attributs que vous pouvez spécifier dans le **keyref** élément.  
  
|Nom d'attribut|Description|  
|--------------------|-----------------|  
|**msdata : ConstraintOnly**|Si **ConstraintOnly = « true »** est spécifié sur le **keyref** élément dans le schéma, une contrainte est créée, mais aucune relation est créée. Si cet attribut n’est pas spécifié (ou a la valeur **False**), la contrainte et la relation sont créés dans le **DataSet**.|  
|**msdata : ConstraintName**|Si le **ConstraintName** attribut est spécifié, sa valeur est utilisée comme nom de la contrainte. Dans le cas contraire, le **nom** attribut de la **keyref** élément dans le schéma fournit le nom de la contrainte dans le **DataSet**.|  
|**msdata:UpdateRule**|Si le **UpdateRule** attribut est spécifié dans le **keyref** élément dans le schéma, sa valeur est assignée à la **UpdateRule** propriété contrainte dans le  **Jeu de données**. Dans le cas contraire le **UpdateRule** est définie sur **Cascade**.|  
|**msdata:DeleteRule**|Si le **DeleteRule** attribut est spécifié dans le **keyref** élément dans le schéma, sa valeur est assignée à la **DeleteRule** propriété contrainte dans le  **Jeu de données**. Dans le cas contraire le **DeleteRule** est définie sur **Cascade**.|  
|**msdata:AcceptRejectRule**|Si le **AcceptRejectRule** attribut est spécifié dans le **keyref** élément dans le schéma, sa valeur est assignée à la **AcceptRejectRule** propriété contrainte dans le  **Jeu de données**. Dans le cas contraire le **AcceptRejectRule** est définie sur **aucun**.|  
  
 L’exemple suivant contient un schéma qui spécifie le **clé** et **keyref** des relations entre les **OrderNumber** élément enfant de le **ordre**  élément et la **OrderNo** élément enfant de le **OrderDetail** élément.  
  
 Dans l’exemple, le **OrderNumber** élément enfant de le **OrderDetail** élément fait référence à la **OrderNo** élément enfant clé de la **commande**élément.  
  
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
  
 Le processus de mappage de schéma XML Schema definition langage (XSD XML) génère les éléments suivants **DataSet** avec deux tables :  
  
```  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 En outre, le **DataSet** définit les contraintes suivantes :  
  
-   Une contrainte unique sur la **commande** table.  
  
    ```  
              Table: Order  
    Columns: OrderNumber   
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
-   Une relation entre la **commande** et **OrderDetail** tables. Le **Nested** est définie sur **False** , car les deux éléments ne sont pas imbriqués dans le schéma.  
  
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
  
-   Une contrainte de clé étrangère sur la **OrderDetail** table.  
  
    ```  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo   
    RelatedTable: Order  
    RelatedColumns: OrderNumber   
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [Génération de relations de DataSet à partir du schéma XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
