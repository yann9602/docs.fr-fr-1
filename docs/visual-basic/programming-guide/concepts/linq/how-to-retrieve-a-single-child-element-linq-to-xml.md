---
title: "Comment : récupérer un seul élément enfant (LINQ to XML) (Visual Basic) | Documents Microsoft"
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
ms.assetid: 0033e258-d9c4-4569-86f6-79b7c06d1204
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 006a6afbb07ceea64b8fcc6cdab1d4fd31ae3c87
ms.contentlocale: fr-fr
ms.lasthandoff: 05/23/2017


---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-visual-basic"></a><span data-ttu-id="c53ac-102">Comment : récupérer un seul élément enfant (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c53ac-102">How to: Retrieve a Single Child Element (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="c53ac-103">Cette rubrique explique comment récupérer un seul élément enfant, étant donné le nom de l'élément enfant.</span><span class="sxs-lookup"><span data-stu-id="c53ac-103">This topic explains how to retrieve a single child element, given the name of the child element.</span></span> <span data-ttu-id="c53ac-104">Lorsque vous connaissez le nom de l’élément enfant et qu’il n’y a qu’un seul élément qui possède ce nom, il peut être plus commode de récupérer un seul élément plutôt qu’une collection.</span><span class="sxs-lookup"><span data-stu-id="c53ac-104">When you know the name of the child element and that there is only one element that has this name, it can be convenient to retrieve just one element, instead of a collection.</span></span>  
  
 <span data-ttu-id="c53ac-105">La <xref:System.Xml.Linq.XContainer.Element%2A>méthode retourne le premier enfant <xref:System.Xml.Linq.XElement>avec le type spécifié <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XContainer.Element%2A></span><span class="sxs-lookup"><span data-stu-id="c53ac-105">The <xref:System.Xml.Linq.XContainer.Element%2A> method returns the first child <xref:System.Xml.Linq.XElement> with the specified <xref:System.Xml.Linq.XName>.</span></span>  
  
 <span data-ttu-id="c53ac-106">Si vous souhaitez récupérer un seul élément enfant en Visual Basic, une approche courante consiste à utiliser la propriété XML, puis à récupérer le premier élément à l'aide de la notation d'indexeur de tableau.</span><span class="sxs-lookup"><span data-stu-id="c53ac-106">If you want to retrieve a single child element in Visual Basic, a common approach is to use the XML property, and then retrieve the first element using array indexer notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c53ac-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="c53ac-107">Example</span></span>  
 <span data-ttu-id="c53ac-108">L’exemple suivant illustre l’utilisation de la <xref:System.Xml.Linq.XContainer.Element%2A>méthode.</xref:System.Xml.Linq.XContainer.Element%2A></span><span class="sxs-lookup"><span data-stu-id="c53ac-108">The following example demonstrates the use of the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="c53ac-109">Cet exemple prend l'arborescence XML nommée `po` et recherche le premier élément nommé `Comment`.</span><span class="sxs-lookup"><span data-stu-id="c53ac-109">This example takes the XML tree named `po` and finds the first element named `Comment`.</span></span>  
  
 <span data-ttu-id="c53ac-110">L'exemple Visual Basic illustre l'utilisation de la notation d'indexeur de tableau pour récupérer un seul élément.</span><span class="sxs-lookup"><span data-stu-id="c53ac-110">The Visual Basic example shows using array indexer notation to retrieve a single element.</span></span>  
  
 <span data-ttu-id="c53ac-111">Cet exemple utilise le document XML suivant : [exemple de fichier XML : commande fournisseur typique (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c53ac-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim e As XElement = po.<DeliveryNotes>(0)  
Console.WriteLine(e)  
```  
  
 <span data-ttu-id="c53ac-112">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="c53ac-112">This example produces the following output:</span></span>  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a><span data-ttu-id="c53ac-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="c53ac-113">Example</span></span>  
 <span data-ttu-id="c53ac-114">L'exemple suivant illustre le même code pour du XML qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="c53ac-114">The following example shows the same code for XML that is in a namespace.</span></span> <span data-ttu-id="c53ac-115">Pour plus d’informations, consultez [utilisation des espaces de noms XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="c53ac-115">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="c53ac-116">Cet exemple utilise le document XML suivant : [exemple de fichier XML : commande fournisseur typique dans un Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="c53ac-116">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")  
        Dim e As XElement = po.<aw:DeliveryNotes>(0)  
        Console.WriteLine(e)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="c53ac-117">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="c53ac-117">This example produces the following output:</span></span>  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c53ac-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c53ac-118">See Also</span></span>  
 [<span data-ttu-id="c53ac-119">Axes LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c53ac-119">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)

