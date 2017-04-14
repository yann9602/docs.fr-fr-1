---
title: "G&#233;n&#233;ration des relations d&#39;un DataSet &#224; partir d&#39;un sch&#233;ma XSD (XML Schema Definition) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# G&#233;n&#233;ration des relations d&#39;un DataSet &#224; partir d&#39;un sch&#233;ma XSD (XML Schema Definition)
Dans un objet <xref:System.Data.DataSet>, vous créez une association entre deux ou plusieurs colonnes en établissant une relation parent\-enfant.  Il existe trois possibilités pour représenter une relation de **DataSet** dans un schéma en langage XSD \(XML Schema Definition\) :  
  
-   spécifier des types complexes imbriqués ;  
  
-   utiliser l'annotation **msdata:Relationship** ;  
  
-   spécifier un **xs:keyref** sans annotation **msdata:ConstraintOnly**.  
  
## Types complexes imbriqués  
 Les définitions de types complexes imbriqués dans un schéma indiquent les relations parent\-enfant des éléments.  Le fragment de schéma XML suivant montre que **OrderDetail** est un élément enfant de l'élément **Order**.  
  
```  
<xs:element name="Order">  
  <xs:complexType>  
     <xs:sequence>          
       <xs:element name="OrderDetail" />  
           <xs:complexType>               
           </xs:complexType>  
     </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 Le processus de mappage du schéma XML crée dans le **DataSet** des tables qui correspondent aux types complexes imbriqués du schéma.  Il crée également des colonnes supplémentaires utilisées comme colonnes parent**\-**enfant pour les tables générées.  Notez que ces colonnes parent**\-**enfant spécifient des relations, à ne pas confondre avec les contraintes de clé primaire\/clé étrangère.  
  
## Annotation msdata:Relationship  
 L'annotation **msdata:Relationship** vous permet de spécifier explicitement les relations parent\-enfant existant entre différents éléments non imbriqués du schéma.  L'exemple suivant représente la structure de l'élément **Relationship**.  
  
```  
  
  <msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 Les attributs de l'annotation **msdata:Relationship** identifient les éléments impliqués dans la relation parent\-enfant, ainsi que les éléments et attributs de **parentkey** et **childkey** impliqués dans la relation.  Le processus de mappage exploite ces informations pour générer des tables dans le **DataSet** et pour créer la relation clé primaire\/clé étrangère entre ces différentes tables.  
  
 Par exemple, le fragment de schéma suivant spécifie que les éléments **Order** et **OrderDetail** se situent au même niveau \(ne sont pas imbriqués\).  Le schéma comporte une annotation **msdata:Relationship**, qui spécifie la relation parent\-enfant entre ces deux éléments.  Dans ce cas, une relation explicite doit être spécifiée à l'aide de l'annotation **msdata:Relationship**.  
  
```  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
        <xs:element name="OrderDetail">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
       <xs:element name="Order">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
    </xs:choice>  
  </xs:complexType>  
</xs:element>  
   <xs:annotation>  
     <xs:appinfo>  
       <msdata:Relationship name="OrdOrdDetailRelation"  
          msdata:parent="Order"  
          msdata:child="OrderDetail"   
          msdata:parentkey="OrderNumber"  
          msdata:childkey="OrderNo"/>  
     </xs:appinfo>  
  </xs:annotation>  
  
```  
  
 Le processus de mappage utilise l'élément **Relationship** pour créer une relation parent\-enfant entre la colonne **OrderNumber** de la table **Order** et la colonne **OrderNo** de la table **OrderDetail** du **DataSet**.  Il ne spécifie que la relation ; il ne spécifie pas automatiquement de contraintes sur les valeurs de ces colonnes comme le font des contraintes de clé primaire\/clé étrangère dans des bases de données relationnelles.  
  
### Dans cette section  
 [Mapper les relations implicites entre les éléments imbriqués d'un schéma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md)  
 Décrit les contraintes et relations implicitement créées dans un **DataSet** lorsque le schéma XML contient des éléments imbriqués.  
  
 [Mapper des relations spécifiées pour des éléments imbriqués](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-relations-specified-for-nested-elements.md)  
 Explique comment définir explicitement des relations dans un **DataSet** pour les éléments imbriqués d'un schéma XML.  
  
 [Spécifier les relations entre des éléments qui ne sont pas imbriqués](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/specify-relations-between-elements-with-no-nesting.md)  
 Explique comment créer des relations dans un **DataSet** pour les éléments de schéma XML qui ne sont pas imbriqués.  
  
### Rubriques connexes  
 [Dérivation de la structure relationnelle d'un DataSet à partir d'un schéma XML \(XSD\)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Décrit la structure relationnelle, ou schéma, d'un **DataSet** créé à partir d'un schéma en langage XSD \(XML Schema Definition\).  
  
 [Mappage de contraintes de schéma XML \(XSD\) à des contraintes de DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Décrit les éléments de schéma XML qui servent à créer des contraintes uniques et de clé étrangère dans un **DataSet**.  
  
## Voir aussi  
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)