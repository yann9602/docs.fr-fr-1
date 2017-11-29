---
title: "Comment : créer une arborescence à partir d’un XmlReader (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6de683d8-177d-402b-b0de-d0539f1ce5d8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4ceae7c2bee85e7b368322c8ba195dea9feff672
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-tree-from-an-xmlreader-visual-basic"></a><span data-ttu-id="5aa6f-102">Comment : créer une arborescence à partir d’un XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5aa6f-102">How to: Create a Tree from an XmlReader (Visual Basic)</span></span>
<span data-ttu-id="5aa6f-103">Cette rubrique montre comment créer une arborescence XML directement à partir d'un objet <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="5aa6f-103">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="5aa6f-104">Pour créer un objet <xref:System.Xml.Linq.XElement> à partir d'un objet <xref:System.Xml.XmlReader>, vous devez placer l'objet <xref:System.Xml.XmlReader> sur un nœud d'élément.</span><span class="sxs-lookup"><span data-stu-id="5aa6f-104">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="5aa6f-105">L'objet <xref:System.Xml.XmlReader> ignorera les commentaires et les instructions de traitement, mais si l'objet <xref:System.Xml.XmlReader> est placé sur un nœud de texte, une erreur sera renvoyée.</span><span class="sxs-lookup"><span data-stu-id="5aa6f-105">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="5aa6f-106">Pour éviter de telles erreurs, placez toujours l'objet <xref:System.Xml.XmlReader> sur un élément avant de créer une arborescence XML à partir de l'objet <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="5aa6f-106">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5aa6f-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="5aa6f-107">Example</span></span>  
 <span data-ttu-id="5aa6f-108">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Livres (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="5aa6f-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="5aa6f-109">Le code suivant crée un objet `T:System.Xml.XmlReader`, puis il lit les nœuds jusqu'à trouver le premier nœud d'élément.</span><span class="sxs-lookup"><span data-stu-id="5aa6f-109">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="5aa6f-110">Il charge ensuite l'objet <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="5aa6f-110">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```vb  
Dim r As XmlReader = XmlReader.Create("books.xml")  
Do While r.NodeType <> XmlNodeType.Element  
    r.Read()  
Loop  
Dim e As XElement = XElement.Load(r)  
Console.WriteLine(e)  
```  
  
 <span data-ttu-id="5aa6f-111">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="5aa6f-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5aa6f-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5aa6f-112">See Also</span></span>  
 [<span data-ttu-id="5aa6f-113">L’analyse XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5aa6f-113">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
