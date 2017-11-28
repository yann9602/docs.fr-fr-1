---
title: "Guide pratique pour récupérer une collection d’éléments (LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 215c32d0879f13ad4ec262bc916de5868ba030e7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-c"></a><span data-ttu-id="5c5f4-102">Guide pratique pour récupérer une collection d’éléments (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="5c5f4-102">How to: Retrieve a Collection of Elements (LINQ to XML) (C#)</span></span>
<span data-ttu-id="5c5f4-103">Cette rubrique illustre la méthode <xref:System.Xml.Linq.XContainer.Elements%2A>.</span><span class="sxs-lookup"><span data-stu-id="5c5f4-103">This topic demonstrates the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span> <span data-ttu-id="5c5f4-104">Cette méthode récupère une collection d’éléments enfants d’un élément.</span><span class="sxs-lookup"><span data-stu-id="5c5f4-104">This method retrieves a collection of the child elements of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c5f4-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="5c5f4-105">Example</span></span>  
 <span data-ttu-id="5c5f4-106">Cet exemple itère au sein des éléments enfants de l'élément `purchaseOrder`.</span><span class="sxs-lookup"><span data-stu-id="5c5f4-106">This example iterates through the child elements of the `purchaseOrder` element.</span></span>  
  
 <span data-ttu-id="5c5f4-107">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : commande fournisseur typique (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="5c5f4-107">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> childElements =  
    from el in po.Elements()  
    select el;  
foreach (XElement el in childElements)  
    Console.WriteLine("Name: " + el.Name);  
```  
  
 <span data-ttu-id="5c5f4-108">Cet exemple produit la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="5c5f4-108">This example produces the following output.</span></span>  
  
```  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a><span data-ttu-id="5c5f4-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c5f4-109">See Also</span></span>  
 [<span data-ttu-id="5c5f4-110">Axes LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="5c5f4-110">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
