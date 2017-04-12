---
title: "Performances des requêtes chaînées (LINQ to XML) (Visual Basic) | Documents Microsoft"
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
ms.assetid: 589f2adc-69f9-404d-b9d6-4c28dabea7f7
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: dd5b63f255107c5864108cfbb87bef6e53a971a0
ms.lasthandoff: 03/13/2017


---
# <a name="performance-of-chained-queries-linq-to-xml-visual-basic"></a>Performances des requêtes chaînées (LINQ to XML) (Visual Basic)
L'un des principaux avantages de LINQ (et LINQ to XML) est que les requêtes chaînées peuvent offrir la même performance qu'une requête unique plus grande et plus complexe.  
  
 Une requête chaînée est une requête qui utilise une autre requête comme source. Par exemple, dans le code simple suivant, `query2` utilise `query1` comme source :  
  
```vb  
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))  
  
Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x  
  
Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e  
  
For Each i As var In query2  
    Console.WriteLine("{0}", CInt(i))  
Next  
  
```  
  
 Cet exemple génère la sortie suivante :  
  
```  
4  
```  
  
 Cette requête chaînée offre le même profil de performance que l'itération sur une liste liée.  
  
-   Le <xref:System.Xml.Linq.XContainer.Elements%2A>axe possède essentiellement la même performance qu’une itération d’une liste liée.</xref:System.Xml.Linq.XContainer.Elements%2A> <xref:System.Xml.Linq.XContainer.Elements%2A>est implémenté comme un itérateur avec exécution différée.</xref:System.Xml.Linq.XContainer.Elements%2A> Cela signifie qu'en plus de l'itération sur la liste liée, il effectue certaines tâches comme l'allocation de l'objet itérateur et le suivi de l'état d'exécution. Ces tâches peuvent être divisées en deux catégories : les tâches effectuées lors de la configuration de l'itérateur et les tâches effectuées à chaque itération. Les tâches de configuration représentent une part réduite et fixe du travail, tandis que les tâches effectuées à chaque itération sont proportionnelles au nombre d'éléments de la collection source.  
  
-   Dans `query1`, le `Where` clause indique que la requête doit appeler le <xref:System.Linq.Enumerable.Where%2A>méthode.</xref:System.Linq.Enumerable.Where%2A> Cette méthode est également implémentée en tant qu'itérateur. Les tâches de configuration se composent de l'instanciation du délégué qui fera référence à l'expression, en plus de la configuration normale d'un itérateur. A chaque itération, le délégué est appelé pour exécuter le prédicat. Les tâches de configuration et les tâches effectuées à chaque itération sont similaires aux tâches effectuées lors de l'itération sur l'axe.  
  
-   Dans `query1`, la clause select indique la requête doit appeler le <xref:System.Linq.Enumerable.Select%2A>méthode.</xref:System.Linq.Enumerable.Select%2A> Cette méthode a le même profil de performances que le <xref:System.Linq.Enumerable.Where%2A>méthode.</xref:System.Linq.Enumerable.Where%2A>  
  
-   Dans `query2`, la clause `Where` et la `Select` clause ont toutes deux le même profil de performance que dans `query1`.  
  
 L'itération sur `query2` est donc directement proportionnelle au nombre d'éléments de la source de la première requête, en d'autres termes, elle suit un algorithme linéaire.  
  
## <a name="see-also"></a>Voir aussi  
 [Performances (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
