---
title: "Mapper des contraintes de sch&#233;ma XML (XSD) uniques sur des contraintes de DataSet | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Mapper des contraintes de sch&#233;ma XML (XSD) uniques sur des contraintes de DataSet
Dans un schéma en langage XSD \(XML Schema Definition\), l'élément **unique** spécifie la contrainte unique sur un élément ou un attribut.  Dans le processus de conversion d'un schéma XML en schéma relationnel, la contrainte unique spécifiée sur un élément ou un attribut du schéma XML est mappée à une contrainte unique dans l'objet <xref:System.Data.DataTable> de l'objet <xref:System.Data.DataSet> correspondant qui est généré.  
  
 Le tableau suivant présente les attributs **msdata** que vous pouvez spécifier dans l'élément **unique**.  
  
|Nom d'attribut|Description|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|Si cet attribut est spécifié, sa valeur est utilisée comme nom de la contrainte.  Sinon, le nom de la contrainte est fourni par l'attribut **name**.|  
|**msdata:PrimaryKey**|Si `PrimaryKey="true"` figure dans l'élément **unique**, une contrainte unique est créée avec la propriété **IsPrimaryKey** ayant pour valeur **true**.|  
  
 L'exemple suivant représente un schéma XML qui utilise l'élément **unique** pour spécifier une contrainte unique.  
  
```  
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
   <xs:unique      
msdata:ConstraintName="UCustID"      
name="UniqueCustIDConstr" >        
<xs:selector xpath=".//Customers" />        
<xs:field xpath="CustomerID" />      
</xs:unique>  
</xs:element>  
</xs:schema>  
```  
  
 L'élément **unique** du schéma spécifie que la valeur de l'élément enfant **CustomerID** doit être unique pour tous les éléments **Customers** d'une instance du document.  Lors de la génération du **DataSet**, le processus de mappage lit ce schéma et crée la table suivante :  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 Le processus de mappage crée aussi une contrainte unique sur la colonne **CustomerID**, comme le montre le **DataSet** suivant.  \(Par souci de simplicité, seules les propriétés pertinentes sont représentées.\)  
  
```  
  
      DataSetName: MyDataSet  
TableName: Customers  
  ColumnName: CustomerID  
      AllowDBNull: True  
      Unique: True  
  ConstraintName: UcustID  
      Type: UniqueConstraint  
      Table: Customers  
      Columns: CustomerID   
      IsPrimaryKey: False  
```  
  
 Dans le **DataSet** généré, la propriété **IsPrimaryKey** a la valeur **False** pour la contrainte unique.  La propriété **unique** sur la colonne indique que les valeurs de la colonne **CustomerID** doivent être uniques \(mais elles peuvent être une référence null, comme spécifié par la propriété **AllowDBNull** de la colonne\).  
  
 Si vous modifiez le schéma et spécifiez pour l'attribut facultatif **msdata:PrimaryKey** la valeur **True**, la contrainte unique est créée sur la table.  La propriété **AllowDBNull** de la colonne a la valeur **False** et la propriété **IsPrimaryKey** de la contrainte a la valeur **True**, faisant ainsi de la colonne **CustomerID** une colonne clé primaire.  
  
 Vous pouvez spécifier une contrainte unique sur une combinaison d'éléments ou d'attributs dans le schéma XML.  L'exemple suivant montre comment spécifier qu'une combinaison des valeurs de **CustomerID** et de **CompanyName** doit être unique pour tous les **Customers** d'une instance, en ajoutant un autre élément **xs:field** au schéma.  
  
```  
  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 Cela est la contrainte créée dans le **DataSet** obtenu.  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## Voir aussi  
 [Mappage de contraintes de schéma XML \(XSD\) à des contraintes de DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)   
 [Génération des relations d'un DataSet à partir d'un schéma XSD \(XML Schema Definition\)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)