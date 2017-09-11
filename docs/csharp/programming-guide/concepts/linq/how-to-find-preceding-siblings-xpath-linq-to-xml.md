---
title: "Guide pratique pour rechercher les frères précédents (XPath-LINQ to XML) (C#)"
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
ms.assetid: b281ff99-d08a-43d0-bea1-eff831b2f8ae
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c49dd8998b0ad1e2a579b44f07462fb1111f3094
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-find-preceding-siblings-xpath-linq-to-xml-c"></a><span data-ttu-id="8ce4c-102">Guide pratique pour rechercher les frères précédents (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8ce4c-102">How to: Find Preceding Siblings (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="8ce4c-103">Cette rubrique compare l’axe `preceding-sibling` XPath à l’axe <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName> enfant [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8ce4c-103">This topic compares the XPath `preceding-sibling` axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] child <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName> axis.</span></span>  
  
 <span data-ttu-id="8ce4c-104">L’expression XPath est la suivante :</span><span class="sxs-lookup"><span data-stu-id="8ce4c-104">The XPath expression is:</span></span>  
  
 `preceding-sibling::*`  
  
 <span data-ttu-id="8ce4c-105">Notez que les résultats de <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> et <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName> sont dans l'ordre du document.</span><span class="sxs-lookup"><span data-stu-id="8ce4c-105">Note that the results of both <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> and <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName> are in document order.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ce4c-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="8ce4c-106">Example</span></span>  
 <span data-ttu-id="8ce4c-107">L'exemple suivant recherche l'élément `FullAddress`, puis récupère les éléments précédents à l'aide de l'axe `preceding-sibling`.</span><span class="sxs-lookup"><span data-stu-id="8ce4c-107">The following example finds the `FullAddress` element, and then retrieves the previous elements using the `preceding-sibling` axis.</span></span>  
  
 <span data-ttu-id="8ce4c-108">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Clients et commandes (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="8ce4c-108">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
XElement co = XElement.Load("CustomersOrders.xml");  
  
XElement add = co.Element("Customers").Element("Customer").Element("FullAddress");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 = add.ElementsBeforeSelf();  
  
// XPath expression  
IEnumerable<XElement> list2 = add.XPathSelectElements("preceding-sibling::*");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list2)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="8ce4c-109">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="8ce4c-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
<CompanyName>Great Lakes Food Market</CompanyName>  
<ContactName>Howard Snyder</ContactName>  
<ContactTitle>Marketing Manager</ContactTitle>  
<Phone>(503) 555-7555</Phone>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8ce4c-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ce4c-110">See Also</span></span>  
 [<span data-ttu-id="8ce4c-111">LINQ to XML pour les utilisateurs XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="8ce4c-111">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)

