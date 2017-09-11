---
title: "Suppression d’éléments, attributs et nœuds d’une arborescence XML (Visual Basic) | Documents Microsoft"
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
ms.assetid: 5cf21919-4360-4b49-b29d-58ea3164ac72
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 8842858080ce1f27d997e6af61a8dd2301cdc2bc
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017


---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-visual-basic"></a><span data-ttu-id="fb4b4-102">Suppression d’éléments, attributs et nœuds d’une arborescence XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb4b4-102">Removing Elements, Attributes, and Nodes from an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="fb4b4-103">Vous pouvez modifier une arborescence XML en supprimant des éléments, des attributs et d’autres types de nœuds.</span><span class="sxs-lookup"><span data-stu-id="fb4b4-103">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>  
  
 <span data-ttu-id="fb4b4-104">La suppression d'un seul élément ou attribut d'un document XML est simple.</span><span class="sxs-lookup"><span data-stu-id="fb4b4-104">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="fb4b4-105">Toutefois, lors de la suppression de collections d’éléments ou d’attributs, vous devez tout d’abord matérialiser une collection dans une liste, puis supprimer les éléments ou attributs de la liste.</span><span class="sxs-lookup"><span data-stu-id="fb4b4-105">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="fb4b4-106">La meilleure approche consiste à utiliser le <xref:System.Xml.Linq.Extensions.Remove%2A>méthode d’extension, qui effectuera cette tâche pour vous.</xref:System.Xml.Linq.Extensions.Remove%2A></span><span class="sxs-lookup"><span data-stu-id="fb4b4-106">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method, which will do this for you.</span></span>  
  
 <span data-ttu-id="fb4b4-107">Cette opération est nécessaire car la plupart des collections que vous récupérez à partir d’une arborescence XML sont produites à l’aide de l’exécution différée.</span><span class="sxs-lookup"><span data-stu-id="fb4b4-107">The main reason for doing this is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="fb4b4-108">Si vous ne les matérialisez pas tout d’abord dans une liste, ou si vous n’utilisez pas les méthodes d’extension, vous risquez de rencontrer une certaine classe de bogues.</span><span class="sxs-lookup"><span data-stu-id="fb4b4-108">If you do not first materialize them into a list, or if you do not use the extension methods, it is possible to encounter a certain class of bugs.</span></span> <span data-ttu-id="fb4b4-109">Pour plus d’informations, consultez [Mixed Declarative Code/impératif Code Bugs (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="fb4b4-109">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="fb4b4-110">Les méthodes suivantes suppriment des nœuds et des attributs d’une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="fb4b4-110">The following methods remove nodes and attributes from an XML tree.</span></span>  
  
|<span data-ttu-id="fb4b4-111">Méthode</span><span class="sxs-lookup"><span data-stu-id="fb4b4-111">Method</span></span>|<span data-ttu-id="fb4b4-112">Description</span><span class="sxs-lookup"><span data-stu-id="fb4b4-112">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="fb4b4-113">[XAttribute.Remove](https://msdn.microsoft.com/library/system.xml.linq.xattribute.remove\(v=vs.110\).aspx)</span><span class="sxs-lookup"><span data-stu-id="fb4b4-113">[XAttribute.Remove](https://msdn.microsoft.com/library/system.xml.linq.xattribute.remove\(v=vs.110\).aspx)</span></span>|<span data-ttu-id="fb4b4-114">Supprime un <xref:System.Xml.Linq.XAttribute>de son parent.</xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="fb4b4-114">Removes an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|  
|<span data-ttu-id="fb4b4-115">[XContainer.RemoveNodes](https://msdn.microsoft.com/library/system.xml.linq.xcontainer.removenodes\(v=vs.110\).aspx)</span><span class="sxs-lookup"><span data-stu-id="fb4b4-115">[XContainer.RemoveNodes](https://msdn.microsoft.com/library/system.xml.linq.xcontainer.removenodes\(v=vs.110\).aspx)</span></span>|<span data-ttu-id="fb4b4-116">Supprime les nœuds enfants d’un <xref:System.Xml.Linq.XContainer>.</xref:System.Xml.Linq.XContainer></span><span class="sxs-lookup"><span data-stu-id="fb4b4-116">Removes the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<span data-ttu-id="fb4b4-117"><xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="fb4b4-117"><xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=fullName></span></span>|<span data-ttu-id="fb4b4-118">Supprime le contenu et les attributs à partir d’un <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="fb4b4-118">Removes content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<span data-ttu-id="fb4b4-119"><xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="fb4b4-119"><xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=fullName></span></span>|<span data-ttu-id="fb4b4-120">Supprime les attributs d’un <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="fb4b4-120">Removes the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<span data-ttu-id="fb4b4-121"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="fb4b4-121"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=fullName></span></span>|<span data-ttu-id="fb4b4-122">Supprime l'attribut si vous passez `null` comme valeur.</span><span class="sxs-lookup"><span data-stu-id="fb4b4-122">If you pass `null` for value, then removes the attribute.</span></span>|  
|<span data-ttu-id="fb4b4-123"><xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="fb4b4-123"><xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=fullName></span></span>|<span data-ttu-id="fb4b4-124">Supprime l'élément enfant si vous passez `null` comme valeur.</span><span class="sxs-lookup"><span data-stu-id="fb4b4-124">If you pass `null` for value, then removes the child element.</span></span>|  
|<span data-ttu-id="fb4b4-125"><xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="fb4b4-125"><xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=fullName></span></span>|<span data-ttu-id="fb4b4-126">Supprime un <xref:System.Xml.Linq.XNode>de son parent.</xref:System.Xml.Linq.XNode></span><span class="sxs-lookup"><span data-stu-id="fb4b4-126">Removes an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|  
|<span data-ttu-id="fb4b4-127"><xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=fullName></xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="fb4b4-127"><xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=fullName></span></span>|<span data-ttu-id="fb4b4-128">Supprime chaque attribut ou élément dans la collection source de son élément parent.</span><span class="sxs-lookup"><span data-stu-id="fb4b4-128">Removes every attribute or element in the source collection from its parent element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fb4b4-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="fb4b4-129">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="fb4b4-130">Description</span><span class="sxs-lookup"><span data-stu-id="fb4b4-130">Description</span></span>  
 <span data-ttu-id="fb4b4-131">Cet exemple illustre trois approches de la suppression d'éléments.</span><span class="sxs-lookup"><span data-stu-id="fb4b4-131">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="fb4b4-132">Tout d'abord, il supprime un seul élément.</span><span class="sxs-lookup"><span data-stu-id="fb4b4-132">First, it removes a single element.</span></span> <span data-ttu-id="fb4b4-133">Ensuite, il récupère une collection d’éléments, les matérialise à l’aide de la <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>(opérateur), puis supprime la collection.</xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="fb4b4-133">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName> operator, and removes the collection.</span></span> <span data-ttu-id="fb4b4-134">Enfin, il récupère une collection d’éléments et les supprime à l’aide de la <xref:System.Xml.Linq.Extensions.Remove%2A>méthode d’extension.</xref:System.Xml.Linq.Extensions.Remove%2A></span><span class="sxs-lookup"><span data-stu-id="fb4b4-134">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>  
  
 <span data-ttu-id="fb4b4-135">Pour plus d’informations sur la <xref:System.Linq.Enumerable.ToList%2A>opérateur, voir [conversion des Types de données (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).</xref:System.Linq.Enumerable.ToList%2A></span><span class="sxs-lookup"><span data-stu-id="fb4b4-135">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).</span></span>  
  
### <a name="code"></a><span data-ttu-id="fb4b4-136">Code</span><span class="sxs-lookup"><span data-stu-id="fb4b4-136">Code</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>  
            <GrandChild1/>  
            <GrandChild2/>  
            <GrandChild3/>  
        </Child1>  
        <Child2>  
            <GrandChild4/>  
            <GrandChild5/>  
            <GrandChild6/>  
        </Child2>  
        <Child3>  
            <GrandChild7/>  
            <GrandChild8/>  
            <GrandChild9/>  
        </Child3>  
    </Root>  
root.<Child1>.<GrandChild1>.Remove()  
root.<Child2>.Elements().ToList().Remove()  
root.<Child3>.Elements().Remove()  
Console.WriteLine(root)  
  
```  
  
### <a name="comments"></a><span data-ttu-id="fb4b4-137">Commentaires</span><span class="sxs-lookup"><span data-stu-id="fb4b4-137">Comments</span></span>  
 <span data-ttu-id="fb4b4-138">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="fb4b4-138">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>  
    <GrandChild2 />  
    <GrandChild3 />  
  </Child1>  
  <Child2 />  
  <Child3 />  
</Root>  
```  
  
 <span data-ttu-id="fb4b4-139">Notez que le premier élément petit-enfant a été supprimé de `Child1`.</span><span class="sxs-lookup"><span data-stu-id="fb4b4-139">Notice that the first grandchild element has been removed from `Child1`.</span></span> <span data-ttu-id="fb4b4-140">Tous les éléments petits-enfants ont été supprimés de `Child2` et de `Child3`.</span><span class="sxs-lookup"><span data-stu-id="fb4b4-140">All grandchildren elements have been removed from `Child2` and from `Child3`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb4b4-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fb4b4-141">See Also</span></span>  
 [<span data-ttu-id="fb4b4-142">Modification d’arborescences XML (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb4b4-142">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
