---
title: "Guide pratique pour charger du code XML à partir d’un fichier (C#)"
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
ms.assetid: 3ed38487-8028-4209-9872-c8dce0ed4dfe
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
ms.openlocfilehash: 683c87608ecc9dea71c55a4b3c426ad3fd9f36fe
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-load-xml-from-a-file-c"></a><span data-ttu-id="2f776-102">Guide pratique pour charger du code XML à partir d’un fichier (C#)</span><span class="sxs-lookup"><span data-stu-id="2f776-102">How to: Load XML from a File (C#)</span></span>
<span data-ttu-id="2f776-103">Cette rubrique montre comment charger des données XML à partir d'un URI en utilisant la méthode <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="2f776-103">This topic shows how to load XML from a URI by using the <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f776-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="2f776-104">Example</span></span>  
 <span data-ttu-id="2f776-105">L'exemple suivant montre comment charger un document XML à partir d'un fichier.</span><span class="sxs-lookup"><span data-stu-id="2f776-105">The following example shows how to load an XML document from a file.</span></span> <span data-ttu-id="2f776-106">L’exemple suivant charge books.xml et affiche l’arborescence XML sur la console.</span><span class="sxs-lookup"><span data-stu-id="2f776-106">The following example loads books.xml and outputs the XML tree to the console.</span></span>  
  
 <span data-ttu-id="2f776-107">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Livres (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2f776-107">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```csharp  
XElement booksFromFile = XElement.Load(@"books.xml");  
Console.WriteLine(booksFromFile);  
```  
  
 <span data-ttu-id="2f776-108">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="2f776-108">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2f776-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f776-109">See Also</span></span>  
 [<span data-ttu-id="2f776-110">Analyse de code XML (C#)</span><span class="sxs-lookup"><span data-stu-id="2f776-110">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)

