---
title: Comparaison de l&quot;interrogation d&quot;un XDocument et d&quot;un Un XElement (Visual Basic) | Documents Microsoft
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
ms.assetid: 2d111f84-0ded-4cde-8d93-5440557a726d
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 29044cd118bfd8ecc12bddca722ee3656d455e0f
ms.lasthandoff: 03/13/2017


---
# <a name="querying-an-xdocument-vs-querying-an-xelement-visual-basic"></a>Comparaison de l'interrogation d'un XDocument et d'un Un XElement (Visual Basic)
Lorsque vous chargez un document <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>, vous remarquerez que vous devez écrire des requêtes légèrement différemment lorsque vous chargez via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>.</xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName> </xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a>Comparaison de XDocument.Load et XElement.Load  
 Lorsque vous chargez un document XML dans un <xref:System.Xml.Linq.XElement>via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>, le <xref:System.Xml.Linq.XElement>à la racine du document XML arborescence contient l’élément racine du document chargé.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName> </xref:System.Xml.Linq.XElement> Toutefois, lorsque vous chargez le même document XML dans un <xref:System.Xml.Linq.XDocument>via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>, la racine de l’arborescence est un <xref:System.Xml.Linq.XDocument>nœud et l’élément racine du document chargé est le <xref:System.Xml.Linq.XElement>nœud du <xref:System.Xml.Linq.XDocument>.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> enfant autorisé</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName> </xref:System.Xml.Linq.XDocument> Les axes [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] opèrent relativement au nœud racine.  
  
 Ce premier exemple charge une arborescence XML à l’aide de <xref:System.Xml.Linq.XElement.Load%2A>.</xref:System.Xml.Linq.XElement.Load%2A> Il interroge ensuite les éléments enfants de la racine de l'arborescence.  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XElement.Load")  
Console.WriteLine("----")  
Dim doc As XElement = XElement.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 Comme prévu, cet exemple produit la sortie suivante :  
  
```  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 L’exemple suivant est identique à celle ci-dessus, sauf que l’arborescence XML est chargée dans un <xref:System.Xml.Linq.XDocument>au lieu d’un <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument>  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XDocument.Load")  
Console.WriteLine("----")  
Dim doc As XDocument = XDocument.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 Cet exemple génère la sortie suivante :  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 Notez que la même requête a retourné le nœud `Root` au lieu des trois nœuds enfants.  
  
 Pour gérer cette situation consiste à utiliser le <xref:System.Xml.Linq.XDocument.Root%2A>propriété avant d’accéder aux méthodes d’axe, comme suit :</xref:System.Xml.Linq.XDocument.Root%2A>  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XDocument.Load")  
Console.WriteLine("----")  
Dim doc As XDocument = XDocument.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Root.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 Cette requête s’exécute maintenant de la même manière que la requête sur l’arborescence enracinée dans <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement> L'exemple produit la sortie suivante :  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Requêtes de base (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
