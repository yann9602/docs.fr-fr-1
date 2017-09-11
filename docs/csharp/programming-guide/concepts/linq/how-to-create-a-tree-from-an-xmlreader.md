---
title: "Guide pratique pour créer une arborescence à partir d’un XmlReader (C#)"
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
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
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
ms.openlocfilehash: 61685e93e6886b3101d6b30c7f8eb04d026ea55a
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a><span data-ttu-id="4b371-102">Guide pratique pour créer une arborescence à partir d’un XmlReader (C#)</span><span class="sxs-lookup"><span data-stu-id="4b371-102">How to: Create a Tree from an XmlReader (C#)</span></span>
<span data-ttu-id="4b371-103">Cette rubrique montre comment créer une arborescence XML directement à partir d'un objet <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="4b371-103">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="4b371-104">Pour créer un objet <xref:System.Xml.Linq.XElement> à partir d'un objet <xref:System.Xml.XmlReader>, vous devez placer l'objet <xref:System.Xml.XmlReader> sur un nœud d'élément.</span><span class="sxs-lookup"><span data-stu-id="4b371-104">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="4b371-105">L'objet <xref:System.Xml.XmlReader> ignorera les commentaires et les instructions de traitement, mais si l'objet <xref:System.Xml.XmlReader> est placé sur un nœud de texte, une erreur sera renvoyée.</span><span class="sxs-lookup"><span data-stu-id="4b371-105">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="4b371-106">Pour éviter de telles erreurs, placez toujours l'objet <xref:System.Xml.XmlReader> sur un élément avant de créer une arborescence XML à partir de l'objet <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="4b371-106">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b371-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="4b371-107">Example</span></span>  
 <span data-ttu-id="4b371-108">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Livres (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4b371-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="4b371-109">Le code suivant crée un objet `T:System.Xml.XmlReader`, puis il lit les nœuds jusqu'à trouver le premier nœud d'élément.</span><span class="sxs-lookup"><span data-stu-id="4b371-109">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="4b371-110">Il charge ensuite l'objet <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="4b371-110">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```csharp  
XmlReader r = XmlReader.Create("books.xml");  
while (r.NodeType != XmlNodeType.Element)  
    r.Read();  
XElement e = XElement.Load(r);  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="4b371-111">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="4b371-111">This example produces the following output:</span></span>  
  
```xml  
<Catalog>  
   <Book id="bk101">  
      <Author>Garghentini, Davide</Author>  
      <Title>XML Developer's Guide</Title>  
      <Genre>Computer</Genre>  
      <Price>44.95</Price>  
      <PublishDate>2000-10-01</PublishDate>  
      <Description>An in-depth look at creating applications   
      with XML.</Description>  
   </Book>  
   <Book id="bk102">  
      <Author>Garcia, Debra</Author>  
      <Title>Midnight Rain</Title>  
      <Genre>Fantasy</Genre>  
      <Price>5.95</Price>  
      <PublishDate>2000-12-16</PublishDate>  
      <Description>A former architect battles corporate zombies,   
      an evil sorceress, and her own childhood to become queen   
      of the world.</Description>  
   </Book>  
</Catalog>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4b371-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b371-112">See Also</span></span>  
 [<span data-ttu-id="4b371-113">Analyse de code XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4b371-113">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)

