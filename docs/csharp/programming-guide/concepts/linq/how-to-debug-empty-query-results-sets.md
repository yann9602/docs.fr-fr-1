---
title: "Guide pratique pour déboguer des ensembles de résultats de requête vides (C#) | Microsoft Docs"
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
ms.assetid: b569f0dc-425e-45a6-acbf-770fb761c981
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: afa7e63f4224a91c072c99d04a4851d2548166e5
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-debug-empty-query-results-sets-c"></a>Guide pratique pour déboguer des ensembles de résultats de requête vides (C#)
L'un des problèmes les plus courants lors de l'interrogation d'une arborescence XML est que si celle-ci possède un espace de noms par défaut, le développeur écrit parfois la requête comme si le code XML n'était dans aucun espace de noms.  
  
 Le premier ensemble d'exemples dans cette rubrique illustre le chargement de code XML dans un espace de noms par défaut et son interrogation incorrecte.  
  
 Le deuxième ensemble d'exemples illustre les corrections que vous devez apporter pour pouvoir interroger du code XML dans un espace de noms.  
  
 Pour plus d’informations, consultez [Utilisation des espaces de noms XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
## <a name="example"></a>Exemple  
 Cet exemple illustre la création de code XML dans un espace de noms et une requête qui retourne un jeu de résultats vide.  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements("Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
 Cet exemple génère le résultat suivant :  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a>Exemple  
 Cet exemple illustre la création de code XML dans un espace de noms et une requête codée correctement.  
  
 La solution consiste à déclarer et à initialiser un objet <xref:System.Xml.Linq.XNamespace>, et à l’utiliser lors de la spécification d’objets <xref:System.Xml.Linq.XName>. Dans ce cas, l’argument de la méthode <xref:System.Xml.Linq.XElement.Elements%2A> est un objet <xref:System.Xml.Linq.XName>.  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
 Cet exemple génère le résultat suivant :  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Requêtes de base (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
