---
title: "D&#233;rivation de la structure relationnelle d&#39;un DataSet &#224; partir d&#39;un sch&#233;ma XML (XSD) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# D&#233;rivation de la structure relationnelle d&#39;un DataSet &#224; partir d&#39;un sch&#233;ma XML (XSD)
Cette section propose une vue d'ensemble de la façon dont le schéma relationnel d'un objet <xref:System.Data.DataSet> est construit à partir d'un document de schéma en langage XSD \(XML Schema Definition\).  En règle générale, pour chaque élément enfant **complexType** d'un élément de schéma, une table est générée dans le **DataSet**.  La structure de cette table est déterminée par la définition du type complexe.  Des tables sont créées dans le **DataSet** pour les éléments de niveau supérieur du schéma.  Toutefois, une table est créée pour un élément **complexType** de niveau supérieur uniquement lorsque l'élément **complexType** est imbriqué dans un autre élément **complexType**, auquel cas l'élément **complexType** imbriqué est mappé à un objet <xref:System.Data.DataTable> du **DataSet**.  
  
 Pour plus d'informations sur le XSD, consultez les recommandations suivantes du World Wide Web Consortium \(W3C\) : XML Schema Part 0 : Primer Recommendation, XML Schema Part 1 : Structures Recommendation et XML Schema Part 2 : Datatypes Recommendation, publiées sur le site [http:\/\/www.w3.org\/](http://www.w3.org/TR/).  
  
 L'exemple suivant présente un schéma XML où `customers` est l'élément enfant de l'élément `MyDataSet`, qui est un élément du **DataSet**.  
  
```  
<xs:schema id="SomeID"   
            xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element name="customers" >   
           <xs:complexType >  
             <xs:sequence>  
               <xs:element name="CustomerID" type="xs:integer"   
                            minOccurs="0" />  
               <xs:element name="CompanyName" type="xs:string"   
                            minOccurs="0" />  
               <xs:element name="Phone" type="xs:string" />  
             </xs:sequence>  
           </xs:complexType>  
          </xs:element>  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 Dans l'exemple précédent, l'élément `customers` est un élément de type complexe.  Par conséquent, la définition du type complexe est analysée et le processus de mappage crée la table suivante.  
  
```  
Customers (CustomerID , CompanyName, Phone)  
```  
  
 Le type de données de chaque colonne de la table est dérivé du type de schéma XML de l'élément ou de l'attribut spécifié correspondant.  
  
> [!NOTE]
>  Si l'élément `customers` est d'un type de données de schéma XML simple, comme **integer**, aucune table n'est générée.  Des tables sont créées uniquement pour les éléments de niveau supérieur de type complexe.  
  
 Dans le schéma XML suivant, l'élément **Schema** a deux éléments enfants, `InStateCustomers` et `OutOfStateCustomers`.  
  
```  
<xs:schema id="SomeID"   
            xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="InStateCustomers" type="customerType" />  
   <xs:element name="OutOfStateCustomers" type="customerType" />  
    <xs:complexType name="customerType" >  
  
     </xs:complexType>  
  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element ref="customers" />  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 Les éléments enfants `InStateCustomers` et `OutOfStateCustomers` sont tous deux des éléments de type complexe \(`customerType`\).  Par conséquent, le processus de mappage génère les deux tables identiques suivantes dans le **DataSet**.  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## Dans cette section  
 [Mappage de contraintes de schéma XML \(XSD\) à des contraintes de DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Décrit les éléments de schéma XML qui servent à créer des contraintes uniques et de clé étrangère dans un **DataSet**.  
  
 [Génération des relations d'un DataSet à partir d'un schéma XSD \(XML Schema Definition\)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 Décrit les éléments de schéma XML qui servent à créer des relations entre les colonnes de table dans un **DataSet**.  
  
 [Contraintes et relations de schéma XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/xml-schema-constraints-and-relationships.md)  
 Explique comment des relations sont créées implicitement lors de l'utilisation d'éléments de schéma XML pour créer des contraintes dans un **DataSet**.  
  
## Rubriques connexes  
 [Utilisation de XML dans un DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 Explique comment charger et conserver la structure relationnelle et les données d'un **DataSet** sous forme de données XML.  
  
## Voir aussi  
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)