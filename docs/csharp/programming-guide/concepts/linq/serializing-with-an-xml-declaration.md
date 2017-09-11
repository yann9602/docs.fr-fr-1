---
title: "Sérialisation avec une déclaration XML (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: c237fa4a-a042-40fd-886f-17b54c66bb75
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 36ffb8ddd584785c660896ca77707d504638852f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="serializing-with-an-xml-declaration-c"></a><span data-ttu-id="2c4d7-102">Sérialisation avec une déclaration XML (C#)</span><span class="sxs-lookup"><span data-stu-id="2c4d7-102">Serializing with an XML Declaration (C#)</span></span>
<span data-ttu-id="2c4d7-103">Cette rubrique décrit comment contrôler si la sérialisation génère une déclaration XML.</span><span class="sxs-lookup"><span data-stu-id="2c4d7-103">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="2c4d7-104">Génération de déclaration XML</span><span class="sxs-lookup"><span data-stu-id="2c4d7-104">XML Declaration Generation</span></span>  
 <span data-ttu-id="2c4d7-105">La sérialisation vers un objet <xref:System.IO.File> ou <xref:System.IO.TextWriter> à l'aide de la méthode <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName> ou <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName>génère une déclaration XML.</span><span class="sxs-lookup"><span data-stu-id="2c4d7-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName> method generates an XML declaration.</span></span> <span data-ttu-id="2c4d7-106">Lorsque vous sérialisez vers un objet <xref:System.Xml.XmlWriter>, les paramètres de writer (spécifiés dans un objet <xref:System.Xml.XmlWriterSettings>) déterminent si une déclaration XML est générée ou non.</span><span class="sxs-lookup"><span data-stu-id="2c4d7-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="2c4d7-107">Si vous sérialisez vers une chaîne à l'aide de la méthode `ToString`, le code XML résultant n'inclura pas de déclaration XML.</span><span class="sxs-lookup"><span data-stu-id="2c4d7-107">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="2c4d7-108">Sérialisation avec une déclaration XML</span><span class="sxs-lookup"><span data-stu-id="2c4d7-108">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="2c4d7-109">L'exemple suivant crée un objet <xref:System.Xml.Linq.XElement>, enregistre le document dans un fichier, puis imprime le fichier sur la console :</span><span class="sxs-lookup"><span data-stu-id="2c4d7-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child", "child content")  
);  
root.Save("Root.xml");  
string str = File.ReadAllText("Root.xml");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="2c4d7-110">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="2c4d7-110">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="2c4d7-111">Sérialisation sans déclaration XML</span><span class="sxs-lookup"><span data-stu-id="2c4d7-111">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="2c4d7-112">L'exemple suivant montre comment enregistrer un objet <xref:System.Xml.Linq.XElement> dans un objet <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="2c4d7-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
```csharp  
StringBuilder sb = new StringBuilder();  
XmlWriterSettings xws = new XmlWriterSettings();  
xws.OmitXmlDeclaration = true;  
  
using (XmlWriter xw = XmlWriter.Create(sb, xws)) {  
    XElement root = new XElement("Root",  
        new XElement("Child", "child content")  
    );  
    root.Save(xw);  
}  
Console.WriteLine(sb.ToString());  
```  
  
 <span data-ttu-id="2c4d7-113">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="2c4d7-113">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2c4d7-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2c4d7-114">See Also</span></span>  
 [<span data-ttu-id="2c4d7-115">Sérialisation d’arborescences XML (C#)</span><span class="sxs-lookup"><span data-stu-id="2c4d7-115">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)

