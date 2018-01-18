---
title: "Dérivation de la structure relationnelle des DataSet à partir du schéma XML (XSD)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: eb4f6e3a63c901ec69ca5572a6f79d2f0ac4adfc
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>Dérivation de la structure relationnelle des DataSet à partir du schéma XML (XSD)
Cette section propose une vue d'ensemble de la façon dont le schéma relationnel d'un objet `DataSet` est construit à partir d'un document de schéma en langage XSD (XML Schema Definition). En règle générale, pour chaque `complexType` élément enfant d’un élément de schéma, une table est générée dans le `DataSet`. La structure de cette table est déterminée par la définition du type complexe. Tables sont créées dans le `DataSet` pour les éléments de niveau supérieur dans le schéma. Toutefois, une table est créée pour un niveau supérieur uniquement `complexType` élément lorsque la `complexType` élément est imbriqué dans une autre `complexType` élément, dans lequel cas imbriqué `complexType` élément est mappé à un `DataTable` dans le `DataSet`.  
  
 Pour plus d’informations sur le schéma XSD, consultez le World Wide Web Consortium (W3C) XML Schema Part 0 : Primer Recommendation, XML Schema Part 1 : Structures Recommendation et XML Schema Part 2 : Datatypes Recommendation, situé dans [http:// www.w3.org/](http://www.w3.org/TR/).  
  
 L’exemple suivant illustre un schéma XML où `customers` est l’élément enfant de le `MyDataSet` élément, qui est un **DataSet** élément.  
  
```xml  
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
  
 Dans l'exemple précédent, l'élément `customers` est un élément de type complexe. Par conséquent, la définition du type complexe est analysée et le processus de mappage crée la table suivante.  
  
```  
Customers (CustomerID , CompanyName, Phone)  
```  
  
 Le type de données de chaque colonne de la table est dérivé du type de schéma XML de l'élément ou de l'attribut spécifié correspondant.  
  
> [!NOTE]
>  Si l’élément `customers` est d’un type de données de schéma XML simple, tel que **entier**, aucune table n’est générée. Des tables sont créées uniquement pour les éléments de niveau supérieur de type complexe.  
  
 Dans le schéma XML suivant, la **schéma** élément a deux éléments enfants, `InStateCustomers` et `OutOfStateCustomers`.  
  
```xml  
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
  
 Les éléments enfants `InStateCustomers` et `OutOfStateCustomers` sont tous deux des éléments de type complexe (`customerType`). Par conséquent, le processus de mappage génère les deux tables identiques suivantes dans le `DataSet`.  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a>Dans cette section  
 [Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Décrit les éléments de schéma XML utilisés pour créer des contraintes de clé étrangères et uniques dans un `DataSet`.  
  
 [Génération de relations de DataSet à partir du schéma XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 Décrit les éléments de schéma XML utilisés pour créer des relations entre les colonnes de table dans un `DataSet`.  
  
 [Contraintes et relations du schéma XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/xml-schema-constraints-and-relationships.md)  
 Décrit comment les relations sont créées implicitement lors de l’utilisation des éléments de schéma XML pour créer des contraintes dans un `DataSet`.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Utilisation de XML dans un DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 Décrit comment charger et conserver la structure relationnelle et les données dans un `DataSet` en tant que données XML.  
  
## <a name="see-also"></a>Voir aussi  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
