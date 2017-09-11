---
title: "Comment : trier des éléments (Visual Basic) | Documents Microsoft"
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
ms.assetid: c2c09279-6c8a-482e-8e71-b1453a815052
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 5b36e9717b3366d73ee4c72390c88dde52248496
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017


---
# <a name="how-to-sort-elements-visual-basic"></a><span data-ttu-id="dfabb-102">Comment : trier des éléments (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dfabb-102">How to: Sort Elements (Visual Basic)</span></span>
<span data-ttu-id="dfabb-103">Cet exemple montre comment écrire une requête qui trie ses résultats.</span><span class="sxs-lookup"><span data-stu-id="dfabb-103">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfabb-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="dfabb-104">Example</span></span>  
 <span data-ttu-id="dfabb-105">Cet exemple utilise le document XML suivant : [exemple de fichier XML : données numériques (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="dfabb-105">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
Dim prices As IEnumerable(Of Decimal) = _  
    From el In root.<Data> _  
    Let price = Convert.ToDecimal(el.<Price>.Value) _  
    Order By (price) _  
    Select price  
For Each el As Decimal In prices  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="dfabb-106">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="dfabb-106">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="dfabb-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="dfabb-107">Example</span></span>  
 <span data-ttu-id="dfabb-108">L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="dfabb-108">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="dfabb-109">Pour plus d’informations, consultez [utilisation des espaces de noms XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="dfabb-109">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="dfabb-110">Cet exemple utilise le document XML suivant : [exemple de fichier XML : données numériques dans un Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="dfabb-110">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("DataInNamespace.xml")  
        Dim prices As IEnumerable(Of Decimal) = _  
            From el In root.<Data> _  
            Let price = Convert.ToDecimal(el.<Price>.Value) _  
            Order By (price) _  
            Select price  
        For Each el As Decimal In prices  
            Console.WriteLine(el)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="dfabb-111">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="dfabb-111">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="dfabb-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dfabb-112">See Also</span></span>  
 <span data-ttu-id="dfabb-113">[Tri des données](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md) </span><span class="sxs-lookup"><span data-stu-id="dfabb-113">[Sorting Data](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md) </span></span>  
<span data-ttu-id="dfabb-114"> [Requêtes de base (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="dfabb-114"> [Basic Queries (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)</span></span>
