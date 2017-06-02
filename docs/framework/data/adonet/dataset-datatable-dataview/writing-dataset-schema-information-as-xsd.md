---
title: "&#201;criture des informations de sch&#233;ma d&#39;un DataSet sous la forme de donn&#233;es XSD | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# &#201;criture des informations de sch&#233;ma d&#39;un DataSet sous la forme de donn&#233;es XSD
Vous pouvez écrire le schéma d'un objet <xref:System.Data.DataSet> sous la forme d'un schéma en langage XSD \(XML Schema Definition\), de façon à pouvoir le transporter, avec ou sans les données connexes, dans un document XML.  Le schéma XML peut être écrit dans un fichier, un flux, un objet <xref:System.Xml.XmlWriter> ou une chaîne ; il est utile pour la génération d'un **DataSet** fortement typé.  Pour plus d'informations sur les objets **DataSet** fortement typés, voir [DataSets typés](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).  
  
 Vous pouvez spécifier la façon dont la colonne d'une table est représentée dans un schéma XML à l'aide de la propriété **ColumnMapping** de l'objet <xref:System.Data.DataColumn>.  Pour plus d'informations, voir « Mappage de colonnes à des éléments, des attributs et du texte XML » dans [Écriture du contenu d'un DataSet sous forme de données XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).  
  
 Pour écrire le schéma d'un **DataSet** sous la forme d'un schéma XML, dans un fichier, un flux ou un **XmlWriter**, utilisez la méthode **WriteXmlSchema** du **DataSet**.  **WriteXmlSchema** accepte un paramètre, qui spécifie la destination du schéma XML obtenu.  Les exemples de code suivants montrent comment écrire le schéma XML d'un **DataSet** dans un fichier en passant une chaîne contenant un nom de fichier et un objet <xref:System.IO.StreamWriter>.  
  
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
  
 Pour obtenir le schéma d'un **DataSet** et l'écrire en tant que chaîne de schéma XML, utilisez la méthode **GetXmlSchema** comme le montre l'exemple suivant.  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## Voir aussi  
 [Utilisation de XML dans un DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)   
 [Écriture du contenu d'un DataSet sous forme de données XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)   
 [DataSets typés](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)   
 [Objets DataSet, DataTable et DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)