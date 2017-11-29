---
title: "Comment : rechercher le frère précédent (XPath-LINQ to XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec046283-9fe2-4440-b295-860bf700099d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a6eb74dc4c106deadb92da1414e359d567fda6df
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-visual-basic"></a>Comment : rechercher le frère précédent (XPath-LINQ to XML) (Visual Basic)
Il peut arriver que vous souhaitiez rechercher le frère précédent d'un nœud. Étant donné la différence de sémantique des prédicats de position pour les axes enfants précédents dans XPath par opposition à [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], il s'agit de l'une des comparaisons les plus intéressantes.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, la requête [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] utilise l'opérateur <xref:System.Linq.Enumerable.Last%2A> pour rechercher le dernier nœud dans la collection retournée par <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>. Par contraste, l'expression XPath utilise un prédicat avec une valeur de 1 pour rechercher l'élément précédent.  
  
```vb  
Dim root As XElement = _   
    <Root>  
        <Child1/>  
        <Child2/>  
        <Child3/>  
        <Child4/>  
    </Root>  
Dim child4 As XElement = root.Element("Child4")  
  
' LINQ to XML query  
Dim el1 As XElement = child4.ElementsBeforeSelf().Last()  
  
' XPath expression  
Dim el2 As XElement = _  
    DirectCast(child4.XPathEvaluate("preceding-sibling::*[1]"),  _  
    IEnumerable).Cast(Of XElement)().First()  
  
If el1 Is el2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(el1)  
```  
  
 Cet exemple génère la sortie suivante :  
  
```  
Results are identical  
<Child3 />  
```  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ to XML pour les utilisateurs de XPath (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
