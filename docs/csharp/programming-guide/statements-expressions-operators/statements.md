---
title: "Instructions (Guide de programmation C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "langage C#, instructions"
  - "instructions (C#), à propos des instructions"
ms.assetid: 901bcde7-87de-4e15-833c-f9cfd40c8ce3
caps.latest.revision: 28
caps.handback.revision: 28
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Instructions (Guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Les actions effectuées par un programme sont exprimées dans des instructions.  Les actions courantes incluent la déclaration de variables, l'attribution de valeurs, l'appel de méthodes, l'exécution de boucle à travers des collections et le branchement à un autre bloc de code, en fonction d'une condition donnée.  L'ordre dans lequel les instructions sont exécutées dans un programme est appelé flux de contrôle ou flux d'exécution.  Le flux de contrôle peut varier chaque fois qu'un programme est exécuté, selon la façon dont le programme réagit à l'entrée qu'il reçoit au moment de l'exécution.  
  
 Une instruction peut être constituée d'une ligne unique de code qui se termine par un point\-virgule, ou d'une série d'instructions sur une ligne dans un bloc.  Un bloc d'instructions est placé entre accolades {} et peut contenir des blocs imbriqués.  Le code suivant illustre deux exemples d'instructions sur une ligne et un bloc d'instructions multiligne :  
  
 [!code-cs[csProgGuideStatements#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_1.cs)]  
  
## Types d'instructions  
 Le tableau suivant répertorie les différents types d'instructions en C\# et leurs mots clés associés, avec des liens vers des rubriques proposant davantage d'informations :  
  
|Catégorie|Mots clés C\# \/ remarques|  
|---------------|--------------------------------|  
|Instructions de déclaration|Une instruction de déclaration introduit une nouvelle variable ou constante.  Une déclaration de variable peut éventuellement assigner une valeur à la variable.  Dans une déclaration de constante, l'assignation est requise.<br /><br /> [!code-cs[csProgGuideStatements#23](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_2.cs)]|  
|Instructions d'expression|Les instructions d'expression qui calculent une valeur doivent stocker la valeur dans une variable.<br /><br /> [!code-cs[csProgGuideStatements#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_3.cs)]|  
|[Instructions de sélection](../../../csharp/language-reference/keywords/selection-statements.md)|Les instructions de sélection permettent de se brancher à différentes sections de code, en fonction d'une ou plusieurs conditions spécifiées.  Pour plus d’informations, voir les rubriques suivantes :<br /><br /> [if](../../../csharp/language-reference/keywords/if-else.md), [else](../../../csharp/language-reference/keywords/if-else.md), [switch](../../../csharp/language-reference/keywords/switch.md), [case](../../../csharp/language-reference/keywords/switch.md)|  
|[Instructions d'itération](../../../csharp/language-reference/keywords/iteration-statements.md)|Les instructions d'itération permettent d'effectuer une boucle à travers des collections telles que des tableaux, ou d'exécuter à plusieurs reprises le même jeu d'instructions jusqu'à ce qu'une condition spécifiée soit remplie.  Pour plus d’informations, voir les rubriques suivantes :<br /><br /> [do](../../../csharp/language-reference/keywords/do.md), [for](../../../csharp/language-reference/keywords/for.md), [foreach](../../../csharp/language-reference/keywords/foreach-in.md), [in](../../../csharp/language-reference/keywords/foreach-in.md), [while](../../../csharp/language-reference/keywords/while.md)|  
|[Instructions de saut](../../../csharp/language-reference/keywords/jump-statements.md)|Les instructions de saut transfèrent le contrôle à une autre section de code.  Pour plus d’informations, voir les rubriques suivantes :<br /><br /> [break](../../../csharp/language-reference/keywords/break.md), [continue](../../../csharp/language-reference/keywords/continue.md), [default](../../../csharp/language-reference/keywords/switch.md), [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), [yield](../../../csharp/language-reference/keywords/yield.md)|  
|[Instructions de gestion des exceptions](../../../csharp/language-reference/keywords/exception-handling-statements.md)|Les instructions de gestion des exceptions vous permettent d'effectuer une récupération « propre » suite à des conditions d'exception qui se produisent au moment de l'exécution.  Pour plus d’informations, voir les rubriques suivantes :<br /><br /> [throw](../../../csharp/language-reference/keywords/throw.md), [try\-catch](../../../csharp/language-reference/keywords/try-catch.md), [try\-finally](../../../csharp/language-reference/keywords/try-finally.md), [try\-catch\-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)|  
|[Checked et unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)|Les instructions checked et unchecked vous permettent de spécifier si les opérations numériques sont autorisées à provoquer un dépassement de capacité lorsque le résultat est stocké dans une variable qui est trop petite pour contenir la valeur résultante.  Pour plus d'informations, consultez [checked](../../../csharp/language-reference/keywords/checked.md) et [unchecked](../../../csharp/language-reference/keywords/unchecked.md).|  
|Instruction `await`|Si vous marquez une méthode avec le modificateur d' [async](../../../csharp/language-reference/keywords/async.md) , vous pouvez utiliser l'opérateur d' [attendez](../../../csharp/language-reference/keywords/await.md) dans la méthode.  Lorsque le contrôle atteint une expression d' `await` dans la méthode async, le contrôle retourne à l'appelant, et la progression de la méthode est interrompue jusqu'à ce que la tâche se termine attendue.  Lorsque la tâche est terminée, l'opération peut continuer dans la méthode.<br /><br /> Pour obtenir un exemple simple, consultez la section « méthodes Async » de [Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md).  Pour plus d’informations, consultez [Programmation asynchrone avec Async et Await](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md).|  
|Instruction `yield return`|Un itérateur effectue une itération au sein d'une collection, telle qu'une liste ou un tableau.  Un itérateur utilise l'instruction de [retour yield](../../../csharp/language-reference/keywords/yield.md) pour retourner les éléments un par un.  Lorsqu'une instruction d' `yield return` est atteinte, la position actuelle dans le code est retrouvée.  L'exécution est redémarrée de cet emplacement lorsque l'itérateur s'agit de la prochaine fois.<br /><br /> Pour plus d’informations, consultez [Itérateurs](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md).|  
|Instruction `fixed`|L'instruction fixed empêche le Garbage Collector de déplacer une variable mobile.  Pour plus d'informations, consultez [fixed](../../../csharp/language-reference/keywords/fixed-statement.md).|  
|Instruction `lock`|L'instruction lock vous permet de limiter l'accès aux blocs de code à un seul thread à la fois.  Pour plus d'informations, consultez [lock](../../../csharp/language-reference/keywords/lock-statement.md).|  
|Instructions étiquetées|Vous pouvez donner une étiquette à une instruction puis utiliser le mot clé [goto](../../../csharp/language-reference/keywords/goto.md) pour accéder à l'instruction étiquetée.  \(Consultez l'exemple sur la ligne suivante.\)|  
|Instruction vide|L'instruction vide se compose d'un point\-virgule unique.  Elle ne fait rien et peut être utilisée à des emplacements où une instruction est requise mais aucune action ne doit être exécutée.  Les exemples suivants illustrent deux utilisations d'une instruction vide :<br /><br /> [!code-cs[csProgGuideStatements#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_4.cs)]|  
  
## Instructions incorporées  
 Certaines instructions, y compris [do](../../../csharp/language-reference/keywords/do.md), [while](../../../csharp/language-reference/keywords/while.md), [for](../../../csharp/language-reference/keywords/for.md) et [foreach](../../../csharp/language-reference/keywords/foreach-in.md), sont toujours suivies d'une instruction incorporée.  Cette instruction incorporée peut être une instruction unique ou plusieurs instructions placées entre accolades {} dans un bloc d'instructions.  Même les instructions incorporées sur une ligne peuvent être placées entre accolades {}, comme illustré dans l'exemple suivant :  
  
 [!code-cs[csProgGuideStatements#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_5.cs)]  
  
 Une instruction incorporée qui n'est pas placée entre accolades {} ne peut pas être une instruction de déclaration ni une instruction étiquetée.  Ceci est démontré dans l'exemple suivant :  
  
 [!code-cs[csProgGuideStatements#27](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_6.cs)]  
  
 Placez l'instruction incorporée dans un bloc pour résoudre l'erreur :  
  
 [!code-cs[csProgGuideStatements#28](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_7.cs)]  
  
## Blocs d'instructions imbriqués  
 Les blocs d'instructions peuvent être imbriqués, comme illustré dans le code suivant :  
  
 [!code-cs[csProgGuideStatements#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_8.cs)]  
  
## Instructions inaccessibles  
 Si le compilateur détermine que le flux de contrôle ne peut jamais atteindre une instruction particulière, il génère l'avertissement CS0162, comme illustré dans l'exemple suivant :  
  
 [!code-cs[csProgGuideStatements#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_9.cs)]  
  
## Rubriques connexes  
  
-   [Mots clés d'instructions](../../../csharp/language-reference/keywords/statement-keywords.md)  
  
-   [Expressions](../../../csharp/programming-guide/statements-expressions-operators/expressions.md)  
  
-   [Opérateurs](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)