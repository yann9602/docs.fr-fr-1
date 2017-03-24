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
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8ebea6b2a62120293eec50b5f304dbfd426a8fe1
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-find-descendant-elements-xpath-linq-to-xml-visual-basic"></a>Comment : rechercher des éléments descendants (XPath-LINQ to XML) (Visual Basic)
Cette rubrique montre comment obtenir les éléments descendants avec un nom particulier.  
  
 L'expression XPath est `//Name`.  
  
## <a name="example"></a>Exemple  
 Cet exemple recherche tous les descendants nommés `Name`.  
  
 Cet exemple utilise le document XML suivant : [exemple de fichier XML : plusieurs commandes fournisseur (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
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
  
 Cet exemple génère la sortie suivante :  
  
```  
Results are identical  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ to XML pour les utilisateurs XPath (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
