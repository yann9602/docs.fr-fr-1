---
title: "Guide pratique pour interroger LINQ to XML à l’aide de XPath (C#) | Microsoft Docs"
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
ms.assetid: ee5af263-4ab1-45e5-b792-33a3221b426d
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 86d02a119423fe33731f0049ca232dde7509936d
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-query-linq-to-xml-using-xpath-c"></a>Guide pratique pour interroger LINQ to XML à l’aide de XPath (C#)
Cette rubrique présente les méthodes d’extension qui vous permettent d’interroger une arborescence XML à l’aide de XPath. Pour plus d’informations sur l’utilisation de ces méthodes d’extension, consultez <xref:System.Xml.XPath.Extensions?displayProperty=fullName>.  
  
 À moins que vous n’ayez une raison spécifique pour interroger à l’aide de XPath, par exemple en cas d’utilisation intensive de code hérité, l’utilisation de XPath avec LINQ to XML n’est pas recommandée. Les requêtes XPath présentent des performances inférieures à celles des requêtes [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée une petite arborescence XML et utilise <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> pour sélectionner un ensemble d’éléments.  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", 1),  
    new XElement("Child1", 2),  
    new XElement("Child1", 3),  
    new XElement("Child2", 4),  
    new XElement("Child2", 5),  
    new XElement("Child2", 6)  
);  
IEnumerable<XElement> list = root.XPathSelectElements("./Child2");  
foreach (XElement el in list)  
    Console.WriteLine(el);  
```  
  
 Cet exemple génère la sortie suivante :  
  
```  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Techniques de requêtes avancées (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
