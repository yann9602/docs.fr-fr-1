---
title: "Mapper des contraintes de sch&#233;ma XML (XSD) key sur des contraintes de DataSet | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Mapper des contraintes de sch&#233;ma XML (XSD) key sur des contraintes de DataSet
Dans un schéma, vous pouvez spécifier une contrainte de clé sur un élément ou un attribut à l'aide de l'élément **key**.  L'élément ou attribut sur lequel une contrainte de clé est spécifiée doit avoir des valeurs uniques dans toute instance du schéma et ne peut pas avoir de valeurs null.  
  
 La contrainte de clé est similaire à la contrainte unique, si ce n'est que la colonne sur laquelle une contrainte de clé est définie ne peut pas comporter de valeurs null.  
  
 Le tableau suivant présente les attributs **msdata** que vous pouvez spécifier dans l'élément **key**.  
  
|Nom d'attribut|Description|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|Si cet attribut est spécifié, sa valeur est utilisée comme nom de la contrainte.  Sinon, le nom de la contrainte est fourni par l'attribut **name**.|  
|**msdata:PrimaryKey**|Si `PrimaryKey="true"` est inclus, la propriété de contrainte **IsPrimaryKey** a la valeur **true**, en faisant ainsi une clé primaire.  La propriété de colonne **AllowDBNull** a la valeur **false** car les clés primaires ne peuvent pas contenir de valeurs null.|  
  
 En convertissant un schéma dans lequel une contrainte de clé est spécifiée, le processus de mappage crée une contrainte unique sur la table avec la propriété de colonne **AllowDBNull** ayant la valeur **false** pour chaque colonne mentionnée dans la contrainte.  La propriété **IsPrimaryKey** de la contrainte unique a également la valeur **false**, sauf si vous avez spécifié `msdata:PrimaryKey="true"` sur l'élément **key**.  Ce mode de fonctionnement est identique à celui d'une contrainte unique dans le schéma faisant apparaître `PrimaryKey="true"`.  
  
 Dans l'exemple de schéma suivant, l'élément **key** spécifie la contrainte de clé sur l'élément **CustomerID**.  
  
```  
<xs:schema id="cod"  
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
        <xs:element name="CompanyName" type="xs:string" minOccurs="0" />  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
<xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:key  msdata:PrimaryKey="true"  
       msdata:ConstraintName="KeyCustID"  
          name="KeyConstCustomerID" >  
     <xs:selector xpath=".//Customers" />  
     <xs:field xpath="CustomerID" />  
    </xs:key>  
 </xs:element>  
</xs:schema>   
```  
  
 L'élément **key** spécifie que les valeurs de l'élément enfant **CustomerID** de l'élément **Customers** doivent avoir des valeurs uniques et pas de valeurs null.  En convertissant le schéma en langage XSD \(XML Schema Definition\), le processus de mappage crée la table suivante :  
  
```  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 Le processus de mappage du schéma XML crée aussi une contrainte **UniqueConstraint** sur la colonne **CustomerID**, comme le montre le <xref:System.Data.DataSet> suivant.  \(Par souci de simplicité, seules les propriétés pertinentes sont représentées.\)  
  
```  
  
      DataSetName: MyDataSet  
TableName: customers  
  ColumnName: CustomerID  
      AllowDBNull: False  
      Unique: True  
  ConstraintName: KeyCustID  
      Table: customers  
      Columns: CustomerID   
      IsPrimaryKey: True  
```  
  
 Dans le **DataSet** généré, la propriété **IsPrimaryKey** de **UniqueConstraint** a la valeur **true** car le schéma spécifie `msdata:PrimaryKey="true"` dans l'élément **key**.  
  
 La valeur de la propriété **ConstraintName** de la contrainte **UniqueConstraint** du **DataSet** correspond à la valeur de l'attribut **msdata:ConstraintName** spécifié dans l'élément **key** du schéma.  
  
## Voir aussi  
 [Mappage de contraintes de schéma XML \(XSD\) à des contraintes de DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)   
 [Génération des relations d'un DataSet à partir d'un schéma XSD \(XML Schema Definition\)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)