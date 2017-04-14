---
title: "Mapper des relations sp&#233;cifi&#233;es pour des &#233;l&#233;ments imbriqu&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Mapper des relations sp&#233;cifi&#233;es pour des &#233;l&#233;ments imbriqu&#233;s
Un schéma peut inclure une annotation **msdata:Relationship** pour spécifier explicitement le mappage entre deux de ses éléments.  Les deux éléments spécifiés dans **msdata:Relationship** peuvent être imbriqués dans le schéma mais ce n'est pas indispensable.  Le processus de mappage utilise l'annotation **msdata:Relationship** du schéma pour générer la relation clé primaire\/clé étrangère entre les deux colonnes.  
  
 L'exemple suivant représente un schéma XML où **OrderDetail** est un élément enfant de **Order**.  L'annotation **msdata:Relationship** identifie cette relation parent\-enfant et spécifie que la colonne **OrderNumber** de la table **Order** obtenue est liée à la colonne **OrderNo** de la table **OrderDetail** obtenue.  
  
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
          <xs:annotation>  
           <xs:appinfo>  
            <msdata:Relationship name="OrdODRelation"   
                                msdata:parent="Order"   
                                msdata:child="OrderDetail"   
                                msdata:parentkey="OrderNumber"   
                                msdata:childkey="OrderNo"/>  
           </xs:appinfo>  
          </xs:annotation>  
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
  
 Le processus de mappage du schéma XML crée les éléments suivants dans le <xref:System.Data.DataSet> :  
  
-   Les tables **Order** et **OrderDetail**.  
  
    ```  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
-   Une relation entre les tables **Order** et **OrderDetail**.  La propriété **Nested** de cette relation a la valeur **True** car les éléments **Order** et **OrderDetail** sont imbriqués dans le schéma.  
  
    ```  
    ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 Le processus de mappage ne crée aucune contrainte.  
  
## Voir aussi  
 [Génération des relations d'un DataSet à partir d'un schéma XSD \(XML Schema Definition\)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)   
 [Mappage de contraintes de schéma XML \(XSD\) à des contraintes de DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)