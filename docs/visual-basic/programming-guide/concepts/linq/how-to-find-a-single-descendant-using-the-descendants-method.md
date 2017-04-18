---
title: "Comment : rechercher un seul Descendant à l’aide de la méthode Descendants (Visual Basic) | Documents Microsoft"
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
ms.assetid: 0c03468c-efc8-4140-98f3-fb67acd9e8e1
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 74d4dd0b805a5ea2c189cb89bcaeca3f4cac1268
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-find-a-single-descendant-using-the-descendants-method-visual-basic"></a>Comment : rechercher un seul Descendant à l’aide de la méthode Descendants (Visual Basic)
Vous pouvez utiliser la <xref:System.Xml.Linq.XContainer.Descendants%2A>méthode d’axe pour écrire rapidement du code pour rechercher de façon unique un seul élément de nommé.</xref:System.Xml.Linq.XContainer.Descendants%2A> Cette technique est particulièrement utile lorsque vous souhaitez rechercher un descendant particulier avec un nom spécifique. Vous pouvez écrire du code pour naviguer jusqu'à l’élément souhaité, mais il est souvent plus rapide et plus facile d’écrire le code à l’aide du <xref:System.Xml.Linq.XContainer.Descendants%2A>axe.</xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise le <xref:System.Linq.Enumerable.First%2A>opérateur de requête standard.</xref:System.Linq.Enumerable.First%2A>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>  
            <GrandChild1>GC1 Value</GrandChild1>  
        </Child1>  
        <Child2>  
            <GrandChild2>GC2 Value</GrandChild2>  
        </Child2>  
        <Child3>  
            <GrandChild3>GC3 Value</GrandChild3>  
        </Child3>  
        <Child4>  
            <GrandChild4>GC4 Value</GrandChild4>  
        </Child4>  
    </Root>  
Dim grandChild3 As String = _  
    (From el In root...<GrandChild3> _  
    Select el).First()  
Console.WriteLine(grandChild3)  
```  
  
 Ce code génère la sortie suivante :  
  
```  
GC3 Value  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms. Pour plus d’informations, consultez [utilisation des espaces de noms XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child1>  
                    <aw:GrandChild1>GC1 Value</aw:GrandChild1>  
                </aw:Child1>  
                <aw:Child2>  
                    <aw:GrandChild2>GC2 Value</aw:GrandChild2>  
                </aw:Child2>  
                <aw:Child3>  
                    <aw:GrandChild3>GC3 Value</aw:GrandChild3>  
                </aw:Child3>  
                <aw:Child4>  
                    <aw:GrandChild4>GC4 Value</aw:GrandChild4>  
                </aw:Child4>  
            </aw:Root>  
        Dim grandChild3 As String = _  
            (From el In root...<aw:GrandChild3> _  
            Select el).First()  
        Console.WriteLine(grandChild3)  
    End Sub  
End Module  
```  
  
 Ce code génère la sortie suivante :  
  
```  
GC3 Value  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Requêtes de base (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
