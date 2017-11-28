---
title: Guide pratique pour effectuer des transformations de streaming au format XML (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 03c5ed5ef66db311ade751b5aad21de70b78f063
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a><span data-ttu-id="e27a0-102">Guide pratique pour effectuer des transformations de streaming au format XML (C#)</span><span class="sxs-lookup"><span data-stu-id="e27a0-102">How to: Perform Streaming Transformations of Text to XML (C#)</span></span>
<span data-ttu-id="e27a0-103">L'une des façons de traiter un fichier texte consiste à écrire une méthode d'extension qui diffuse en continu le fichier texte une ligne à la fois à l'aide de la construction `yield return`.</span><span class="sxs-lookup"><span data-stu-id="e27a0-103">One approach to processing a text file is to write an extension method that streams the text file a line at a time using the `yield return` construct.</span></span> <span data-ttu-id="e27a0-104">Vous pouvez alors écrire une requête LINQ qui traite le fichier texte de manière différée.</span><span class="sxs-lookup"><span data-stu-id="e27a0-104">You then can write a LINQ query that processes the text file in a lazy deferred fashion.</span></span> <span data-ttu-id="e27a0-105">Si vous utilisez ensuite <xref:System.Xml.Linq.XStreamingElement> pour diffuser la sortie en continu, vous pouvez créer une transformation du fichier texte en XML qui utilise une quantité minimale de mémoire, quelle que soit la taille du fichier texte source.</span><span class="sxs-lookup"><span data-stu-id="e27a0-105">If you then use <xref:System.Xml.Linq.XStreamingElement> to stream output, you then can create a transformation from the text file to XML that uses a minimal amount of memory, regardless of the size of the source text file.</span></span>  
  
 <span data-ttu-id="e27a0-106">Il existe certains points à noter concernant les transformations de diffusion en continu.</span><span class="sxs-lookup"><span data-stu-id="e27a0-106">There are some caveats regarding streaming transformations.</span></span> <span data-ttu-id="e27a0-107">Il est préférable d'appliquer une transformation de streaming dans les situations où vous pouvez traiter l'intégralité du fichier une seule fois et si vous pouvez traiter les lignes dans l'ordre dans lequel elles apparaissent dans le document source.</span><span class="sxs-lookup"><span data-stu-id="e27a0-107">A streaming transformation is best applied in situations where you can process the entire file once, and if you can process the lines in the order that they occur in the source document.</span></span> <span data-ttu-id="e27a0-108">Si vous devez traiter le fichier à plusieurs reprises, ou si vous devez trier les lignes avant de les traiter, vous perdez une grande partie des avantages offerts par l'utilisation d'une technique de streaming.</span><span class="sxs-lookup"><span data-stu-id="e27a0-108">If you have to process the file more than once, or if you have to sort the lines before you can process them, you will lose many of the benefits of using a streaming technique.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e27a0-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="e27a0-109">Example</span></span>  
 <span data-ttu-id="e27a0-110">Le fichier texte suivant, People.txt, est la source pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="e27a0-110">The following text file, People.txt, is the source for this example.</span></span>  
  
```  
#This is a comment  
1,Tai,Yee,Writer  
2,Nikolay,Grachev,Programmer  
3,David,Wright,Inventor  
```  
  
 <span data-ttu-id="e27a0-111">Le code suivant contient une méthode d'extension qui diffuse en continu les lignes du fichier texte de manière différée.</span><span class="sxs-lookup"><span data-stu-id="e27a0-111">The following code contains an extension method that streams the lines of the text file in a deferred fashion.</span></span>  
  
```csharp  
public static class StreamReaderSequence  
{  
    public static IEnumerable<string> Lines(this StreamReader source)  
    {  
        String line;  
  
        if (source == null)  
            throw new ArgumentNullException("source");  
        while ((line = source.ReadLine()) != null)  
        {  
            yield return line;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        StreamReader sr = new StreamReader("People.txt");  
        XStreamingElement xmlTree = new XStreamingElement("Root",  
            from line in sr.Lines()  
            let items = line.Split(',')  
            where !line.StartsWith("#")  
            select new XElement("Person",  
                       new XAttribute("ID", items[0]),  
                       new XElement("First", items[1]),  
                       new XElement("Last", items[2]),  
                       new XElement("Occupation", items[3])  
                   )  
        );  
        Console.WriteLine(xmlTree);  
        sr.Close();  
    }  
}  
```  
  
 <span data-ttu-id="e27a0-112">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="e27a0-112">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Person ID="1">  
    <First>Tai</First>  
    <Last>Yee</Last>  
    <Occupation>Writer</Occupation>  
  </Person>  
  <Person ID="2">  
    <First>Nikolay</First>  
    <Last>Grachev</Last>  
    <Occupation>Programmer</Occupation>  
  </Person>  
  <Person ID="3">  
    <First>David</First>  
    <Last>Wright</Last>  
    <Occupation>Inventor</Occupation>  
  </Person>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e27a0-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e27a0-113">See Also</span></span>  
 <xref:System.Xml.Linq.XStreamingElement>  
 [<span data-ttu-id="e27a0-114">Techniques de requêtes avancées (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e27a0-114">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
