---
title: "Comment : récupérer une Collection d’attributs (LINQ to XML) (Visual Basic) | Documents Microsoft"
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
ms.assetid: a07e9645-b45b-403b-b698-f652f904c7d2
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 696cb1c41d38cfc7f3d739265bf79af62ff456fe
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017


---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-visual-basic"></a><span data-ttu-id="2e48a-102">Comment : récupérer une Collection d’attributs (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e48a-102">How to: Retrieve a Collection of Attributes (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="2e48a-103">Cette rubrique présente la <xref:System.Xml.Linq.XElement.Attributes%2A>méthode.</xref:System.Xml.Linq.XElement.Attributes%2A></span><span class="sxs-lookup"><span data-stu-id="2e48a-103">This topic introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="2e48a-104">Cette méthode récupère les attributs d'un élément.</span><span class="sxs-lookup"><span data-stu-id="2e48a-104">This method retrieves the attributes of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e48a-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="2e48a-105">Example</span></span>  
 <span data-ttu-id="2e48a-106">L’exemple suivant montre comment itérer au sein de la collection d’attributs d’un élément.</span><span class="sxs-lookup"><span data-stu-id="2e48a-106">The following example shows how to iterate through the collection of attributes of an element.</span></span>  
  
```vb  
Dim val = _  
    <Value ID="1243" Type="int" ConvertableTo="double">100</Value>  
Dim listOfAttributes As IEnumerable(Of XAttribute) = _  
    From att In val.Attributes() _  
    Select att  
For Each att As XAttribute In listOfAttributes  
    Console.WriteLine(att)  
Next  
```  
  
 <span data-ttu-id="2e48a-107">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="2e48a-107">This code produces the following output:</span></span>  
  
```  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e48a-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e48a-108">See Also</span></span>  
 [<span data-ttu-id="2e48a-109">Axes LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e48a-109">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
