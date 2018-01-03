---
title: "Mapper les contraintes uniques de schéma XML (XSD) aux contraintes de DataSet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 5276697ebdc065965d970afc4ac2ef6be61c8f20
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapper les contraintes uniques de schéma XML (XSD) aux contraintes de DataSet
Dans un schéma de langage (XSD XML) de définition de schéma XML, le **unique** élément spécifie la contrainte d’unicité sur un élément ou attribut. Dans le processus de conversion d'un schéma XML en schéma relationnel, la contrainte unique spécifiée sur un élément ou un attribut du schéma XML est mappée à une contrainte unique dans l'objet <xref:System.Data.DataTable> de l'objet <xref:System.Data.DataSet> correspondant qui est généré.  
  
 Le tableau suivant décrit les **msdata** les attributs que vous pouvez spécifier dans le **unique** élément.  
  
|Nom d'attribut|Description|  
|--------------------|-----------------|  
|**msdata : ConstraintName**|Si cet attribut est spécifié, sa valeur est utilisée comme nom de la contrainte. Dans le cas contraire, le **nom** attribut fournit la valeur de la contrainte.|  
|**msdata : PrimaryKey**|Si `PrimaryKey="true"` est présent dans le **unique** élément, une contrainte unique est créée avec le **IsPrimaryKey** propriété **true**.|  
  
 L’exemple suivant montre un schéma XML qui utilise le **unique** élément pour spécifier une contrainte d’unicité.  
  
```xml  
<xs:schema id="SampleDataSet"   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:integer"   
           minOccurs="0"/>  
        <xs:element name="CompanyName" type="xs:string"   
           minOccurs="0"/>  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
  
 <xs:element name="SampleDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:unique     msdata:ConstraintName="UCustID"     name="UniqueCustIDConstr" >       <xs:selector xpath=".//Customers" />       <xs:field xpath="CustomerID" />     </xs:unique>  
</xs:element>  
</xs:schema>  
```  
  
 Le **unique** élément dans le schéma spécifie que, pour toutes les **clients** éléments dans un document d’instance, la valeur de la **CustomerID** élément enfant doit être unique. Dans la construction du **DataSet**, le processus de mappage lit ce schéma et crée la table suivante :  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 Le processus de mappage crée aussi une contrainte unique sur la **CustomerID** colonne, comme le montre l’exemple suivant **DataSet**. (Par souci de simplicité, seules les propriétés pertinentes sont représentées.)  
  
```  
      DataSetName: MyDataSet  
TableName: Customers  
  ColumnName: CustomerID  
      AllowDBNull: True  
      Unique: True  
  ConstraintName: UcustID       Type: UniqueConstraint  
      Table: Customers  
      Columns: CustomerID   
      IsPrimaryKey: False  
```  
  
 Dans le **DataSet** qui est généré, le **IsPrimaryKey** est définie sur **False** pour la contrainte unique. Le **unique** sur la colonne indique que la **CustomerID** les valeurs de colonne doivent être uniques (mais elles peuvent être une référence null, comme spécifié par le **AllowDBNull** propriété de la colonne).  
  
 Si vous modifiez le schéma et définir le paramètre facultatif **msdata : PrimaryKey** valeur d’attribut **True**, la contrainte unique est créée sur la table. Le **AllowDBNull** colonne est définie sur **False**et le **IsPrimaryKey** propriétés de la contrainte de valeur **True**, faisant ainsi le **CustomerID** colonne une colonne clé primaire.  
  
 Vous pouvez spécifier une contrainte unique sur une combinaison d'éléments ou d'attributs dans le schéma XML. L’exemple suivant montre comment spécifier qu’une combinaison de **CustomerID** et **CompanyName** valeurs doivent être uniques pour tous les **clients** dans n’importe quelle instance, par Ajout d’un autre **xs : Field** élément dans le schéma.  
  
```xml  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 Ceci est la contrainte qui est créée dans la boîte **DataSet**.  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [Génération de relations de DataSet à partir du schéma XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
