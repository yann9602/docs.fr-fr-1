---
title: "Guide pratique pour interroger LINQ to XML à l’aide de XPath (C#)"
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
ms.assetid: ee5af263-4ab1-45e5-b792-33a3221b426d
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6d7acf7519e6ab3384f2f34b8435fe96307921f0
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-query-linq-to-xml-using-xpath-c"></a><span data-ttu-id="73029-102">Guide pratique pour interroger LINQ to XML à l’aide de XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="73029-102">How to: Query LINQ to XML Using XPath (C#)</span></span>
<span data-ttu-id="73029-103">Cette rubrique présente les méthodes d’extension qui vous permettent d’interroger une arborescence XML à l’aide de XPath.</span><span class="sxs-lookup"><span data-stu-id="73029-103">This topic introduces the extension methods that enable you to query an XML tree by using XPath.</span></span> <span data-ttu-id="73029-104">Pour plus d'informations sur l'utilisation de ces méthodes d'extension, consultez <xref:System.Xml.XPath.Extensions?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="73029-104">For detailed information about using these extension methods, see <xref:System.Xml.XPath.Extensions?displayProperty=fullName>.</span></span>  
  
 <span data-ttu-id="73029-105">À moins que vous n’ayez une raison spécifique pour interroger à l’aide de XPath, par exemple en cas d’utilisation intensive de code hérité, l’utilisation de XPath avec LINQ to XML n’est pas recommandée.</span><span class="sxs-lookup"><span data-stu-id="73029-105">Unless you have a very specific reason for querying using XPath, such as extensive use of legacy code, using XPath with LINQ to XML is not recommended.</span></span> <span data-ttu-id="73029-106">Les requêtes XPath présentent des performances inférieures à celles des requêtes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="73029-106">XPath queries will not perform as well as [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73029-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="73029-107">Example</span></span>  
 <span data-ttu-id="73029-108">L'exemple suivant crée une petite arborescence XML et utilise <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> pour sélectionner un ensemble d'éléments.</span><span class="sxs-lookup"><span data-stu-id="73029-108">The following example creates a small XML tree and uses <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to select a set of elements.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", 1),  
    new XElement("Child1", 2),  
    new XElement("Child1", 3),  
    new XElement("Child2", 4),  
    new XElement("Child2", 5),  
    new XElement("Child2", 6)  
);  
IEnumerable<XElement> list = root.XPathSelectElements("./Child2");  
foreach (XElement el in list)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="73029-109">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="73029-109">This example produces the following output:</span></span>  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a><span data-ttu-id="73029-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73029-110">See Also</span></span>  
 [<span data-ttu-id="73029-111">Techniques de requêtes avancées (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="73029-111">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)

