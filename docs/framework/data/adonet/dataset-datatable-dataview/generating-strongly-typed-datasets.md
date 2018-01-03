---
title: "Génération de datasets fortement typés"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 54333cbf-bb43-4314-a7d4-6dc1dd1c44b3
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 867c6f5fa918b0886d8d618e89c62201cd92b213
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="generating-strongly-typed-datasets"></a>Génération de datasets fortement typés
À partir d'un schéma XML conforme à la norme XSD (XML Schema Definition), vous pouvez générer un <xref:System.Data.DataSet> fortement typé à l'aide de l'outil XSD.exe fourni avec le [!INCLUDE[winsdklong](../../../../../includes/winsdklong-md.md)].  
  
 (Pour créer un schéma xsd à partir des tables de base de données, consultez <xref:System.Data.DataSet.WriteXmlSchema%2A> ou [utilisation de Datasets dans Visual Studio](http://msdn.microsoft.com/library/8bw9ksd6.aspx)).  
  
 Le code suivant montre la syntaxe permettant de générer un **DataSet** à l’aide de cet outil.  
  
```  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 Dans cette syntaxe, la `/d` directive indique à l’outil pour générer un **DataSet**et le `/l:` indique le langage à utiliser (par exemple, c# ou Visual Basic .NET). Le paramètre facultatif `/eld` directive spécifie que vous pouvez utiliser [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)] interroger généré **jeu de données.** Cette option est utilisée lorsque l'option `/d` est également spécifiée. Pour plus d’informations, consultez [interrogation de DataSets typés](../../../../../docs/framework/data/adonet/querying-typed-datasets.md). Le paramètre facultatif `/n:` directive indique à l’outil de générer également un espace de noms pour le **DataSet** appelé **XSDSchema.Namespace**. La commande donne en sortie un fichier XSDSchemaFileName.cs, qui peut être compilé et utilisé dans une application ADO.NET. Le code généré peut être compilé sous la forme d'une bibliothèque ou d'un module.  
  
 Le code suivant montre la syntaxe permettant de compiler le code généré sous la forme d'une bibliothèque à l'aide du compilateur C# (csc.exe).  
  
```  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 La directive `/t:` donne à l'outil l'ordre de compiler en bibliothèque et les directives `/r:` spécifient les bibliothèques dépendantes requises pour la compilation. La commande donne en sortie un fichier XSDSchemaFileName.dll, qui peut être passé au compilateur au moment de la compilation d'une application ADO.NET avec la directive `/r:`.  
  
 Le code suivant montre la syntaxe permettant d'accéder à l'espace de noms passé à XSD.exe dans une application ADO.NET.  
  
```vb  
Imports XSDSchema.Namespace  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 L’exemple de code suivant utilise un typé **DataSet** nommé **CustomerDataSet** pour charger une liste de clients à partir de la **Northwind** base de données. Une fois que les données sont chargées à l’aide de la **remplir** (méthode), l’exemple boucle sur chaque client de la **clients** table en utilisant le typé **CustomersRow** ( **DataRow**) objet. Cela fournit un accès direct à la **CustomerID** colonne, que via les **DataColumnCollection**.  
  
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
  
 Vous trouverez ci-après le schéma XML utilisé pour l'exemple.  
  
```xml  
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
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataSet>  
 [Datasets typés](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [DataSets, DataTables et DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
