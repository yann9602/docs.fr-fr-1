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
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3733b66fbe22bb4835f9bb100b8300dd6d061e3e
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-visual-basic"></a>Comment : récupérer une Collection d’attributs (LINQ to XML) (Visual Basic)
Cette rubrique présente la <xref:System.Xml.Linq.XElement.Attributes%2A>méthode.</xref:System.Xml.Linq.XElement.Attributes%2A> Cette méthode récupère les attributs d'un élément.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment itérer au sein de la collection d’attributs d’un élément.  
  
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
  
 Ce code génère la sortie suivante :  
  
```  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Axes LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
