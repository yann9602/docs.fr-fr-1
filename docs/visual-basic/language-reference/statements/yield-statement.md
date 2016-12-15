---
title: "yield, instruction (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Yield"
helpviewer_keywords: 
  - "itérateurs, instruction Yield [Visual Basic]"
  - "itérateurs (Visual Basic)"
  - "Instruction yield (Visual Basic)"
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# yield, instruction (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Envoie le premier élément d'une collection à une instruction d' `For Each...Next` .  
  
## Syntaxe  
  
```  
Yield expression  
```  
  
#### Paramètres  
  
|||  
|-|-|  
|Terme|Définition|  
|`expression`|Requis.  Une expression qui est implicitement convertible au type de la fonction d'itérateur ou de l'utilisateur d' `Get` qui contient l'instruction d' `Yield` .|  
  
## Notes  
 L'instruction d' `Yield` retourne un élément d'une collection à la fois.  L'instruction d' `Yield` est incluse dans une fonction d'itérateur ou un utilisateur d' `Get`, qui exécutent des itérations personnalisées sur une collection.  
  
 Vous consommez une fonction d'itérateur à l'aide de [For Each...Next, instruction](../../../visual-basic/language-reference/statements/for-each-next-statement.md) ou d'une requête LINQ.  Chaque itération de la boucle d' `For Each` appelle la fonction d'itérateur.  Lorsqu'une instruction d' `Yield` atteinte dans la fonction d'itérateur, `expression` est retourné, et la position actuelle dans le code est conservée.  L'exécution est redémarrée de cet emplacement à la prochaine fois que la fonction d'itérateur est appelé.  
  
 Une conversion implicite doit exister du type d' `expression` dans l'instruction d' `Yield` au type de retour de l'itérateur.  
  
 Vous pouvez utiliser une instruction d' `Exit Function` ou d' `Return` pour terminer l'itération.  
  
 Le rendement «  » n'est pas un mot réservé et a un ordre particulier uniquement lorsqu'il est utilisé dans une fonction d' `Iterator` ou un utilisateur d' `Get` .  
  
 Pour plus d'informations sur les fonctions des itérateurs et des utilisateurs d' `Get`, consultez l' [Itérateurs](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Utilisateurs de fonctions et get itérateur  
 La déclaration d'une fonction d'itérateur ou d'un utilisateur d' `Get` doit répondre aux conditions suivantes :  
  
-   Il doit inclure un modificateur d' [Itérateur](../../../visual-basic/language-reference/modifiers/iterator.md) .  
  
-   Le type de retour doit être <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, ou <xref:System.Collections.Generic.IEnumerator%601>.  
  
-   Il n'a peut\-être pas de paramètres d' `ByRef` .  
  
 Une fonction d'itérateur ne peut pas apparaître dans un événement, un constructeur d'instance, un constructeur statique, ou un destructeur statique.  
  
 Une fonction d'itérateur peut être une fonction anonyme.  Pour plus d'informations, consultez [Itérateurs](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Gestion des exceptions  
 Une instruction d' `Yield` peut se trouver dans un bloc d' `Try` de [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  Un bloc `Try` qui a une instruction `Yield` peut avoir des blocs `Catch` , et peut avoir un bloc `Finally` .  
  
 Une instruction `Yield` ne peut pas être dans un bloc `Catch` ou un bloc `Finally` .  
  
 Si le corps d' `For Each` \(en dehors de la fonction d'itérateur\) lève une exception, un bloc d' `Catch` dans la fonction d'itérateur n'est pas exécuté, mais un bloc d' `Finally` dans la fonction d'itérateur est exécuté.  Un bloc `Catch` à l'intérieur d'une fonction d'itérateur intercepte uniquement les exceptions qui se produisent à l'intérieur de la fonction d'itérateur.  
  
## Implémentation technique  
 Le code suivant retourne `IEnumerable (Of String)` d'une fonction d'itérateur puis itère au sein de les éléments d' `IEnumerable (Of String)`.  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 L'appel à `MyIteratorFunction` n'exécute pas le corps de la fonction.  À la place l'appel retourne `IEnumerable(Of String)` dans la variable d' `elements` .  
  
 Sur une itération de la boucle d' `For Each`, la méthode d' <xref:System.Collections.IEnumerator.MoveNext%2A> est appelée pour `elements`.  Cet appel exécute le corps d' `MyIteratorFunction` jusqu'à ce que l'instruction suivante d' `Yield` soit atteinte.  L'instruction d' `Yield` retourne une expression qui détermine non seulement la valeur de la variable d' `element` en vue de leur utilisation par le corps de la boucle mais également la propriété d' <xref:System.Collections.Generic.IEnumerator%601.Current%2A> des éléments, qui est `IEnumerable (Of String)`.  
  
 Pour chaque itération suivante de la boucle d' `For Each`, l'exécution du corps des itérateurs continue à laquelle elle a été arrêté, de nouveau arrêtant lorsqu'elle atteint une instruction d' `Yield` .  La boucle d' `For Each` se termine lorsque la fin de la fonction d'itérateur ou d'une instruction d' `Return` ou d' `Exit Function` est atteinte.  
  
## Exemple  
 L'exemple suivant présente une instruction d' `Yield` qui est à l'intérieur d'une boucle d' [For… next](../../../visual-basic/language-reference/statements/for-next-statement.md) .  Chaque itération du corps d'instruction d' [Pour chaque](../../../visual-basic/language-reference/statements/for-each-next-statement.md) dans `Main` crée un appel à la fonction d'itérateur d' `Power` .  Chaque appel à la fonction d'itérateur continue à la prochaine exécution de l'instruction d' `Yield`, qui se produit pendant l'itération suivante de la boucle d' `For…Next` .  
  
 Le type de retour de la méthode d'itérateur est <xref:System.Collections.Generic.IEnumerable%601>, un type d'interface d'itérateur.  Lorsque la méthode d'itérateur est appelée, elle retourne un objet énumérable qui contient les puissances d'un nombre.  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_1.vb)]  
  
## Exemple  
 L'exemple suivant montre un utilisateur d' `Get` qui est un itérateur.  La déclaration de propriété inclut un modificateur d' `Iterator` .  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_2.vb)]  
  
 Pour obtenir d'autres exemples, consultez [Itérateurs](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Configuration requise  
 [!INCLUDE[vs_dev11_long](../../../csharp/includes/vs_dev11_long_md.md)]  
  
## Voir aussi  
 [Itérateurs](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)   
 [Statements](../../../visual-basic/language-reference/statements/index.md)