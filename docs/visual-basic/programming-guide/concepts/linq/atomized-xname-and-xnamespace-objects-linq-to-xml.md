---
title: "L’atomisation XName et XNamespace atomisés (LINQ to XML) (Visual Basic) | Documents Microsoft"
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
ms.assetid: 21ee7585-7df9-40b4-8c76-a12bb5f29bb3
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b08f3116f5acb404cf2c33072ec31fbaada4e7cb
ms.lasthandoff: 03/13/2017


---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-visual-basic"></a>L’atomisation XName et XNamespace atomisés (LINQ to XML) (Visual Basic)
<xref:System.Xml.Linq.XName>et <xref:System.Xml.Linq.XNamespace>sont des objets *atomisés*; autrement dit, si elles contiennent le même nom qualifié, ils font référence au même objet.</xref:System.Xml.Linq.XNamespace></xref:System.Xml.Linq.XName> Ceci permet d'améliorer les performances des requêtes : lorsque vous comparez deux noms atomisés pour en vérifier l'égalité, le langage intermédiaire sous-jacent doit seulement déterminer si les deux références pointent vers le même objet. Le code sous-jacent ne doit pas effectuer de comparaisons de chaînes, ce qui prendrait beaucoup de temps.  
  
## <a name="atomization-semantics"></a>Sémantique d'atomisation  
 L’atomisation signifie que si deux <xref:System.Xml.Linq.XName>objets ont le même nom local et elles se trouvent dans le même espace de noms, ils partagent la même instance.</xref:System.Xml.Linq.XName> De la même façon, si deux <xref:System.Xml.Linq.XNamespace>ont le même espace de noms URI, ils partagent la même instance.</xref:System.Xml.Linq.XNamespace>  
  
 Pour qu'une classe autorise les objets atomisés, le constructeur de cette classe doit être privé, et non public. En effet, si le constructeur était public, vous pourriez créer un objet non atomisé. <xref:System.Xml.Linq.XName>Et <xref:System.Xml.Linq.XNamespace>classes implémentent un opérateur de conversion implicite pour convertir une chaîne en un <xref:System.Xml.Linq.XName>ou <xref:System.Xml.Linq.XNamespace>.</xref:System.Xml.Linq.XNamespace> </xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XNamespace> </xref:System.Xml.Linq.XName> Telle est la manière dont vous obtenez une instance de ces objets. Vous ne pouvez pas obtenir une instance à l'aide d'un constructeur, car le constructeur est inaccessible.  
  
 <xref:System.Xml.Linq.XName>et <xref:System.Xml.Linq.XNamespace>implémentent également les opérateurs d’égalité et d’inégalité, afin de déterminer si les deux objets comparés sont des références à la même instance.</xref:System.Xml.Linq.XNamespace></xref:System.Xml.Linq.XName>  
  
## <a name="example"></a>Exemple  
 Le code suivant crée certains <xref:System.Xml.Linq.XElement>objets et démontre que des noms identiques partagent la même instance.</xref:System.Xml.Linq.XElement>  
  
```vb  
Dim r1 As New XElement("Root", "data1")  
Dim r2 As XElement = XElement.Parse("<Root>data2</Root>")  
  
If DirectCast(r1.Name, Object) = DirectCast(r2.Name, Object) Then  
    Console.WriteLine("r1 and r2 have names that refer to the same instance.")  
Else  
    Console.WriteLine("Different")  
End If  
  
Dim n As XName = "Root"  
  
If DirectCast(n, Object) = DirectCast(r1.Name, Object) Then  
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.")  
Else  
    Console.WriteLine("Different")  
End If  
  
```  
  
 Cet exemple génère la sortie suivante :  
  
```  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 Comme mentionné précédemment, l’avantage des objets atomisés est que lorsque vous utilisez une des méthodes d’axe qui prennent un <xref:System.Xml.Linq.XName>en tant que paramètre, la méthode d’axe doit seulement déterminer que deux noms font référence à la même instance pour sélectionner les éléments voulus.</xref:System.Xml.Linq.XName>  
  
 L’exemple suivant passe une <xref:System.Xml.Linq.XName>à la <xref:System.Xml.Linq.XContainer.Descendants%2A>appel de méthode, qui a ensuite les meilleures performances grâce au modèle d’atomisation.</xref:System.Xml.Linq.XContainer.Descendants%2A> </xref:System.Xml.Linq.XName>  
  
```vb  
Dim root As New XElement("Root", New XElement("C1", 1), New XElement("Z1", New XElement("C1", 2), New XElement("C1", 1)))  
  
Dim query = From e In root.Descendants("C1") Where CInt(e) = 1e  
  
For Each z As var In query  
    Console.WriteLine(z)  
Next  
```  
  
 Cet exemple génère la sortie suivante :  
  
```  
<C1>1</C1>  
<C1>1</C1>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Performances (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
