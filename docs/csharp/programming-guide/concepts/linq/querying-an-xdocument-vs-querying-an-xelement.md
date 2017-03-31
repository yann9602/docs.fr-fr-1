---
title: Comparaison de l&quot;interrogation d&quot;un XDocument et d&quot;un XElement (C#) | Microsoft Docs
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 46221ff5-62ee-4de8-93ba-66465facb5c1
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9a3da563618ad3dbc9797f252ab51588a43ce8e6
ms.lasthandoff: 03/13/2017


---
# <a name="querying-an-xdocument-vs-querying-an-xelement-c"></a>Comparaison de l'interrogation d'un XDocument et d'un XElement (C#)
Notez que vous devez écrire des requêtes de façon légèrement différente quand vous chargez un document via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName> au lieu de le charger via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>.  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a>Comparaison de XDocument.Load et XElement.Load  
 Lorsque vous chargez un document XML dans un <xref:System.Xml.Linq.XElement> via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>, le <xref:System.Xml.Linq.XElement> situé à la racine de l’arborescence XML contient l’élément racine du document chargé. Toutefois, lorsque vous chargez le même document XML dans un <xref:System.Xml.Linq.XDocument> via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>, la racine de l’arborescence est un nœud <xref:System.Xml.Linq.XDocument> et l’élément racine du document chargé est le seul et unique nœud <xref:System.Xml.Linq.XElement> enfant autorisé du <xref:System.Xml.Linq.XDocument>. Les axes [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] opèrent relativement au nœud racine.  
  
 Ce premier exemple charge une arborescence XML à l’aide de <xref:System.Xml.Linq.XElement.Load%2A>. Il interroge ensuite les éléments enfants de la racine de l'arborescence.  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XElement.Load");  
Console.WriteLine("----");  
XElement doc = XElement.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 Comme prévu, cet exemple produit la sortie suivante :  
  
```  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 L’exemple suivant est identique au précédent, hormis le fait que l’arborescence XML est chargée dans un <xref:System.Xml.Linq.XDocument> et non pas dans un <xref:System.Xml.Linq.XElement>.  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XDocument.Load");  
Console.WriteLine("----");  
XDocument doc = XDocument.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
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
  
 L’une des solutions à ce problème consiste à utiliser la propriété <xref:System.Xml.Linq.XDocument.Root%2A> avant d’accéder aux méthodes d’axe, comme suit :  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XDocument.Load");  
Console.WriteLine("----");  
XDocument doc = XDocument.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Root.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 Cette requête s’exécute maintenant de la même manière que la requête sur l’arborescence avec la racine dans <xref:System.Xml.Linq.XElement>. L'exemple produit la sortie suivante :  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Requêtes de base (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
