---
title: "Passage de param&#232;tres de type r&#233;f&#233;rence (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "paramètres de méthode (C#), types référence"
  - "paramètres (C#), référence"
ms.assetid: 9e6eb65c-942e-48ab-920a-b7ba9df4ea20
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# Passage de param&#232;tres de type r&#233;f&#233;rence (Guide de programmation C#)
Une variable de [type référence](../../../csharp/language-reference/keywords/reference-types.md) ne contient pas directement les données, mais contient une référence aux données.  Lorsque vous passez un paramètre de type référence par valeur, il est possible de modifier les données sur lesquelles pointe la référence, comme par exemple la valeur d'un membre de classe.  Toutefois, vous ne pouvez pas modifier la valeur de la référence elle\-même. Cela signifie que vous ne pouvez pas utiliser la même référence pour allouer de la mémoire pour une nouvelle classe et la faire persister en dehors du bloc.  Pour cela, passez le paramètre en utilisant le mot clé [ref](../../../csharp/language-reference/keywords/ref.md) ou [out](../../../csharp/language-reference/keywords/out.md).  Par souci de simplicité, les exemples qui suivent utilisent `ref`.  
  
## Passage de types référence par valeur  
 Cet exemple illustre le passage d'un paramètre de type référence, `arr`, par valeur à une méthode, `Change`.  Comme le paramètre est une référence de `arr`, il est possible de modifier les valeurs des éléments du tableau.  Toutefois, la tentative de réassignation du paramètre à un emplacement de mémoire différent s'effectue uniquement au sein de la méthode et n'affecte pas la variable d'origine, `arr`.  
  
 [!code-cs[csProgGuideParameters#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_1.cs)]  
  
 Dans l'exemple précédent, le tableau, `arr`, de type référence, est passé à la méthode sans le paramètre `ref`.  Dans ce cas, une copie de la référence, qui pointe sur `arr`, est passée à la méthode.  La sortie montre qu'il est possible que la méthode modifie le contenu d'un élément du tableau \(dans ce cas, de `1` à `888`\).  Toutefois, l'allocation d'une nouvelle partie de la mémoire à l'aide de l'opérateur [new](../../../csharp/language-reference/keywords/new.md) au sein de la méthode `Change` fait de la référence `pArray` de la variable un nouveau tableau.  De cette manière, aucune modification ultérieure n'affectera le tableau d'origine, `arr`, qui est créé au sein de `Main`.  En fait, deux tableaux sont créés dans cet exemple, l'un au sein de `Main` et l'autre au sein de la méthode `Change`.  
  
## Passage de types référence par référence  
 L'exemple suivant est identique à l'exemple précédent, mais que le mot clé d' `ref` est ajouté à l'en\-tête et à l'appel de méthode.  Toutes les modifications qui interviennent dans l'impact de méthode la variable d'origine dans le programme appelant.  
  
 [!code-cs[csProgGuideParameters#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_2.cs)]  
  
 Toutes les modifications qui interviennent au sein de la méthode affectent le tableau d'origine dans `Main`.  En fait, le tableau d'origine est réalloué à l'aide de l'opérateur `new`.  En conséquence, après l'appel de la méthode `Change`, toute référence à `arr` pointe sur le tableau à cinq éléments, créé dans la méthode `Change`.  
  
## Permutation de deux chaînes  
 La permutation de chaînes est un bon exemple de passage de paramètres de type référence par référence.  Dans cet exemple, deux chaînes, `str1` et `str2`, sont initialisées dans `Main` et passées à la méthode `SwapStrings` en tant que paramètres modifiés par le mot clé `ref`.  Les deux chaînes sont permutées au sein de la méthode, ainsi que dans `Main`.  
  
 [!code-cs[csProgGuideParameters#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_3.cs)]  
  
 Dans cet exemple, les paramètres doivent être passés par référence pour affecter les variables dans le programme appelant.  Si vous supprimez le mot clé `ref` à la fois dans l'en\-tête et dans l'appel de la méthode, aucune modification n'intervient dans le programme appelant.  
  
 Pour plus d'informations sur les chaînes, consultez [chaîne](../../../csharp/language-reference/keywords/string.md).  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Passage de paramètres](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)   
 [Passage de tableaux à l'aide de paramètres ref et out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)   
 [ref](../../../csharp/language-reference/keywords/ref.md)   
 [Types référence](../../../csharp/language-reference/keywords/reference-types.md)