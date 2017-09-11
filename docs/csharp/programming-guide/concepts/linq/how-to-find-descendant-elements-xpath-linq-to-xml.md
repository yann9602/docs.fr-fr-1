---
title: "Guide pratique pour rechercher des éléments descendants (XPath-LINQ to XML) (C#)"
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
ms.assetid: b318da39-bb8b-4c56-a019-e13b12b01831
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 27b9b08fea2cfed476f4caf10b65b2b7e5eb74c5
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-find-descendant-elements-xpath-linq-to-xml-c"></a><span data-ttu-id="8c29f-102">Guide pratique pour rechercher des éléments descendants (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8c29f-102">How to: Find Descendant Elements (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="8c29f-103">Cette rubrique montre comment obtenir les éléments descendants avec un nom particulier.</span><span class="sxs-lookup"><span data-stu-id="8c29f-103">This topic shows how to get the descendant elements with a particular name.</span></span>  
  
 <span data-ttu-id="8c29f-104">L'expression XPath est `//Name`.</span><span class="sxs-lookup"><span data-stu-id="8c29f-104">The XPath expression is `//Name`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c29f-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="8c29f-105">Example</span></span>  
 <span data-ttu-id="8c29f-106">Cet exemple recherche tous les descendants nommés `Name`.</span><span class="sxs-lookup"><span data-stu-id="8c29f-106">This example finds all descendants named `Name`.</span></span>  
  
 <span data-ttu-id="8c29f-107">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Plusieurs commandes fournisseur (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8c29f-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 = po.Root.Descendants("Name");  
  
// XPath expression  
IEnumerable<XElement> list2 = po.XPathSelectElements("//Name");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="8c29f-108">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="8c29f-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8c29f-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c29f-109">See Also</span></span>  
 [<span data-ttu-id="8c29f-110">LINQ to XML pour les utilisateurs XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="8c29f-110">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)

