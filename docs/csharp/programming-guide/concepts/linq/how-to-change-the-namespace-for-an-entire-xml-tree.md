---
title: "Guide pratique pour modifier l’espace de noms pour toute une arborescence XML (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 1584ff3b-c77d-4241-ab62-80adfb7bfc1b
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 80e3e4d7d352cb479eda66fb6eca1a76748511b8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-change-the-namespace-for-an-entire-xml-tree-c"></a><span data-ttu-id="eb55d-102">Guide pratique pour modifier l’espace de noms pour toute une arborescence XML (C#)</span><span class="sxs-lookup"><span data-stu-id="eb55d-102">How to: Change the Namespace for an Entire XML Tree (C#)</span></span>
<span data-ttu-id="eb55d-103">Vous devez parfois modifier par programmation l’espace de noms pour un élément ou un attribut.</span><span class="sxs-lookup"><span data-stu-id="eb55d-103">You sometimes have to programmatically change the namespace for an element or an attribute.</span></span> <span data-ttu-id="eb55d-104">LINQ to XML rend cette tâche très simple.</span><span class="sxs-lookup"><span data-stu-id="eb55d-104">LINQ to XML makes this easy.</span></span> <span data-ttu-id="eb55d-105">La propriété <xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType> peut être définie.</span><span class="sxs-lookup"><span data-stu-id="eb55d-105">The <xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType> property can be set.</span></span> <span data-ttu-id="eb55d-106">La propriété <xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType> ne peut pas être définie, mais vous pouvez facilement copier les attributs dans un objet <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>, supprimer les attributs existants, puis ajouter de nouveaux attributs qui sont dans le nouvel espace de noms souhaité.</span><span class="sxs-lookup"><span data-stu-id="eb55d-106">The <xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType> property cannot be set, but you can easily copy the attributes into a <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>, remove the existing attributes, and then add new attributes that are in the new desired namespace.</span></span>  
  
 <span data-ttu-id="eb55d-107">Pour plus d’informations, consultez [Utilisation des espaces de noms XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="eb55d-107">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb55d-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="eb55d-108">Example</span></span>  
 <span data-ttu-id="eb55d-109">Le code suivant crée deux arborescences XML qui ne sont dans aucun espace de noms.</span><span class="sxs-lookup"><span data-stu-id="eb55d-109">The following code creates two XML trees in no namespace.</span></span> <span data-ttu-id="eb55d-110">Il modifie ensuite l'espace de noms des deux arborescences et les combine en une seule arborescence.</span><span class="sxs-lookup"><span data-stu-id="eb55d-110">It then changes the namespace of each of the trees, and combines them into a single tree.</span></span>  
  
```csharp  
XElement tree1 = new XElement("Data",  
    new XElement("Child", "content",  
        new XAttribute("MyAttr", "content")  
    )  
);  
XElement tree2 = new XElement("Data",  
    new XElement("Child", "content",  
        new XAttribute("MyAttr", "content")  
    )  
);  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace ad = "http://www.adatum.com";  
// change the namespace of every element and attribute in the first tree  
foreach (XElement el in tree1.DescendantsAndSelf())  
{  
    el.Name = aw.GetName(el.Name.LocalName);  
    List<XAttribute> atList = el.Attributes().ToList();  
    el.Attributes().Remove();  
    foreach (XAttribute at in atList)  
        el.Add(new XAttribute(aw.GetName(at.Name.LocalName), at.Value));  
}  
// change the namespace of every element and attribute in the second tree  
foreach (XElement el in tree2.DescendantsAndSelf())  
{  
    el.Name = ad.GetName(el.Name.LocalName);  
    List<XAttribute> atList = el.Attributes().ToList();  
    el.Attributes().Remove();  
    foreach (XAttribute at in atList)  
        el.Add(new XAttribute(ad.GetName(at.Name.LocalName), at.Value));  
}  
// add attribute namespaces so that the tree will be serialized with  
// the aw and ad namespace prefixes  
tree1.Add(  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com")  
);  
tree2.Add(  
    new XAttribute(XNamespace.Xmlns + "ad", "http://www.adatum.com")  
);  
// create a new composite tree  
XElement root = new XElement("Root",  
    tree1,  
    tree2  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="eb55d-111">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="eb55d-111">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <aw:Data xmlns:aw="http://www.adventure-works.com">  
    <aw:Child aw:MyAttr="content">content</aw:Child>  
  </aw:Data>  
  <ad:Data xmlns:ad="http://www.adatum.com">  
    <ad:Child ad:MyAttr="content">content</ad:Child>  
  </ad:Data>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="eb55d-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb55d-112">See Also</span></span>  
 [<span data-ttu-id="eb55d-113">Modification d’arborescences XML (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="eb55d-113">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
