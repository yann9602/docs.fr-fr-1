---
title: "Tableaux (guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "tableaux (C#)"
  - "langage C#, tableaux"
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
caps.latest.revision: 33
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 33
---
# Tableaux (guide de programmation C#)
Vous pouvez stocker plusieurs variables du même type dans une structure de données de tableau.  Vous déclarez un tableau en spécifiant le type de ses éléments.  
  
 `type[] arrayName;`  
  
 Les exemples suivants créent des tableaux unidimensionnels, multidimensionnels et en escalier :  
  
 [!code-cs[csProgGuideArrays#1](../../../csharp/programming-guide/arrays/codesnippet/csharp/index_1.cs)]  
  
## Vue d'ensemble des tableaux  
 Un tableau possède les propriétés suivantes :  
  
-   Un tableau peut être [Unidimensionnel](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md), [Multidimensionnel](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) ou [En escalier](../../../csharp/programming-guide/arrays/jagged-arrays.md).  
  
-   Le nombre de dimensions et la longueur de chaque dimension sont des valeurs établies lorsque l'instance de tableau est créée.  Ces valeurs ne peuvent pas être modifiées pendant la durée de vie de l'instance.  
  
-   Les valeurs par défaut des éléments de tableau numériques sont égales à zéro et les éléments de référence ont la valeur Null.  
  
-   Un tableau en escalier est un tableau de tableaux, et par conséquent ses éléments sont des types référence et sont initialisés à `null`.  
  
-   Les tableaux sont indexés à partir de zéro : un tableau avec `n` éléments est indexé de `0` à `n-1`.  
  
-   Les éléments du tableau peuvent être de n'importe quel autre type, y compris un type tableau.  
  
-   Les types de tableaux sont des [types référence](../../../csharp/language-reference/keywords/reference-types.md) dérivés du type de base abstrait <xref:System.Array>.  Puisque ce type implémente <xref:System.Collections.IEnumerable> et <xref:System.Collections.Generic.IEnumerable%601>, vous pouvez utiliser l'itération [foreach](../../../csharp/language-reference/keywords/foreach-in.md) sur tous les tableaux en C\#.  
  
## Rubriques connexes  
  
-   [Tableaux en tant qu'objets](../../../csharp/programming-guide/arrays/arrays-as-objects.md)  
  
-   [Utilisation de foreach avec des tableaux](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
-   [Passage de tableaux en tant qu'arguments](../../../csharp/programming-guide/arrays/passing-arrays-as-arguments.md)  
  
-   [Passage de tableaux à l'aide de paramètres ref et out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)  
  
-   [En savoir plus sur les variables](http://go.microsoft.com/fwlink/?LinkId=221230) dans [Débuter avec Visual C\# 2010](http://go.microsoft.com/fwlink/?LinkId=221214) \(en anglais\)  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Collections](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)   
 [Array Collection Type](http://msdn.microsoft.com/fr-fr/8a9964de-8941-47b1-a3cf-a01bc88db9e8)