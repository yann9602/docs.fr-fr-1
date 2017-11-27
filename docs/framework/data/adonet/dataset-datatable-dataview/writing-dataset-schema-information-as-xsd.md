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
ms.openlocfilehash: dde8a16ee0fbd86dacf6125c9a02209a794a5b74
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="writing-dataset-schema-information-as-xsd"></a><span data-ttu-id="a7556-102">Écriture des informations de schéma de DataSet comme XSD</span><span class="sxs-lookup"><span data-stu-id="a7556-102">Writing DataSet Schema Information as XSD</span></span>
<span data-ttu-id="a7556-103">Vous pouvez écrire le schéma d'un objet <xref:System.Data.DataSet> sous la forme d'un schéma en langage XSD (XML Schema Definition), de façon à pouvoir le transporter, avec ou sans les données connexes, dans un document XML.</span><span class="sxs-lookup"><span data-stu-id="a7556-103">You can write the schema of a <xref:System.Data.DataSet> as XML Schema definition language (XSD) schema, so that you can transport it, with or without related data, in an XML document.</span></span> <span data-ttu-id="a7556-104">Schéma XML peuvent être écrites dans un fichier, un flux, un <xref:System.Xml.XmlWriter>, ou une chaîne ; il est utile pour générer un fortement typé **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="a7556-104">XML Schema can be written to a file, a stream, an <xref:System.Xml.XmlWriter>, or a string; it is useful for generating a strongly typed **DataSet**.</span></span> <span data-ttu-id="a7556-105">Pour plus d’informations sur fortement typées **DataSet** , consultez [typés](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="a7556-105">For more information about strongly typed **DataSet** objects, see [Typed DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span></span>  
  
 <span data-ttu-id="a7556-106">Vous pouvez spécifier la façon dont une colonne d’une table est représentée dans le schéma XML à l’aide de la **ColumnMapping** propriété de la <xref:System.Data.DataColumn> objet.</span><span class="sxs-lookup"><span data-stu-id="a7556-106">You can specify how a column of a table is represented in XML Schema using the **ColumnMapping** property of the <xref:System.Data.DataColumn> object.</span></span> <span data-ttu-id="a7556-107">Pour plus d’informations, consultez « Mappage des colonnes de texte, des attributs et des éléments XML » dans [contenu l’écriture d’un DataSet en tant que données XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="a7556-107">For more information, see "Mapping Columns to XML Elements, Attributes, and Text" in [Writing DataSet Contents as XML Data](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).</span></span>  
  
 <span data-ttu-id="a7556-108">Pour écrire le schéma d’un **DataSet** comme un schéma XML, dans un fichier, flux, ou **XmlWriter**, utiliser le **WriteXmlSchema** méthode de la **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="a7556-108">To write the schema of a **DataSet** as XML Schema, to a file, stream, or **XmlWriter**, use the **WriteXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="a7556-109">**WriteXmlSchema** prend un paramètre qui spécifie la destination du schéma XML obtenu.</span><span class="sxs-lookup"><span data-stu-id="a7556-109">**WriteXmlSchema** takes one parameter that specifies the destination of the resulting XML Schema.</span></span> <span data-ttu-id="a7556-110">Les exemples de code suivants montrent comment écrire le schéma XML d’un **DataSet** dans un fichier en passant une chaîne contenant un nom de fichier et un <xref:System.IO.StreamWriter> objet.</span><span class="sxs-lookup"><span data-stu-id="a7556-110">The following code examples demonstrate how to write the XML Schema of a **DataSet** to a file by passing a string containing a file name and a <xref:System.IO.StreamWriter> object.</span></span>  
  
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
  
 <span data-ttu-id="a7556-111">Pour obtenir le schéma d’un **DataSet** et les écrire en tant que chaîne de schéma XML, utilisez la **GetXmlSchema** méthode, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="a7556-111">To obtain the schema of a **DataSet** and write it as an XML Schema string, use the **GetXmlSchema** method, as shown in the following example.</span></span>  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a><span data-ttu-id="a7556-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7556-112">See Also</span></span>  
 [<span data-ttu-id="a7556-113">Utilisation de XML dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="a7556-113">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="a7556-114">L’écriture du contenu d’un DataSet en tant que données XML</span><span class="sxs-lookup"><span data-stu-id="a7556-114">Writing DataSet Contents as XML Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 [<span data-ttu-id="a7556-115">Datasets typés</span><span class="sxs-lookup"><span data-stu-id="a7556-115">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [<span data-ttu-id="a7556-116">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="a7556-116">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="a7556-117">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="a7556-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
