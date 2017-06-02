---
title: "Comment : rechercher une Union de deux chemins d’emplacements (XPath-LINQ to XML) (Visual Basic) | Documents Microsoft"
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
ms.assetid: c82c09b4-cb0a-47ec-8cc3-a124144c2788
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 90fe1bd9a7992c5e3f4c57f5596a88e5be506917
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-visual-basic"></a>Comment : rechercher une Union de deux chemins d’emplacements (XPath-LINQ to XML) (Visual Basic)
XPath vous permet de rechercher l’union des résultats de deux chemins d’emplacements XPath.  
  
 L’expression XPath est la suivante :  
  
 `//Category|//Price`  
  
 Vous pouvez obtenir les mêmes résultats à l’aide de la <xref:System.Linq.Enumerable.Concat%2A>opérateur de requête standard.</xref:System.Linq.Enumerable.Concat%2A>  
  
## <a name="example"></a>Exemple  
 Cet exemple recherche tous les éléments `Category` et tous les éléments `Price` et il les concatène en une collection unique. Notez que la [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] requête appelle <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A>pour classer les résultats.</xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> Les résultats de l’évaluation d’expression XPath sont également dans l’ordre du document.  
  
 Cet exemple utilise le document XML suivant : [exemple de fichier XML : données numériques (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).  
  
```vb  
Dim data As XDocument = XDocument.Load("Data.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    data...<Category>.Concat(data...<Price>).InDocumentOrder()  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = _  
    data.XPathSelectElements("//Category|//Price")  
  
If list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 Cet exemple génère la sortie suivante :  
  
```  
Results are identical  
<Category>A</Category>  
<Price>24.50</Price>  
<Category>B</Category>  
<Price>89.99</Price>  
<Category>A</Category>  
<Price>4.95</Price>  
<Category>A</Category>  
<Price>66.00</Price>  
<Category>B</Category>  
<Price>.99</Price>  
<Category>A</Category>  
<Price>29.00</Price>  
<Category>B</Category>  
<Price>6.99</Price>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ to XML pour les utilisateurs XPath (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)

