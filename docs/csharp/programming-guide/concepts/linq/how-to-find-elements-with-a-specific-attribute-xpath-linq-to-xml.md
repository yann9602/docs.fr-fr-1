---
title: "Guide pratique pour rechercher des éléments avec un attribut spécifique (XPath-LINQ to XML) (C#)"
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
ms.assetid: daed00dd-923a-43be-8a90-eee406f6f574
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: fec0b9a4dc5cee0f10f1675f1b8b281c40be7f21
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-find-elements-with-a-specific-attribute-xpath-linq-to-xml-c"></a><span data-ttu-id="f2b4b-102">Guide pratique pour rechercher des éléments avec un attribut spécifique (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f2b4b-102">How to: Find Elements with a Specific Attribute (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="f2b4b-103">Parfois, vous souhaitez rechercher tous les éléments qui ont un attribut spécifique.</span><span class="sxs-lookup"><span data-stu-id="f2b4b-103">Sometimes you want to find all elements that have a specific attribute.</span></span> <span data-ttu-id="f2b4b-104">Vous ne vous souciez pas du contenu de l'attribut.</span><span class="sxs-lookup"><span data-stu-id="f2b4b-104">You are not concerned about the contents of the attribute.</span></span> <span data-ttu-id="f2b4b-105">Au lieu de cela, vous souhaitez sélectionner les éléments en fonction de l'existence de l'attribut.</span><span class="sxs-lookup"><span data-stu-id="f2b4b-105">Instead, you want to select based on the existence of the attribute.</span></span>  
  
 <span data-ttu-id="f2b4b-106">L’expression XPath est la suivante :</span><span class="sxs-lookup"><span data-stu-id="f2b4b-106">The XPath expression is:</span></span>  
  
 `./*[@Select]`  
  
## <a name="example"></a><span data-ttu-id="f2b4b-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="f2b4b-107">Example</span></span>  
 <span data-ttu-id="f2b4b-108">Le code suivant sélectionne simplement les éléments qui ont l'attribut `Select`.</span><span class="sxs-lookup"><span data-stu-id="f2b4b-108">The following code selects just the elements that have the `Select` attribute.</span></span>  
  
```csharp  
XElement doc = XElement.Parse(  
@"<Root>  
    <Child1>1</Child1>  
    <Child2 Select='true'>2</Child2>  
    <Child3>3</Child3>  
    <Child4 Select='true'>4</Child4>  
    <Child5>5</Child5>  
</Root>");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    from el in doc.Elements()  
    where el.Attribute("Select") != null  
    select el;  
  
// XPath expression  
IEnumerable<XElement> list2 =  
    ((IEnumerable)doc.XPathEvaluate("./*[@Select]")).Cast<XElement>();  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="f2b4b-109">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="f2b4b-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Child2 Select="true">2</Child2>  
<Child4 Select="true">4</Child4>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f2b4b-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2b4b-110">See Also</span></span>  
 [<span data-ttu-id="f2b4b-111">LINQ to XML pour les utilisateurs XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="f2b4b-111">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)

