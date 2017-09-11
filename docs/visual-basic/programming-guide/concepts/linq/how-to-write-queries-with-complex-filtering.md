---
title: "Comment : écrire des requêtes avec un filtrage complexe (Visual Basic) | Documents Microsoft"
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
ms.assetid: bf286ffc-7990-4b00-a4eb-ee3d70129950
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 3f8f6dfc78fb94dcb719ca68841dba54fe92ec75
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017


---
# <a name="how-to-write-queries-with-complex-filtering-visual-basic"></a><span data-ttu-id="88ad0-102">Comment : écrire des requêtes avec un filtrage complexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88ad0-102">How to: Write Queries with Complex Filtering (Visual Basic)</span></span>
<span data-ttu-id="88ad0-103">Il peut arriver que vous souhaitiez écrire des requêtes LINQ to XML à l'aide de filtres complexes.</span><span class="sxs-lookup"><span data-stu-id="88ad0-103">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="88ad0-104">Par exemple, il se peut que vous deviez rechercher tous les éléments qui ont un élément enfant avec un nom et une valeur spécifiques.</span><span class="sxs-lookup"><span data-stu-id="88ad0-104">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="88ad0-105">Cette rubrique fournit un exemple d'écriture de requête avec un filtrage complexe.</span><span class="sxs-lookup"><span data-stu-id="88ad0-105">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88ad0-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="88ad0-106">Example</span></span>  
 <span data-ttu-id="88ad0-107">Cet exemple montre comment rechercher tous les éléments `PurchaseOrder` qui ont un élément `Address` enfant ayant un attribut `Type` égal à « Shipping » et un élément `State` enfant égal à « NY ».</span><span class="sxs-lookup"><span data-stu-id="88ad0-107">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="88ad0-108">Il utilise une sous-requête dans la clause `Where` et l'opérateur `Any` retourne `True` si la collection possède des éléments.</span><span class="sxs-lookup"><span data-stu-id="88ad0-108">It uses a nested query in the `Where` clause, and the `Any` operator returns `True` if the collection has any elements in it.</span></span>  
  
 <span data-ttu-id="88ad0-109">Cet exemple utilise le document XML suivant : [exemple de fichier XML : plusieurs commandes fournisseur (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="88ad0-109">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="88ad0-110">Pour plus d’informations sur la `Any` opérateur, voir [opérations de quantificateur (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).</span><span class="sxs-lookup"><span data-stu-id="88ad0-110">For more information about the `Any` operator, see [Quantifier Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("PurchaseOrders.xml")  
Dim purchaseOrders As IEnumerable(Of XElement) = _  
    From el In root.<PurchaseOrder> _  
    Where _  
        (From add In el.<Address> _  
        Where _  
             add.@Type = "Shipping" And _  
             add.<State>.Value = "NY" _  
        Select add) _  
    .Any() _  
    Select el  
For Each el As XElement In purchaseOrders  
    Console.WriteLine(el.@PurchaseOrderNumber)  
Next  
```  
  
 <span data-ttu-id="88ad0-111">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="88ad0-111">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="88ad0-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="88ad0-112">Example</span></span>  
 <span data-ttu-id="88ad0-113">L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="88ad0-113">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="88ad0-114">Pour plus d’informations, consultez [utilisation des espaces de noms XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="88ad0-114">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="88ad0-115">Cet exemple utilise le document XML suivant : [exemple de fichier XML : plusieurs commandes fournisseur dans un Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="88ad0-115">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")  
        Dim purchaseOrders As IEnumerable(Of XElement) = _  
            From el In root.<aw:PurchaseOrder> _  
            Where _  
                (From add In el.<aw:Address> _  
                Where _  
                     add.@aw:Type = "Shipping" And _  
                     add.<aw:State>.Value = "NY" _  
                Select add) _  
            .Any() _  
            Select el  
        For Each el As XElement In purchaseOrders  
            Console.WriteLine(el.@aw:PurchaseOrderNumber)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="88ad0-116">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="88ad0-116">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="88ad0-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88ad0-117">See Also</span></span>  
 <span data-ttu-id="88ad0-118"><xref:System.Xml.Linq.XElement.Attribute%2A></xref:System.Xml.Linq.XElement.Attribute%2A></span><span class="sxs-lookup"><span data-stu-id="88ad0-118"><xref:System.Xml.Linq.XElement.Attribute%2A></span></span>   
 <span data-ttu-id="88ad0-119"><xref:System.Xml.Linq.XContainer.Elements%2A></xref:System.Xml.Linq.XContainer.Elements%2A></span><span class="sxs-lookup"><span data-stu-id="88ad0-119"><xref:System.Xml.Linq.XContainer.Elements%2A></span></span>   
<span data-ttu-id="88ad0-120"> [Requêtes de base (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md) </span><span class="sxs-lookup"><span data-stu-id="88ad0-120"> [Basic Queries (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md) </span></span>  
<span data-ttu-id="88ad0-121"> [Propriété d’axe enfant XML](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md) </span><span class="sxs-lookup"><span data-stu-id="88ad0-121"> [XML Child Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md) </span></span>  
<span data-ttu-id="88ad0-122"> [Propriété d’axe d’attribut XML](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md) </span><span class="sxs-lookup"><span data-stu-id="88ad0-122"> [XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md) </span></span>  
<span data-ttu-id="88ad0-123"> [Propriété de valeur XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md) </span><span class="sxs-lookup"><span data-stu-id="88ad0-123"> [XML Value Property](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md) </span></span>  
<span data-ttu-id="88ad0-124"> [Opérations de projection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md) </span><span class="sxs-lookup"><span data-stu-id="88ad0-124"> [Projection Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md) </span></span>  
<span data-ttu-id="88ad0-125"> [Opérations de quantificateur (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)</span><span class="sxs-lookup"><span data-stu-id="88ad0-125"> [Quantifier Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)</span></span>
