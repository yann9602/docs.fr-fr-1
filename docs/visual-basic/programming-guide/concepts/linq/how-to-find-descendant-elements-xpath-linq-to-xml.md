---
title: "Comment : rechercher des éléments descendants (XPath-LINQ to XML) (Visual Basic) | Documents Microsoft"
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
ms.assetid: e7e2dc9e-bda9-420d-a5b1-4fabf1cca46b
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 3fc67c7717447dbdebc32743f89b3178c7a8e220
ms.contentlocale: fr-fr
ms.lasthandoff: 05/23/2017


---
# <a name="how-to-find-descendant-elements-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="bbd77-102">Comment : rechercher des éléments descendants (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bbd77-102">How to: Find Descendant Elements (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="bbd77-103">Cette rubrique montre comment obtenir les éléments descendants avec un nom particulier.</span><span class="sxs-lookup"><span data-stu-id="bbd77-103">This topic shows how to get the descendant elements with a particular name.</span></span>  
  
 <span data-ttu-id="bbd77-104">L'expression XPath est `//Name`.</span><span class="sxs-lookup"><span data-stu-id="bbd77-104">The XPath expression is `//Name`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbd77-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="bbd77-105">Example</span></span>  
 <span data-ttu-id="bbd77-106">Cet exemple recherche tous les descendants nommés `Name`.</span><span class="sxs-lookup"><span data-stu-id="bbd77-106">This example finds all descendants named `Name`.</span></span>  
  
 <span data-ttu-id="bbd77-107">Cet exemple utilise le document XML suivant : [exemple de fichier XML : plusieurs commandes fournisseur (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="bbd77-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```vb  
      Dim po As XDocument = XDocument.Load("PurchaseOrders.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = po...<Name>  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = po.XPathSelectElements("//Name")  
  
If (list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count()) Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="bbd77-108">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="bbd77-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bbd77-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bbd77-109">See Also</span></span>  
 [<span data-ttu-id="bbd77-110">LINQ to XML pour les utilisateurs XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bbd77-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)

