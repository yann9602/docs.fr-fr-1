---
title: "Guide pratique pour récupérer un seul élément enfant (LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 722a6b6630fd08a328a26dcef4d72a8cdd817924
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-c"></a><span data-ttu-id="f88e1-102">Guide pratique pour récupérer un seul élément enfant (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f88e1-102">How to: Retrieve a Single Child Element (LINQ to XML) (C#)</span></span>
<span data-ttu-id="f88e1-103">Cette rubrique explique comment récupérer un seul élément enfant, étant donné le nom de l'élément enfant.</span><span class="sxs-lookup"><span data-stu-id="f88e1-103">This topic explains how to retrieve a single child element, given the name of the child element.</span></span> <span data-ttu-id="f88e1-104">Lorsque vous connaissez le nom de l'élément enfant et qu'il n'y a qu'un seul élément qui possède ce nom, il peut être plus commode de récupérer un seul élément plutôt qu'une collection.</span><span class="sxs-lookup"><span data-stu-id="f88e1-104">When you know the name of the child element and that there is only one element that has this name, it can be convenient to retrieve just one element, instead of a collection.</span></span>  
  
 <span data-ttu-id="f88e1-105">La méthode <xref:System.Xml.Linq.XContainer.Element%2A> retourne le premier objet <xref:System.Xml.Linq.XElement> enfant avec l'objet <xref:System.Xml.Linq.XName> spécifié.</span><span class="sxs-lookup"><span data-stu-id="f88e1-105">The <xref:System.Xml.Linq.XContainer.Element%2A> method returns the first child <xref:System.Xml.Linq.XElement> with the specified <xref:System.Xml.Linq.XName>.</span></span>  
  
 <span data-ttu-id="f88e1-106">Si vous souhaitez récupérer un seul élément enfant en Visual Basic, une approche courante consiste à utiliser la propriété XML, puis à récupérer le premier élément à l'aide de la notation d'indexeur de tableau.</span><span class="sxs-lookup"><span data-stu-id="f88e1-106">If you want to retrieve a single child element in Visual Basic, a common approach is to use the XML property, and then retrieve the first element using array indexer notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f88e1-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="f88e1-107">Example</span></span>  
 <span data-ttu-id="f88e1-108">L'exemple suivant illustre l'utilisation de la méthode <xref:System.Xml.Linq.XContainer.Element%2A>.</span><span class="sxs-lookup"><span data-stu-id="f88e1-108">The following example demonstrates the use of the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="f88e1-109">Cet exemple prend l'arborescence XML nommée `po` et recherche le premier élément nommé `Comment`.</span><span class="sxs-lookup"><span data-stu-id="f88e1-109">This example takes the XML tree named `po` and finds the first element named `Comment`.</span></span>  
  
 <span data-ttu-id="f88e1-110">L'exemple Visual Basic illustre l'utilisation de la notation d'indexeur de tableau pour récupérer un seul élément.</span><span class="sxs-lookup"><span data-stu-id="f88e1-110">The Visual Basic example shows using array indexer notation to retrieve a single element.</span></span>  
  
 <span data-ttu-id="f88e1-111">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : commande fournisseur typique (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="f88e1-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
XElement e = po.Element("DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="f88e1-112">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="f88e1-112">This example produces the following output:</span></span>  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a><span data-ttu-id="f88e1-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="f88e1-113">Example</span></span>  
 <span data-ttu-id="f88e1-114">L'exemple suivant illustre le même code pour du XML qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="f88e1-114">The following example shows the same code for XML that is in a namespace.</span></span> <span data-ttu-id="f88e1-115">Pour plus d’informations, consultez [Utilisation des espaces de noms XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="f88e1-115">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="f88e1-116">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : commande fournisseur typique dans un espace de noms](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="f88e1-116">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
XElement e = po.Element(aw + "DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="f88e1-117">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="f88e1-117">This example produces the following output:</span></span>  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f88e1-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f88e1-118">See Also</span></span>  
 [<span data-ttu-id="f88e1-119">Axes LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="f88e1-119">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
