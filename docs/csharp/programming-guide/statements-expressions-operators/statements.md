---
title: "Instructions (Guide de programmation C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- statements [C#], about statements
- C# language, statements
ms.assetid: 901bcde7-87de-4e15-833c-f9cfd40c8ce3
caps.latest.revision: 28
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: cfbd607f614bd8d287dd33f08dd47b12fa651ced
ms.lasthandoff: 03/13/2017

---
# <a name="statements-c-programming-guide"></a>Instructions (Guide de programmation C#)
Les actions qu’un programme effectue sont exprimées dans les instructions. Les actions courantes incluent la déclaration de variables, l’assignation de valeurs, l’appel de méthodes, l’exécution de boucles dans les collections et la création de branches sur des blocs de code, selon une condition donnée. L’ordre dans lequel les instructions sont exécutées dans un programme est appelé le flux de contrôle ou le flux d’exécution. Le flux de contrôle peut varier chaque fois qu’un programme est exécuté, selon la manière dont le programme réagit à l’entrée qu’il reçoit au moment de l’exécution.  
  
 Une instruction peut comporter une seule ligne de code terminée par un point-virgule ou une série d’instructions d’une ligne dans un bloc. Un bloc d’instructions est placé entre accolades {} et peut contenir des blocs imbriqués. Le code suivant illustre deux exemples d’instructions d’une ligne, et un bloc d’instructions multiligne :  
  
 [!code-cs[csProgGuideStatements#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_1.cs)]  
  
## <a name="types-of-statements"></a>Types d’instructions  
 Le tableau suivant répertorie les différents types d’instructions en C# et leurs mots clés associés, avec des liens vers des rubriques contenant plus d’informations :  
  
|Catégorie|Mots clés C# / Remarques|  
|--------------|---------------------------|  
|Instructions de déclaration|Une instruction de déclaration introduit une nouvelle variable ou constante. Une déclaration de variable peut éventuellement assigner une valeur à la variable. Dans une déclaration de constante, l’assignation est obligatoire.<br /><br /> [!code-cs[csProgGuideStatements#23](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_2.cs)]|  
|Instructions d’expression|Les instructions d’expression qui calculent une valeur doivent stocker la valeur dans une variable.<br /><br /> [!code-cs[csProgGuideStatements#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_3.cs)]|  
|[Instructions de sélection](../../../csharp/language-reference/keywords/selection-statements.md)|Les instructions de sélection permettent de créer des branches vers différentes sections de code, selon une ou plusieurs conditions spécifiées. Pour plus d’informations, consultez les rubriques suivantes :<br /><br /> [if](../../../csharp/language-reference/keywords/if-else.md), [else](../../../csharp/language-reference/keywords/if-else.md), [switch](../../../csharp/language-reference/keywords/switch.md), [case](../../../csharp/language-reference/keywords/switch.md)|  
|[Instructions d’itération](../../../csharp/language-reference/keywords/iteration-statements.md)|Les instructions d’itération permettent d’exécuter une boucle dans des collections telles que des tableaux, ou d’effectuer à plusieurs reprises le même jeu d’instructions jusqu’à ce qu’une condition spécifiée soit remplie. Pour plus d’informations, consultez les rubriques suivantes :<br /><br /> [do](../../../csharp/language-reference/keywords/do.md), [for](../../../csharp/language-reference/keywords/for.md), [foreach](../../../csharp/language-reference/keywords/foreach-in.md), [in](../../../csharp/language-reference/keywords/foreach-in.md), [while](../../../csharp/language-reference/keywords/while.md)|  
|[Instructions de saut](../../../csharp/language-reference/keywords/jump-statements.md)|Les instructions de saut transfèrent le contrôle vers une autre section de code. Pour plus d’informations, consultez les rubriques suivantes :<br /><br /> [break](../../../csharp/language-reference/keywords/break.md), [continue](../../../csharp/language-reference/keywords/continue.md), [default](../../../csharp/language-reference/keywords/switch.md), [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), [yield](../../../csharp/language-reference/keywords/yield.md)|  
|[Instructions de gestion des exceptions](../../../csharp/language-reference/keywords/exception-handling-statements.md)|Les instructions de gestion des exceptions permettent de récupérer normalement en cas de conditions exceptionnelles au moment de l’exécution. Pour plus d’informations, consultez les rubriques suivantes :<br /><br /> [throw](../../../csharp/language-reference/keywords/throw.md), [try-catch](../../../csharp/language-reference/keywords/try-catch.md), [try-finally](../../../csharp/language-reference/keywords/try-finally.md), [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)|  
|[Checked et unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)|Les instructions checked et unchecked vous permettent de spécifier si les opérations numériques sont autorisées à provoquer un dépassement de capacité lorsque le résultat est stocké dans une variable trop petite pour contenir la valeur résultante. Pour plus d’informations, consultez [checked](../../../csharp/language-reference/keywords/checked.md) et [unchecked](../../../csharp/language-reference/keywords/unchecked.md).|  
Instruction `await`|Si vous marquez une méthode avec le modificateur [async](../../../csharp/language-reference/keywords/async.md), vous pouvez utiliser l’opérateur [await](../../../csharp/language-reference/keywords/await.md) dans cette méthode. Quand le contrôle atteint une expression `await` dans la méthode async, il retourne à l’appelant, et la progression dans la méthode est interrompue jusqu’à ce que la tâche attendue soit terminée. Quand la tâche est terminée, l'exécution peut reprendre dans la méthode.<br /><br /> Pour obtenir un exemple simple, consultez la section « Méthodes async » de [Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md). Pour plus d’informations, consultez [Programmation asynchrone avec async et await](../../../csharp/programming-guide/concepts/async/index.md).|  
|Instruction `yield return`|Un itérateur exécute une itération personnalisée sur une collection, comme une liste ou un tableau. Un itérateur utilise l’instruction [yield return](../../../csharp/language-reference/keywords/yield.md) pour retourner chaque élément un par un. Quand une instruction `yield return` est atteinte, l’emplacement actuel dans le code est mémorisé. L'exécution redémarre à partir de cet emplacement au prochain appel de l'itérateur.<br /><br /> Pour plus d’informations, consultez [Itérateurs](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).|  
|Instruction `fixed`|L’instruction fixed empêche le récupérateur de mémoire de déplacer une variable mobile. Pour plus d’informations, consultez [fixed](../../../csharp/language-reference/keywords/fixed-statement.md).|  
|Instruction `lock`|L’instruction lock permet de limiter l’accès aux blocs de code à un seul thread à la fois. Pour plus d’informations, consultez [lock](../../../csharp/language-reference/keywords/lock-statement.md).|  
|Instructions étiquetées|Vous pouvez donner une étiquette à une instruction, puis utiliser le mot clé [goto](../../../csharp/language-reference/keywords/goto.md) pour sauter jusqu’à l’instruction étiquetée. (Examinez l’exemple de la ligne suivante.)|  
|Instruction vide|L’instruction vide se compose seulement d’un point-virgule. Elle ne fait rien et peut être utilisée à un emplacement où une instruction est requise alors qu’aucune action ne doit être effectuée. Les exemples suivants illustrent deux utilisations d’une instruction vide :<br /><br /> [!code-cs[csProgGuideStatements#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_4.cs)]|  
  
## <a name="embedded-statements"></a>Instructions incorporées  
 Certaines instructions, y compris [do](../../../csharp/language-reference/keywords/do.md), [while](../../../csharp/language-reference/keywords/while.md), [for](../../../csharp/language-reference/keywords/for.md) et [foreach](../../../csharp/language-reference/keywords/foreach-in.md), sont toujours suivies d’une instruction incorporée. Cette instruction incorporée peut être une instruction unique ou plusieurs instructions placées entre accolades {} dans un bloc d’instructions. Même les instructions incorporées d’une ligne peuvent être placées entre accolades {}, comme illustré dans l’exemple suivant :  
  
 [!code-cs[csProgGuideStatements#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_5.cs)]  
  
 Une instruction incorporée qui n’est pas placée entre accolades {} ne peut pas être une instruction de déclaration ni une instruction étiquetée. Ceci est illustré dans l'exemple suivant :  
  
 [!code-cs[csProgGuideStatements#27](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_6.cs)]  
  
 Placez l’instruction incorporée dans un bloc pour corriger l’erreur :  
  
 [!code-cs[csProgGuideStatements#28](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_7.cs)]  
  
## <a name="nested-statement-blocks"></a>Blocs d’instructions imbriqués  
 Les blocs d’instructions peuvent être imbriqués, comme illustré dans le code suivant :  
  
 [!code-cs[csProgGuideStatements#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_8.cs)]  
  
## <a name="unreachable-statements"></a>Instructions inaccessibles  
 Si le compilateur détermine que le flux de contrôle ne peut jamais atteindre une instruction particulière, il génère l’avertissement CS0162, comme illustré dans l’exemple suivant :  
  
 [!code-cs[csProgGuideStatements#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_9.cs)]  
  
## <a name="related-sections"></a>Rubriques connexes  
  
-   [Mots clés d’instructions](../../../csharp/language-reference/keywords/statement-keywords.md)  
  
-   [Expressions](../../../csharp/programming-guide/statements-expressions-operators/expressions.md)  
  
-   [Opérateurs](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)
