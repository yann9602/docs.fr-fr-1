---
title: "Comment : rechercher les frères (XPath-LINQ to XML) précédents (Visual Basic) | Documents Microsoft"
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
ms.assetid: 59055718-d0a7-4db3-8901-18dd33587703
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 250028f73eff7aad3926ee4916aef7d118b6fbea
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-find-preceding-siblings-xpath-linq-to-xml-visual-basic"></a>Comment : rechercher les frères (XPath-LINQ to XML) précédents (Visual Basic)
Cette rubrique compare l’expression XPath `preceding-sibling` axe pour le [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] enfant <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName>axe.</xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName>  
  
 L’expression XPath est la suivante :  
  
 `preceding-sibling::*`  
  
 Notez que les résultats des deux <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A>et <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName>sont dans l’ordre du document.</xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName> </xref:System.Xml.XPath.Extensions.XPathSelectElements%2A>  
  
## <a name="example"></a>Exemple  
 L'exemple suivant recherche l'élément `FullAddress`, puis récupère les éléments précédents à l'aide de l'axe `preceding-sibling`.  
  
 Cet exemple utilise le document XML suivant : [exemple de fichier XML : clients et commandes (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
```vb  
Dim co As XElement = XElement.Load("CustomersOrders.xml")  
Dim add As XElement = co.<Customers>.<Customer>. _  
        <FullAddress>.FirstOrDefault  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = add.ElementsBeforeSelf()  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = add.XPathSelectElements("preceding-sibling::*")  
  
If list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list2  
    Console.WriteLine(el)  
Next  
```  
  
 Cet exemple génère la sortie suivante :  
  
```  
Results are identical  
<CompanyName>Great Lakes Food Market</CompanyName>  
<ContactName>Howard Snyder</ContactName>  
<ContactTitle>Marketing Manager</ContactTitle>  
<Phone>(503) 555-7555</Phone>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ to XML pour les utilisateurs XPath (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
