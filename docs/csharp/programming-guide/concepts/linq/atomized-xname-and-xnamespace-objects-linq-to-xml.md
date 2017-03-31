---
title: "Objets XName et XNamespace atomisés (LINQ to XML) (C#) | Microsoft Docs"
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
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 89f5c2634e1deb196b121f2983b85f125927ae32
ms.lasthandoff: 03/13/2017


---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-c"></a>Objets XName et XNamespace atomisés (LINQ to XML) (C#)
Les objets <xref:System.Xml.Linq.XName> et <xref:System.Xml.Linq.XNamespace> sont *atomisés*. Autrement dit, s’ils contiennent le même nom qualifié, ils font référence au même objet. Ceci permet d'améliorer les performances des requêtes : lorsque vous comparez deux noms atomisés pour en vérifier l'égalité, le langage intermédiaire sous-jacent doit seulement déterminer si les deux références pointent vers le même objet. Le code sous-jacent ne doit pas effectuer de comparaisons de chaînes, ce qui prendrait beaucoup de temps.  
  
## <a name="atomization-semantics"></a>Sémantique d'atomisation  
 L’atomisation signifie que, si deux objets <xref:System.Xml.Linq.XName> ont le même nom local et sont dans le même espace de noms, ils partagent la même instance. De la même manière, si deux objets <xref:System.Xml.Linq.XNamespace> ont le même URI d’espace de noms, ils partagent la même instance.  
  
 Pour qu'une classe autorise les objets atomisés, le constructeur de cette classe doit être privé, et non public. En effet, si le constructeur était public, vous pourriez créer un objet non atomisé. Les classes <xref:System.Xml.Linq.XName> et <xref:System.Xml.Linq.XNamespace> implémentent un opérateur de conversion implicite pour convertir une chaîne en objet <xref:System.Xml.Linq.XName> ou <xref:System.Xml.Linq.XNamespace>. Telle est la manière dont vous obtenez une instance de ces objets. Vous ne pouvez pas obtenir une instance à l'aide d'un constructeur, car le constructeur est inaccessible.  
  
 <xref:System.Xml.Linq.XName> et <xref:System.Xml.Linq.XNamespace> implémentent également les opérateurs d’égalité et d’inégalité pour déterminer si les deux objets comparés sont des références à la même instance.  
  
## <a name="example"></a>Exemple  
 Le code suivant crée certains objets <xref:System.Xml.Linq.XElement> et montre que des noms identiques partagent la même instance.  
  
```csharp  
XElement r1 = new XElement("Root", "data1");  
XElement r2 = XElement.Parse("<Root>data2</Root>");  
  
if ((object)r1.Name == (object)r2.Name)  
    Console.WriteLine("r1 and r2 have names that refer to the same instance.");  
else  
    Console.WriteLine("Different");  
  
XName n = "Root";  
  
if ((object)n == (object)r1.Name)  
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.");  
else  
    Console.WriteLine("Different");  
```  
  
 Cet exemple génère la sortie suivante :  
  
```  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 Comme indiqué précédemment, l’avantage des objets atomisés est que, lorsque vous utilisez une méthode d’axe qui accepte un <xref:System.Xml.Linq.XName> comme paramètre, cette méthode d’axe doit seulement déterminer que deux noms font référence à la même instance pour sélectionner les éléments voulus.  
  
 L’exemple suivant passe un <xref:System.Xml.Linq.XName> à l’appel de méthode <xref:System.Xml.Linq.XContainer.Descendants%2A>, qui a ensuite de meilleures performances grâce au modèle d’atomisation.  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("C1", 1),  
    new XElement("Z1",  
        new XElement("C1", 2),  
        new XElement("C1", 1)  
    )  
);  
  
var query = from e in root.Descendants("C1")  
            where (int)e == 1  
            select e;  
  
foreach (var z in query)  
    Console.WriteLine(z);  
```  
  
 Cet exemple génère la sortie suivante :  
  
```  
<C1>1</C1>  
<C1>1</C1>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Performance (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
