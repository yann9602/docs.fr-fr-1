---
title: "Écriture des informations de schéma de DataSet comme XSD"
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
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 95f8a5d4d03c349467cbd13976ca9023470735aa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="writing-dataset-schema-information-as-xsd"></a>Écriture des informations de schéma de DataSet comme XSD
Vous pouvez écrire le schéma d'un objet <xref:System.Data.DataSet> sous la forme d'un schéma en langage XSD (XML Schema Definition), de façon à pouvoir le transporter, avec ou sans les données connexes, dans un document XML. Schéma XML peuvent être écrites dans un fichier, un flux, un <xref:System.Xml.XmlWriter>, ou une chaîne ; il est utile pour générer un fortement typé **DataSet**. Pour plus d’informations sur fortement typées **DataSet** , consultez [typés](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).  
  
 Vous pouvez spécifier la façon dont une colonne d’une table est représentée dans le schéma XML à l’aide de la **ColumnMapping** propriété de la <xref:System.Data.DataColumn> objet. Pour plus d’informations, consultez « Mappage des colonnes de texte, des attributs et des éléments XML » dans [contenu l’écriture d’un DataSet en tant que données XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).  
  
 Pour écrire le schéma d’un **DataSet** comme un schéma XML, dans un fichier, flux, ou **XmlWriter**, utiliser le **WriteXmlSchema** méthode de la **DataSet**. **WriteXmlSchema** prend un paramètre qui spécifie la destination du schéma XML obtenu. Les exemples de code suivants montrent comment écrire le schéma XML d’un **DataSet** dans un fichier en passant une chaîne contenant un nom de fichier et un <xref:System.IO.StreamWriter> objet.  
  
```vb  
dataSet.WriteXmlSchema("Customers.xsd")  
```  
  
```csharp  
dataSet.WriteXmlSchema("Customers.xsd");  
```  
  
```vb  
Dim writer As System.IO.StreamWriter = New System.IO.StreamWriter("Customers.xsd")  
dataSet.WriteXmlSchema(writer)  
writer.Close()  
```  
  
```csharp  
System.IO.StreamWriter writer = new System.IO.StreamWriter("Customers.xsd");  
dataSet.WriteXmlSchema(writer);  
writer.Close();  
```  
  
 Pour obtenir le schéma d’un **DataSet** et les écrire en tant que chaîne de schéma XML, utilisez la **GetXmlSchema** méthode, comme indiqué dans l’exemple suivant.  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de XML dans un DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Écriture du contenu d’un DataSet comme données XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 [Datasets typés](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [DataSets, DataTables et DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
