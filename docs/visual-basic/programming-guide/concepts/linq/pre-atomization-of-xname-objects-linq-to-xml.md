---
title: "Préatomisation des objets XName (LINQ to XML) (Visual Basic) | Documents Microsoft"
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
ms.assetid: 06ea104b-f44c-4bb2-9c34-889ae025c80d
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 519b64a96e03e098d7325cfb779bcd5d53db3741
ms.lasthandoff: 03/13/2017


---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-visual-basic"></a>Préatomisation des objets XName (LINQ to XML) (Visual Basic)
Pour améliorer les performances dans LINQ to XML est de préatomiser <xref:System.Xml.Linq.XName>objets.</xref:System.Xml.Linq.XName> Préatomisation signifie que vous affectez une chaîne à un <xref:System.Xml.Linq.XName>de l’objet avant de créer l’arborescence XML à l’aide des constructeurs de la <xref:System.Xml.Linq.XElement>et <xref:System.Xml.Linq.XAttribute>classes.</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XName> Ensuite, au lieu de transmettre une chaîne au constructeur, ce qui utiliserait la conversion implicite d’une chaîne en <xref:System.Xml.Linq.XName>, vous passez l’initialisé <xref:System.Xml.Linq.XName>objet.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XName>  
  
 Ceci améliore la performance lorsque vous créez une grande arborescence XML dans laquelle des noms spécifiques sont répétés. Pour ce faire, vous déclarez et initialisez <xref:System.Xml.Linq.XName>objets avant de construire l’arborescence XML, puis utiliser le <xref:System.Xml.Linq.XName>objets au lieu de spécifier des chaînes pour les noms d’élément et d’attribut.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XName> Cette technique peut apporter une amélioration significative de la performance si vous créez un grand nombre d'éléments (ou d'attributs) avec le même nom.  
  
 Vous devez tester la préatomisation avec votre scénario pour décider si vous devez l'utiliser.  
  
## <a name="example"></a>Exemple  
 Cela est illustré par l'exemple suivant.  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 L'exemple suivant illustre la même technique dans laquelle le document XML est dans un espace de noms :  
  
```vb  
Dim aw As XNamespace = "http://www.adventure-works.com"  
Dim Root__1 As XName = aw + "Root"  
Dim Data As XName = aw + "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XAttribute(XNamespace.Xmlns + "aw", aw), New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 L'exemple suivant reflète mieux la situation que vous êtes susceptible de rencontrer dans le monde réel. Dans cet exemple, le contenu de l'élément est fourni par une requête :  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim t1 As DateTime = DateTime.Now  
Dim root__2 As New XElement(Root__1, From i In System.Linq.Enumerable.Range(1, 100000)New XElement(Data, New XAttribute(ID, i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
 L'exemple suivant produit une meilleure performance que l'exemple précédent, dans lequel les noms ne sont pas préatomisés :  
  
```vb  
Dim t1 As DateTime = DateTime.Now  
Dim root As New XElement("Root", From i In System.Linq.Enumerable.Range(1, 100000)New XElement("Data", New XAttribute("ID", i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Performances (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)   
 [L’atomisation XName et XNamespace atomisés (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)
