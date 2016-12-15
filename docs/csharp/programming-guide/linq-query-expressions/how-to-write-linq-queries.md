---
title: "Comment&#160;: &#233;crire des requ&#234;tes LINQ en C# | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "requêtes (LINQ en C#), écrire"
  - "expressions de requête (LINQ en C#), écrire des requêtes"
  - "écriture de requêtes LINQ"
ms.assetid: 45e47fcc-cfa1-4b72-b161-d038ae87bd23
caps.latest.revision: 25
caps.handback.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Comment&#160;: &#233;crire des requ&#234;tes LINQ en C# #
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Cette rubrique présente les trois façons d'écrire une requête [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] en C\# :  
  
1.  Utilisez la syntaxe de requête.  
  
2.  Utilisez la syntaxe de méthode.  
  
3.  Utilisez une combinaison de syntaxe de requête et de syntaxe de méthode.  
  
 Les exemples suivants montrent des requêtes [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] simples en utilisant chaque approche répertoriée précédemment.  En général, la règle consiste à utiliser \(1\) dès que possible et à utiliser \(2\) et \(3\) dès que cela est nécessaire.  
  
> [!NOTE]
>  Ces requêtes fonctionnent sur les collections simples en mémoire ; toutefois, la syntaxe de base est identique à celle utilisée dans [!INCLUDE[vbtecdlinq](../../../csharp/includes/vbtecdlinq_md.md)] et [!INCLUDE[sqltecxlinq](../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].  
  
## Exemple  
  
## Syntaxe de requête  
 La méthode recommandée pour écrire la plupart des requêtes consiste à utiliser la *syntaxe de requête* pour créer des *expressions de requête*.  L'exemple suivant présente trois expressions de requête.  La première expression de requête montre comment filtrer ou restreindre des résultats en appliquant des conditions avec une clause `where`.  Tous les éléments de la séquence source dont la valeur est supérieure à 7 ou inférieure à 3 sont retournés.  La deuxième expression montre comment classer les résultats retournés.  La troisième expression montre comment regrouper des résultats en fonction d'une clé.  Cette requête retourne deux groupes en fonction de la première lettre du mot.  
  
 [!code-cs[csProgGuideLINQ#5](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-write-linq-queries_1.cs)]  
  
 Notez que le type des requêtes est <xref:System.Collections.Generic.IEnumerable%601>.  Toutes ces requêtes pourraient être écrites à l'aide de `var`, comme montré dans l'exemple suivant :  
  
 `var query = from num in numbers...`  
  
 Dans chacun des exemples précédents, les requêtes ne s'exécutent pas réellement tant vous n'avez pas itéré la variable de requête dans une instruction `foreach`.  Pour plus d'informations, consultez [Introduction to LINQ Queries \(C\#\)](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
## Exemple  
  
## Syntaxe de méthode  
 Certaines opérations de requête doivent être exprimées comme un appel de méthode.  Les plus répandues de ces méthodes retournent des valeurs numériques uniques, telles que <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>, etc.  Ces méthodes doivent toujours être appelées en dernier dans toutes les requêtes car elles ne représentent qu'une valeur unique et ne peuvent pas servir de source pour une opération de requête supplémentaire.  L'exemple suivant présente un appel de méthode dans une expression de requête :  
  
 [!code-cs[csProgGuideLINQ#6](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-write-linq-queries_2.cs)]  
  
## Exemple  
 Si la méthode a des paramètres, ceux\-ci sont fournis sous la forme d'une expression [lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md), comme dans l'exemple suivant :  
  
 [!code-cs[csProgGuideLINQ#7](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-write-linq-queries_3.cs)]  
  
 Dans les requêtes précédentes, seule la requête 4 s'exécute immédiatement.  Cela s'explique par le fait qu'elle retourne une valeur unique et non pas une collection <xref:System.Collections.Generic.IEnumerable%601> générique.  La méthode elle\-même doit utiliser `foreach` pour calculer sa valeur.  
  
 Chacune des requêtes précédentes peut être écrite en utilisant des types implicites avec [var](../../../csharp/language-reference/keywords/var.md), comme dans l'exemple suivant :  
  
 [!code-cs[csProgGuideLINQ#8](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-write-linq-queries_4.cs)]  
  
## Exemple  
  
## Syntaxe de méthode et de requête mixte  
 Cet exemple montre comment utiliser la syntaxe de méthode sur les résultats d'une clause de requête.  Encadrez simplement l'expression de requête entre parenthèses, puis appliquez l'opérateur point et appelez la méthode.  Dans l'exemple suivant, la requête 7 retourne les nombres dont la valeur est comprise entre 3 et 7.  Toutefois, il est généralement préférable d'utiliser une deuxième variable pour stocker le résultat de l'appel de méthode.  De cette manière, il est moins probable que la requête soit confondue avec les résultats de la requête.  
  
 [!code-cs[csProgGuideLINQ#9](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-write-linq-queries_5.cs)]  
  
 Comme la requête 7 retourne une valeur unique et non pas une collection, la requête s'exécute immédiatement.  
  
 La requête précédente peut être écrite en utilisant des types implicites avec `var`, comme suit :  
  
```  
var numCount = (from num in numbers...  
```  
  
 Elle peut être écrite dans la syntaxe de méthode comme suit :  
  
```  
var numCount = numbers.Where(n => n < 3 || n > 7).Count();  
```  
  
 Elle peut être écrite en utilisant des types explicites, comme suit :  
  
```  
int numCount = numbers.Where(n => n < 3 || n > 7).Count();  
```  
  
## Voir aussi  
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [Walkthrough: Writing Queries in C\#](../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)   
 [Expressions de requête \(LINQ\)](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [where, clause](../../../csharp/language-reference/keywords/where-clause.md)