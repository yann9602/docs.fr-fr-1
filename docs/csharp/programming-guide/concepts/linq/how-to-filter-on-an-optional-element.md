---
title: "Guide pratique pour filtrer sur un élément facultatif (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: f99e2f93-fca5-403f-8a0c-770761d4905a
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dc1b5384add88db209a71ec56dc1c5edf4caecb3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-filter-on-an-optional-element-c"></a><span data-ttu-id="1ac13-102">Guide pratique pour filtrer sur un élément facultatif (C#)</span><span class="sxs-lookup"><span data-stu-id="1ac13-102">How to: Filter on an Optional Element (C#)</span></span>
<span data-ttu-id="1ac13-103">Parfois, vous souhaitez appliquer un filtrage sur un élément sans être certain qu'il existe dans votre document XML.</span><span class="sxs-lookup"><span data-stu-id="1ac13-103">Sometimes you want to filter for an element even though you are not sure it exists in your XML document.</span></span> <span data-ttu-id="1ac13-104">La recherche doit être exécutée de telle sorte que, si l'élément particulier ne possède pas l'élément enfant, aucune exception de référence Null ne soit déclenchée suite au filtrage.</span><span class="sxs-lookup"><span data-stu-id="1ac13-104">The search should be executed so that if the particular element does not have the child element, you do not trigger a null reference exception by filtering for it.</span></span> <span data-ttu-id="1ac13-105">Dans l'exemple suivant, l'élément `Child5` ne possède pas d'élément enfant `Type`, mais la requête s'exécute tout de même correctement.</span><span class="sxs-lookup"><span data-stu-id="1ac13-105">In the following example, the `Child5` element does not have a `Type` child element, but the query still executes correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ac13-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="1ac13-106">Example</span></span>  
 <span data-ttu-id="1ac13-107">Cet exemple utilise la méthode d'extension <xref:System.Xml.Linq.Extensions.Elements%2A>.</span><span class="sxs-lookup"><span data-stu-id="1ac13-107">This example uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method.</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<Root>  
  <Child1>  
    <Text>Child One Text</Text>  
    <Type Value=""Yes""/>  
  </Child1>  
  <Child2>  
    <Text>Child Two Text</Text>  
    <Type Value=""Yes""/>  
  </Child2>  
  <Child3>  
    <Text>Child Three Text</Text>  
    <Type Value=""No""/>  
  </Child3>  
  <Child4>  
    <Text>Child Four Text</Text>  
    <Type Value=""Yes""/>  
  </Child4>  
  <Child5>  
    <Text>Child Five Text</Text>  
  </Child5>  
</Root>");  
var cList =  
    from typeElement in root.Elements().Elements("Type")  
    where (string)typeElement.Attribute("Value") == "Yes"  
    select (string)typeElement.Parent.Element("Text");  
foreach(string str in cList)  
    Console.WriteLine(str);  
```  
  
 <span data-ttu-id="1ac13-108">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="1ac13-108">This code produces the following output:</span></span>  
  
```  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="example"></a><span data-ttu-id="1ac13-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="1ac13-109">Example</span></span>  
 <span data-ttu-id="1ac13-110">L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="1ac13-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="1ac13-111">Pour plus d’informations, consultez [Utilisation des espaces de noms XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="1ac13-111">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>  
  <Child1>  
    <Text>Child One Text</Text>  
    <Type Value=""Yes""/>  
  </Child1>  
  <Child2>  
    <Text>Child Two Text</Text>  
    <Type Value=""Yes""/>  
  </Child2>  
  <Child3>  
    <Text>Child Three Text</Text>  
    <Type Value=""No""/>  
  </Child3>  
  <Child4>  
    <Text>Child Four Text</Text>  
    <Type Value=""Yes""/>  
  </Child4>  
  <Child5>  
    <Text>Child Five Text</Text>  
  </Child5>  
</Root>");  
XNamespace ad = "http://www.adatum.com";  
var cList =  
    from typeElement in root.Elements().Elements(ad + "Type")  
    where (string)typeElement.Attribute("Value") == "Yes"  
    select (string)typeElement.Parent.Element(ad + "Text");  
foreach (string str in cList)  
    Console.WriteLine(str);  
```  
  
 <span data-ttu-id="1ac13-112">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="1ac13-112">This code produces the following output:</span></span>  
  
```  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ac13-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ac13-113">See Also</span></span>  
 <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="1ac13-114">Requêtes de base (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="1ac13-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)  
 [<span data-ttu-id="1ac13-115">Présentation des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="1ac13-115">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="1ac13-116">Opérations de projection (C#)</span><span class="sxs-lookup"><span data-stu-id="1ac13-116">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)
