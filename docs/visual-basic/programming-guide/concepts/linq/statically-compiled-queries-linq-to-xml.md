---
title: "Compilé statiquement des requêtes (LINQ to XML) (Visual Basic) | Documents Microsoft"
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
ms.assetid: 3f4825c7-c3b0-48da-ba4e-8e97fb2a2f34
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2ea8e71acf861b93a21296c74254b3ca4d977d0a
ms.lasthandoff: 03/13/2017


---
# <a name="statically-compiled-queries-linq-to-xml-visual-basic"></a>Compilé statiquement des requêtes (LINQ to XML) (Visual Basic)
Un des performances plus importants avantages de LINQ to XML, par opposition à <xref:System.Xml.XmlDocument>, sont que les requêtes dans LINQ to XML sont compilées statiquement, tandis que les requêtes XPath doivent être interprétés au moment de l’exécution.</xref:System.Xml.XmlDocument> Cette fonctionnalité étant intégrée dans LINQ to XML, vous n’avez pas à effectuer d’étapes supplémentaires pour en bénéficier, mais il est utile de comprendre cette distinction pour pouvoir choisir entre ces deux technologies. Cette rubrique explique en quoi consiste la différence.  
  
## <a name="statically-compiled-queries-vs-xpath"></a>Requêtes compilées statiquement et XPath  
 L'exemple suivant montre comment obtenir les éléments descendants avec un nom spécifié et avec un attribut avec une valeur spécifiée.  
  
 L'expression XPath équivalente est indiquée ci-dessous :  
  
```  
//Address[@Type='Shipping']  
```  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 = From el In po.Descendants("Address")  
            Where el.@Type = "Shipping"  
  
For Each el In list1  
    Console.WriteLine(el)  
Next  
  
```  
  
 L'expression de requête contenue dans cet exemple est réécrite par le compilateur en syntaxe de requête fondée sur une méthode. L'exemple suivant, qui est écrit dans la syntaxe de requête fondée sur une méthode, produit les mêmes résultats que l'exemple précédent :  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next   
```  
  
 Le <xref:System.Linq.Enumerable.Where%2A>méthode est une méthode d’extension.</xref:System.Linq.Enumerable.Where%2A> Pour plus d’informations, consultez [les méthodes d’Extension](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md). Étant donné que <xref:System.Linq.Enumerable.Where%2A>est une méthode d’extension, la requête ci-dessus est compilée comme si elle était écrite comme suit :</xref:System.Linq.Enumerable.Where%2A>  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next  
```  
  
 Cet exemple produit exactement les mêmes résultats que les deux exemples précédents. Ceci illustre le fait que les requêtes sont effectivement compilées en appels de méthodes liés statiquement. Ceci, combiné à la sémantique d'exécution différée des itérateurs, améliore la performance. Pour plus d’informations sur la sémantique d’exécution différée des itérateurs, consultez [l’exécution différée et évaluation différées dans LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
> [!NOTE]
>  Ces exemples sont représentatifs du code susceptible d'être écrit par le compilateur. L'implémentation réelle peut différer légèrement de ces exemples, mais la performance sera identique ou similaire à celle de ces exemples.  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a>Exécution d’expressions XPath avec XmlDocument  
 L’exemple suivant utilise <xref:System.Xml.XmlDocument>pour obtenir les mêmes résultats que les exemples précédents :</xref:System.Xml.XmlDocument>  
  
```vb  
Dim reader = Xml.XmlReader.Create("PurchaseOrders.xml")  
Dim doc As New Xml.XmlDocument()  
doc.Load(reader)  
Dim nl As Xml.XmlNodeList = doc.SelectNodes(".//Address[@Type='Shipping']")  
For Each n As Xml.XmlNode In nl  
    Console.WriteLine(n.OuterXml)  
Next  
reader.Close()  
  
```  
  
 Cette requête renvoie le même résultat que les exemples qui utilisent LINQ to XML ; la seule différence est que LINQ to XML met en retrait le XML imprimé, tandis que <xref:System.Xml.XmlDocument>ne.</xref:System.Xml.XmlDocument>  
  
 Toutefois, les <xref:System.Xml.XmlDocument>approche généralement n’exécute pas et LINQ to XML, car la <xref:System.Xml.XmlNode.SelectNodes%2A>méthode procédez comme suit en interne chaque fois qu’elle est appelée :</xref:System.Xml.XmlNode.SelectNodes%2A> </xref:System.Xml.XmlDocument>  
  
-   Elle analyse la chaîne qui contient l’expression XPath, en scindant la chaîne en jetons.  
  
-   Elle valide les jetons pour s'assurer que l'expression XPath est valide.  
  
-   Elle traduit l'expression en arborescence d'expression interne.  
  
-   Elle effectue l'itération sur les nœuds, en sélectionnant de façon appropriée les nœuds pour le jeu de résultats basé sur l'évaluation de l'expression.  
  
 Ces opérations représentent un travail considérablement plus important que celui effectué par la requête LINQ to XML correspondant. La différence de performance spécifique varie selon les différents types de requêtes, mais en général les requêtes LINQ to XML effectuent moins de tâches et par conséquent plus performant, que l’évaluation des expressions XPath à l’aide de <xref:System.Xml.XmlDocument>.</xref:System.Xml.XmlDocument>  
  
## <a name="see-also"></a>Voir aussi  
 [Performances (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
