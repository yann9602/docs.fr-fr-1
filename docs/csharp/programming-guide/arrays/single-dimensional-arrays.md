---
title: "Tableaux unidimensionnels (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "tableaux (C#), unidimensionnel"
  - "tableaux unidimensionnels (C#)"
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
caps.latest.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 18
---
# Tableaux unidimensionnels (Guide de programmation C#)
Vous pouvez déclarer un tableau unidimensionnel de cinq entiers comme indiqué dans l'exemple suivant :  
  
 [!code-cs[csProgGuideArrays#4](../../../csharp/programming-guide/arrays/codesnippet/csharp/single-dimensional-arrays_1.cs)]  
  
 Ce tableau contient les éléments de `array[0]` à `array[4]`.  L'opérateur [new](../../../csharp/language-reference/keywords/new.md) est utilisé pour créer le tableau et initialiser ses éléments à leurs valeurs par défaut.  Dans cet exemple, tous les éléments du tableau sont initialisés à zéro.  
  
 Un tableau qui stocke des éléments de type chaîne peut être déclaré de la même façon.  Par exemple :  
  
 [!code-cs[csProgGuideArrays#5](../../../csharp/programming-guide/arrays/codesnippet/csharp/single-dimensional-arrays_2.cs)]  
  
## Initialisation des tableaux  
 Il est possible d'initialiser un tableau lors de sa déclaration, auquel cas le spécificateur de rang n'est pas nécessaire, car il est déjà fourni par le nombre d'éléments dans la liste d'initialisation.  Par exemple :  
  
 [!code-cs[csProgGuideArrays#6](../../../csharp/programming-guide/arrays/codesnippet/csharp/single-dimensional-arrays_3.cs)]  
  
 Un tableau de chaînes peut être initialisé de la même manière.  Ce qui suit est la déclaration d'un tableau de chaînes où chaque élément du tableau est initialisé par un nom du jour de la semaine :  
  
 [!code-cs[csProgGuideArrays#7](../../../csharp/programming-guide/arrays/codesnippet/csharp/single-dimensional-arrays_4.cs)]  
  
 Lorsque vous initialisez un tableau lors de sa déclaration, vous pouvez utiliser les raccourcis suivants :  
  
 [!code-cs[csProgGuideArrays#8](../../../csharp/programming-guide/arrays/codesnippet/csharp/single-dimensional-arrays_5.cs)]  
  
 Il est possible de déclarer une variable de tableau sans initialisation, mais vous devez alors utiliser l'opérateur `new` quand vous assignez un tableau à cette variable.  Par exemple :  
  
 [!code-cs[csProgGuideArrays#9](../../../csharp/programming-guide/arrays/codesnippet/csharp/single-dimensional-arrays_6.cs)]  
  
 C\# 3.0 introduit les tableaux implicitement typés.  Pour plus d'informations, consultez [Tableaux implicitement typés](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).  
  
## Tableaux de types valeur et de types référence  
 Considérons la déclaration de tableau suivante :  
  
 [!code-cs[csProgGuideArrays#10](../../../csharp/programming-guide/arrays/codesnippet/csharp/single-dimensional-arrays_7.cs)]  
  
 Le résultat de cette instruction varie selon que `SomeType` est un type valeur ou un type référence.  S'il s'agit d'un type de valeur, l'instruction crée un tableau de 10 éléments, chacun ayant le type `SomeType`.  Si `SomeType` est un type référence, l'instruction crée un tableau de 10 éléments dont chacun est initialisé à une référence null.  
  
 Pour plus d'informations sur les types valeur et les types référence, consultez [Types](../../../csharp/language-reference/keywords/types.md).  
  
## Voir aussi  
 <xref:System.Array>   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Tableaux](../../../csharp/programming-guide/arrays/index.md)   
 [Tableaux multidimensionnels](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)   
 [Tableaux en escalier](../../../csharp/programming-guide/arrays/jagged-arrays.md)