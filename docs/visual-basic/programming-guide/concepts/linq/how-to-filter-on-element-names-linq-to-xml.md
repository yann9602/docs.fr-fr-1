---
title: "Comment : filtrer sur des noms d’élément (LINQ to XML) (Visual Basic) | Documents Microsoft"
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
ms.assetid: b1437b4a-48aa-4546-834a-d6d3ab015fe1
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 07f7867b0fc5cf79ba5ce06f95b07b5c538e83d3
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-filter-on-element-names-linq-to-xml-visual-basic"></a><span data-ttu-id="66b1f-102">Comment : filtrer sur des noms d’élément (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66b1f-102">How to: Filter on Element Names (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="66b1f-103">Lorsque vous appelez une des méthodes qui retournent des <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XElement>, vous pouvez filtrer sur le nom de l’élément.</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="66b1f-103">When you call one of the methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, you can filter on the element name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66b1f-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="66b1f-104">Example</span></span>  
 <span data-ttu-id="66b1f-105">Cet exemple récupère une collection des descendants filtrée de sorte à contenir uniquement les descendants avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="66b1f-105">This example retrieves a collection of descendants that is filtered to contain only descendants with the specified name.</span></span>  
  
 <span data-ttu-id="66b1f-106">Cet exemple utilise le document XML suivant : [exemple de fichier XML : commande fournisseur typique (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="66b1f-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
<span data-ttu-id="66b1f-107"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="66b1f-107"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="66b1f-108">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="66b1f-108">This code produces the following output:</span></span>  
  
<span data-ttu-id="66b1f-109"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="66b1f-109"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="66b1f-110">Les autres méthodes qui retournent <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XElement>collections suivent le même modèle.</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="66b1f-110">The other methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> collections follow the same pattern.</span></span> <span data-ttu-id="66b1f-111">Leurs signatures sont semblables aux <xref:System.Xml.Linq.XContainer.Elements%2A>et <xref:System.Xml.Linq.XContainer.Descendants%2A>.</xref:System.Xml.Linq.XContainer.Descendants%2A> </xref:System.Xml.Linq.XContainer.Elements%2A></span><span class="sxs-lookup"><span data-stu-id="66b1f-111">Their signatures are similar to <xref:System.Xml.Linq.XContainer.Elements%2A> and <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span></span> <span data-ttu-id="66b1f-112">Voici la liste complète des méthodes qui ont des signatures de méthodes semblables :</span><span class="sxs-lookup"><span data-stu-id="66b1f-112">The following is the complete list of methods that have similar method signatures:</span></span>  
  
-   <span data-ttu-id="66b1f-113"><xref:System.Xml.Linq.XNode.Ancestors%2A></xref:System.Xml.Linq.XNode.Ancestors%2A></span><span class="sxs-lookup"><span data-stu-id="66b1f-113"><xref:System.Xml.Linq.XNode.Ancestors%2A></span></span>  
  
-   <span data-ttu-id="66b1f-114"><xref:System.Xml.Linq.XContainer.Descendants%2A></xref:System.Xml.Linq.XContainer.Descendants%2A></span><span class="sxs-lookup"><span data-stu-id="66b1f-114"><xref:System.Xml.Linq.XContainer.Descendants%2A></span></span>  
  
-   <span data-ttu-id="66b1f-115"><xref:System.Xml.Linq.XContainer.Elements%2A></xref:System.Xml.Linq.XContainer.Elements%2A></span><span class="sxs-lookup"><span data-stu-id="66b1f-115"><xref:System.Xml.Linq.XContainer.Elements%2A></span></span>  
  
-   <span data-ttu-id="66b1f-116"><xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A></xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A></span><span class="sxs-lookup"><span data-stu-id="66b1f-116"><xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A></span></span>  
  
-   <span data-ttu-id="66b1f-117"><xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A></xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A></span><span class="sxs-lookup"><span data-stu-id="66b1f-117"><xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A></span></span>  
  
-   <span data-ttu-id="66b1f-118"><xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A></xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A></span><span class="sxs-lookup"><span data-stu-id="66b1f-118"><xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A></span></span>  
  
-   <span data-ttu-id="66b1f-119"><xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A></xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A></span><span class="sxs-lookup"><span data-stu-id="66b1f-119"><xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A></span></span>  
  
## <a name="example"></a><span data-ttu-id="66b1f-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="66b1f-120">Example</span></span>  
 <span data-ttu-id="66b1f-121">L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="66b1f-121">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="66b1f-122">Pour plus d’informations, consultez [utilisation des espaces de noms XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="66b1f-122">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="66b1f-123">Cet exemple utilise le document XML suivant : [exemple de fichier XML : commande fournisseur typique dans un Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="66b1f-123">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")  
        Dim items As IEnumerable(Of XElement) = _  
            From el In po...<aw:ProductName> _  
            Select el  
        For Each prdName As XElement In items  
            Console.WriteLine(prdName.Name.ToString & ":" & prdName.Value)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="66b1f-124">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="66b1f-124">This code produces the following output:</span></span>  
  
```  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a><span data-ttu-id="66b1f-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="66b1f-125">See Also</span></span>  
 [<span data-ttu-id="66b1f-126">Axes LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66b1f-126">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
