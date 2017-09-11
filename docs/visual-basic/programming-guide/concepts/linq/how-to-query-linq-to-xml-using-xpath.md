---
title: "Comment : interroger LINQ to XML à l’aide de XPath (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: e1f69a20-1efa-452d-9089-c472fa84b3d5
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 586182367ea26539384ea630dde301fe447915b8
ms.contentlocale: fr-fr
ms.lasthandoff: 05/23/2017


---
# <a name="how-to-query-linq-to-xml-using-xpath-visual-basic"></a><span data-ttu-id="c05b2-102">Comment : interroger LINQ to XML à l’aide de XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c05b2-102">How to: Query LINQ to XML Using XPath (Visual Basic)</span></span>
<span data-ttu-id="c05b2-103">Cette rubrique présente les méthodes d’extension qui vous permettent d’interroger une arborescence XML à l’aide de XPath.</span><span class="sxs-lookup"><span data-stu-id="c05b2-103">This topic introduces the extension methods that enable you to query an XML tree by using XPath.</span></span> <span data-ttu-id="c05b2-104">Pour plus d’informations sur l’utilisation de ces méthodes d’extension, consultez <xref:System.Xml.XPath.Extensions?displayProperty=fullName>.</xref:System.Xml.XPath.Extensions?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="c05b2-104">For detailed information about using these extension methods, see <xref:System.Xml.XPath.Extensions?displayProperty=fullName>.</span></span>  
  
 <span data-ttu-id="c05b2-105">À moins que vous n’ayez une raison spécifique pour interroger à l’aide de XPath, par exemple en cas d’utilisation intensive de code hérité, l’utilisation de XPath avec LINQ to XML n’est pas recommandée.</span><span class="sxs-lookup"><span data-stu-id="c05b2-105">Unless you have a very specific reason for querying using XPath, such as extensive use of legacy code, using XPath with LINQ to XML is not recommended.</span></span> <span data-ttu-id="c05b2-106">Requêtes XPath n’effectuera pas ainsi que [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] requêtes.</span><span class="sxs-lookup"><span data-stu-id="c05b2-106">XPath queries will not perform as well as [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c05b2-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="c05b2-107">Example</span></span>  
 <span data-ttu-id="c05b2-108">L’exemple suivant crée une petite arborescence XML et utilise <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A>pour sélectionner un ensemble d’éléments.</xref:System.Xml.XPath.Extensions.XPathSelectElements%2A></span><span class="sxs-lookup"><span data-stu-id="c05b2-108">The following example creates a small XML tree and uses <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to select a set of elements.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>1</Child1>  
        <Child1>2</Child1>  
        <Child1>3</Child1>  
        <Child2>4</Child2>  
        <Child2>5</Child2>  
        <Child2>6</Child2>  
    </Root>  
  
Dim list As IEnumerable(Of XElement) = root.XPathSelectElements("./Child2")  
For Each el As XElement In list  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="c05b2-109">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="c05b2-109">This example produces the following output:</span></span>  
  
```  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c05b2-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c05b2-110">See Also</span></span>  
 [<span data-ttu-id="c05b2-111">Techniques de requêtes (LINQ to XML) avancées (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c05b2-111">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)

