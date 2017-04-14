---
title: "G&#233;n&#233;ration d&#39;objets DataSet fortement typ&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 54333cbf-bb43-4314-a7d4-6dc1dd1c44b3
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# G&#233;n&#233;ration d&#39;objets DataSet fortement typ&#233;s
À partir d'un schéma XML conforme à la norme XSD \(XML Schema Definition\), vous pouvez générer un <xref:System.Data.DataSet> fortement typé à l'aide de l'outil XSD.exe fourni avec le [!INCLUDE[winsdklong](../../../../../includes/winsdklong-md.md)].  
  
 \(Pour créer une définition XSD à partir de tables de base de données, consultez <xref:System.Data.DataSet.WriteXmlSchema%2A> ou [Utilisation de datasets dans Visual Studio](http://msdn.microsoft.com/library/8bw9ksd6.aspx).\)  
  
 Le code suivant montre la syntaxe permettant de générer un **DataSet** à l'aide de cet outil.  
  
```  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 Dans cette syntaxe, la directive `/d` donne à l'outil l'ordre de générer un **DataSet** et `/l:` indique le langage à utiliser \(par exemple, C\# ou Visual Basic .NET\).  La directive `/eld` facultative spécifie que vous pouvez utiliser la fonctionnalité [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)] pour effectuer une requête sur le **DataSet** généré. Cette option est utilisée lorsque l'option `/d` est également spécifiée.  Pour plus d'informations, consultez [Interrogation de DataSets typés](../../../../../docs/framework/data/adonet/querying-typed-datasets.md).  La directive facultative `/n:` indique à l'outil de générer également un espace de noms pour le **DataSet**, nommé **XSDSchema.Namespace**.  La commande donne en sortie un fichier XSDSchemaFileName.cs, qui peut être compilé et utilisé dans une application ADO.NET.  Le code généré peut être compilé sous la forme d'une bibliothèque ou d'un module.  
  
 Le code suivant montre la syntaxe permettant de compiler le code généré sous la forme d'une bibliothèque à l'aide du compilateur C\# \(csc.exe\).  
  
```  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 La directive `/t:` donne à l'outil l'ordre de compiler en bibliothèque et les directives `/r:` spécifient les bibliothèques dépendantes requises pour la compilation.  La commande donne en sortie un fichier XSDSchemaFileName.dll, qui peut être passé au compilateur au moment de la compilation d'une application ADO.NET avec la directive `/r:`.  
  
 Le code suivant montre la syntaxe permettant d'accéder à l'espace de noms passé à XSD.exe dans une application ADO.NET.  
  
```vb  
Imports XSDSchema.Namespace  
  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 L'exemple de code suivant utilise un **DataSet** typé nommé **CustomerDataSet** pour charger une liste de clients à partir de la base de données **Northwind**.  Une fois les données chargées à l'aide de la méthode **Fill**, l'exemple boucle sur chaque client de la table **Customers** à l'aide de l'objet typé **CustomersRow** \(**DataRow**\).  La colonne **CustomerID** est ainsi accessible directement, plutôt que via le **DataColumnCollection**.  
  
```vb  
Dim customers As CustomerDataSet= New CustomerDataSet()  
Dim adapter As SqlDataAdapter New SqlDataAdapter( _  
  "SELECT * FROM dbo.Customers;", _  
  "Data Source=(local);Integrated " & _  
  "Security=SSPI;Initial Catalog=Northwind")  
  
adapter.Fill(customers, "Customers")  
  
Dim customerRow As CustomerDataSet.CustomersRow  
For Each customerRow In customers.Customers  
  Console.WriteLine(customerRow.CustomerID)  
Next  
  
```  
  
```csharp  
CustomerDataSet customers = new CustomerDataSet();  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT * FROM dbo.Customers;",  
  "Data Source=(local);Integrated " +  
  "Security=SSPI;Initial Catalog=Northwind");  
  
adapter.Fill(customers, "Customers");  
  
foreach(CustomerDataSet.CustomersRow customerRow in customers.Customers)  
  Console.WriteLine(customerRow.CustomerID);  
```  
  
 Vous trouverez ci\-après le schéma XML utilisé pour l'exemple.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet" xmlns="" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
## Voir aussi  
 <xref:System.Data.DataColumnCollection>   
 <xref:System.Data.DataSet>   
 [DataSets typés](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)   
 [Objets DataSet, DataTable et DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)