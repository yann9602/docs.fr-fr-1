---
title: "Guide pratique pour déboguer des ensembles de résultats de requête vides (C#)"
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
ms.assetid: b569f0dc-425e-45a6-acbf-770fb761c981
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 78c6d612e11f50bedf8f1c2e9826775494faa465
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-debug-empty-query-results-sets-c"></a><span data-ttu-id="6f716-102">Guide pratique pour déboguer des ensembles de résultats de requête vides (C#)</span><span class="sxs-lookup"><span data-stu-id="6f716-102">How to: Debug Empty Query Results Sets (C#)</span></span>
<span data-ttu-id="6f716-103">L'un des problèmes les plus courants lors de l'interrogation d'une arborescence XML est que si celle-ci possède un espace de noms par défaut, le développeur écrit parfois la requête comme si le code XML n'était dans aucun espace de noms.</span><span class="sxs-lookup"><span data-stu-id="6f716-103">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="6f716-104">Le premier ensemble d'exemples dans cette rubrique illustre le chargement de code XML dans un espace de noms par défaut et son interrogation incorrecte.</span><span class="sxs-lookup"><span data-stu-id="6f716-104">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, and is queried improperly.</span></span>  
  
 <span data-ttu-id="6f716-105">Le deuxième ensemble d'exemples illustre les corrections que vous devez apporter pour pouvoir interroger du code XML dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="6f716-105">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
 <span data-ttu-id="6f716-106">Pour plus d’informations, consultez [Utilisation des espaces de noms XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="6f716-106">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f716-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="6f716-107">Example</span></span>  
 <span data-ttu-id="6f716-108">Cet exemple illustre la création de code XML dans un espace de noms et une requête qui retourne un jeu de résultats vide.</span><span class="sxs-lookup"><span data-stu-id="6f716-108">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements("Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
 <span data-ttu-id="6f716-109">Cet exemple génère le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="6f716-109">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="6f716-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="6f716-110">Example</span></span>  
 <span data-ttu-id="6f716-111">Cet exemple illustre la création de code XML dans un espace de noms et une requête codée correctement.</span><span class="sxs-lookup"><span data-stu-id="6f716-111">This example shows creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="6f716-112">La solution consiste à déclarer et à initialiser un objet <xref:System.Xml.Linq.XNamespace> et à l’utiliser lors de la spécification d’objets <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="6f716-112">The solution is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="6f716-113">Dans ce cas, l'argument de la méthode <xref:System.Xml.Linq.XElement.Elements%2A> est un objet <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="6f716-113">In this case, the argument to the <xref:System.Xml.Linq.XElement.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
 <span data-ttu-id="6f716-114">Cet exemple génère le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="6f716-114">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="6f716-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f716-115">See Also</span></span>  
 [<span data-ttu-id="6f716-116">Requêtes de base (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="6f716-116">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)

