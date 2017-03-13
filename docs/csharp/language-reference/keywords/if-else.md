---
title: "if-else (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "if_CSharpKeyword"
  - "else"
  - "else_CSharpKeyword"
  - "if"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "else (mot clé C#)"
  - "if (mot clé C#)"
ms.assetid: d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2
caps.latest.revision: 32
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 32
---
# if-else (r&#233;f&#233;rence C#)
Une instruction `if` identifie l’instruction à exécuter en fonction de la valeur d’une expression `Boolean`. Dans l’exemple suivant, la variable `Boolean``result` est définie sur `true` puis archivé dans l’instruction `if`. Le résultat est `The condition is true`.  
  
 [!code-cs[csrefKeywordsSelection#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_1.cs)]  
  
 Vous pouvez exécuter les exemples de cette rubrique en les plaçant dans la méthode `Main` d’une application console.  
  
 En C\#, une instruction `if` peut prendre deux formes, comme le montre l’exemple suivant.  
  
```c#  
  
// if-else statement if (condition) { then-statement; } else { else-statement; } // Next statement in the program. // if statement without an else if (condition) { then-statement; } // Next statement in the program.  
```  
  
 Dans une instruction `if-else`, si `condition` a la valeur true, `then-statement` s’exécute. Si `condition` a la valeur false, `else-statement` s’exécute. Sachant que `condition` ne peut pas avoir simultanément les valeurs true et false, `then-statement` et `else-statement` d’une instruction `if-else` ne peuvent jamais s’exécuter. Une fois que `then-statement` ou `else-statement` s’est exécuté, le contrôle est transféré à l’instruction suivante après l’instruction `if`.  
  
 Dans une instruction `if` qui n’inclut pas d’instruction `else`, si `condition` a la valeur true, `then-statement` s’exécute. Si `condition` a la valeur false, le contrôle est transféré à l’instruction suivante après l’instruction `if`.  
  
 `then-statement` et `else-statement` peuvent tous deux être constitués d’une ou plusieurs instructions placées entre accolades \(`{}`\). Pour une seule instruction, les accolades sont facultatives, mais recommandées.  
  
 La ou les instructions contenues dans `then-statement` et `else-statement` peuvent être de n’importe quel type, y compris une autre instruction `if` imbriquée à l’intérieur de l’instruction `if` d’origine. Dans les instructions `if` imbriquées, chaque clause `else` appartient à la dernière instruction `if` qui n’a pas d’instruction `else` correspondante. Dans l’exemple suivant, `Result1` s’affiche si `m > 10` et `n > 20` ont tous deux la valeur true. Si `m > 10` a la valeur true, mais que `n > 20` a la valeur false, `Result2` s’affiche.  
  
 [!code-cs[csrefKeywordsSelection#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_2.cs)]  
  
 Si vous préférez que `Result2` s’affiche quand `(m > 10)` a la valeur false, vous pouvez spécifier cette association au moyen d’accolades pour établir le début et la fin de l’instruction `if` imbriquée, comme le montre l’exemple suivant.  
  
 [!code-cs[csrefKeywordsSelection#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_3.cs)]  
  
 `Result2` s’affiche si la condition `(m > 10)` a la valeur false.  
  
## Exemple  
 Dans l’exemple suivant, vous entrez un caractère au clavier et le programme utilise une instruction `if` imbriquée pour déterminer si le caractère d’entrée est un caractère alphabétique. Si le caractère d’entrée est un caractère alphabétique, le programme vérifie si c’est une minuscule ou une majuscule. Un message s’affiche dans chaque cas.  
  
 [!code-cs[csrefKeywordsSelection#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_4.cs)]  
  
## Exemple  
 Vous pouvez aussi imbriquer une instruction `if` à l’intérieur d’un bloc « else », comme le montre l’extrait de code suivant. L’exemple imbrique des instructions `if` à l’intérieur de deux blocs « else » et d’un bloc « then ». Les commentaires précisent les conditions qui sont vraies \(true\) et celles qui sont fausses \(false\) dans chaque bloc.  
  
 [!code-cs[csrefKeywordsSelection#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_5.cs)]  
  
## Exemple  
 L’exemple suivant détermine si un caractère d’entrée est une lettre minuscule, une lettre majuscule ou un nombre. Si ces trois conditions ont la valeur false, le caractère n’est pas un caractère alphanumérique. L’exemple affiche un message dans chaque cas.  
  
 [!code-cs[csrefKeywordsSelection#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_6.cs)]  
  
 De la même manière que le bloc « else » ou le bloc « then » peuvent contenir n’importe quelle instruction valide, vous pouvez utiliser n’importe quelle expression booléenne valide pour la condition. Vous pouvez utiliser des opérateurs logiques tels que [&&](../../../csharp/language-reference/operators/conditional-and-operator.md), [&](../../../csharp/language-reference/operators/and-operator.md), [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md), [&#124;](../../../csharp/language-reference/operators/or-operator.md) et [\!](../../../csharp/language-reference/operators/logical-negation-operator.md) pour former des conditions composées. Le code suivant présente des exemples.  
  
```c#  
// NOT bool result = true; if (!result) { Console.WriteLine("The condition is true (result is false)."); } else { Console.WriteLine("The condition is false (result is true)."); } // Short-circuit AND int m = 9; int n = 7; int p = 5; if (m >= n && m >= p) { Console.WriteLine("Nothing is larger than m."); } // AND and NOT if (m >= n && !(p > m)) { Console.WriteLine("Nothing is larger than m."); } // Short-circuit OR if (m > n || m > p) { Console.WriteLine("m isn't the smallest."); } // NOT and OR m = 4; if (!(m >= n || m >= p)) { Console.WriteLine("Now m is the smallest."); } // Output: // The condition is false (result is true). // Nothing is larger than m. // Nothing is larger than m. // m isn't the smallest. // Now m is the smallest.  
```  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [?:, opérateur](../../../csharp/language-reference/operators/conditional-operator.md)   
 [if\-else, instruction \(C\+\+\)](/visual-cpp/cpp/if-else-statement-cpp)   
 [switch](../../../csharp/language-reference/keywords/switch.md)