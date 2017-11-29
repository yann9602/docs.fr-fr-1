---
title: "Sérialisation avec une déclaration XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8726f79e-2bb0-4ba0-969d-197cca591647
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e8544157104b202a36f2ef75b069bcdd297b9158
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="serializing-with-an-xml-declaration-visual-basic"></a><span data-ttu-id="969b6-102">Sérialisation avec une déclaration XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="969b6-102">Serializing with an XML Declaration (Visual Basic)</span></span>
<span data-ttu-id="969b6-103">Cette rubrique décrit comment contrôler si la sérialisation génère une déclaration XML.</span><span class="sxs-lookup"><span data-stu-id="969b6-103">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="969b6-104">Génération de déclaration XML</span><span class="sxs-lookup"><span data-stu-id="969b6-104">XML Declaration Generation</span></span>  
 <span data-ttu-id="969b6-105">La sérialisation vers un objet <xref:System.IO.File> ou <xref:System.IO.TextWriter> à l'aide de la méthode <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> ou <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>génère une déclaration XML.</span><span class="sxs-lookup"><span data-stu-id="969b6-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="969b6-106">Lorsque vous sérialisez vers un objet <xref:System.Xml.XmlWriter>, les paramètres de writer (spécifiés dans un objet <xref:System.Xml.XmlWriterSettings>) déterminent si une déclaration XML est générée ou non.</span><span class="sxs-lookup"><span data-stu-id="969b6-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="969b6-107">Si vous sérialisez vers une chaîne à l'aide de la méthode `ToString`, le code XML résultant n'inclura pas de déclaration XML.</span><span class="sxs-lookup"><span data-stu-id="969b6-107">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="969b6-108">Sérialisation avec une déclaration XML</span><span class="sxs-lookup"><span data-stu-id="969b6-108">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="969b6-109">L'exemple suivant crée un objet <xref:System.Xml.Linq.XElement>, enregistre le document dans un fichier, puis imprime le fichier sur la console :</span><span class="sxs-lookup"><span data-stu-id="969b6-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```vb  
Dim root As XElement = <Root>  
                           <Child>child content</Child>  
                       </Root>  
root.Save("Root.xml")  
Dim str As String = File.ReadAllText("Root.xml")  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="969b6-110">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="969b6-110">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="969b6-111">Sérialisation sans déclaration XML</span><span class="sxs-lookup"><span data-stu-id="969b6-111">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="969b6-112">L'exemple suivant montre comment enregistrer un objet <xref:System.Xml.Linq.XElement> dans un objet <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="969b6-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
```vb  
Dim sb As StringBuilder = New StringBuilder()  
Dim xws As XmlWriterSettings = New XmlWriterSettings()  
xws.OmitXmlDeclaration = True  
  
Using xw As XmlWriter = XmlWriter.Create(sb, xws)  
    Dim root = <Root>  
                   <Child>child content</Child>  
               </Root>  
    root.Save(xw)  
End Using  
Console.WriteLine(sb.ToString())  
```  
  
 <span data-ttu-id="969b6-113">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="969b6-113">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="969b6-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="969b6-114">See Also</span></span>  
 [<span data-ttu-id="969b6-115">Sérialisation d’arborescences XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="969b6-115">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
