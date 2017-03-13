---
title: "For Each...Next, instruction (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.ForEach"
  - "vb.ForEachNext"
  - "vb.Each"
  - "ForEachNext"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "boucles infinies"
  - "instruction Next, For Each...Next"
  - "boucles infinies"
  - "structures de boucle, For Each...Next"
  - "boucles, infinies"
  - "Each (mot clé)"
  - "instructions, répéter"
  - "For Each (instruction)"
  - "collections, répétition d’instruction"
  - "boucles, infinies"
  - "instructions For Each...Next"
  - "mot clé For [Visual Basic], instructions For Each...Next"
  - "instruction Exit, instructions For Each...Next"
  - "itération"
ms.assetid: ebce3120-95c3-42b1-b70b-fa7da40c75e2
caps.latest.revision: 56
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 56
---
# For Each...Next, instruction (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Répète un groupe d'instructions pour chaque élément d'une collection.  
  
## Syntaxe  
  
```  
For Each element [ As datatype ] In group  
    [ statements ]  
    [ Continue For ]  
    [ statements ]  
    [ Exit For ]  
    [ statements ]  
Next [ element ]  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`element`|Requis dans l'instruction `For Each`.  Facultatif dans les instructions `Next`.  Variable.  Utilisée pour itérer au sein des éléments de la collection.|  
|`datatype`|Obligatoire si `element` n'est pas déjà déclaré.  Type de données de `element`.|  
|`group`|Requis.  Une variable avec un type qui est un type de collection ou un objet.  Fait référence à la collection sur laquelle les `statements` doivent être répétées.|  
|`statements`|Optionnel.  Une ou plusieurs instructions entre `For Each` et `Next` qui s'exécutent sur chaque élément dans `group`.|  
|`Continue For`|Optionnel.  Transfère le contrôle au démarrage de la boucle `For Each`.|  
|`Exit For`|Optionnel.  Transfert le contrôle hors de la boucle `For Each`.|  
|`Next`|Requis.  Termine la définition de la boucle `For Each`.|  
  
## Exemple simple  
 Utilisez une boucle `For Each`...`Next` lorsque vous souhaitez répéter un ensemble d'instructions pour chaque élément d'une collection ou d'un tableau.  
  
> [!TIP]
>  Une [For...Next, instruction](../../../visual-basic/language-reference/statements/for-next-statement.md) fonctionne correctement lorsque vous pouvez associer chaque itération d'une boucle à une variable de contrôle et déterminer les valeurs initiale et finale de cette variable.  Toutefois, lorsque vous utilisez une collection, le concept des valeurs initiales et dernières n'est pas explicite, et vous ne connaissez pas nécessairement le nombre d'éléments que la collection est.  Dans ce type de cas, une boucle d' `For Each`…`Next` est souvent préférable d'utiliser.  
  
 Dans l'exemple suivant, l'instruction d' `For Each`…`Next` itère au sein de tous les éléments d'une collection de listes.  
  
 [!code-vb[VbVbalrStatements#121](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_1.vb)]  
  
 Pour obtenir d'autres exemples, consultez [Collections](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md) et [Tableaux](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## Boucles imbriquées  
 Vous pouvez imbriquer les boucles `For Each` en plaçant une boucle à l'intérieur d'une autre.  
  
 L'exemple suivant illustre des structures `For Each`…`Next` imbriquées.  
  
 [!code-vb[VbVbalrStatements#122](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_2.vb)]  
  
 Lorsque vous emboîtez des boucles, chaque boucle doit avoir une seule variable d' `element` .  
  
 Vous pouvez également imbriquer divers types de structures de contrôle l'un dans l'autre.  Pour plus d'informations, consultez [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## Quittez pour & continuer pour  
 L'instruction d' [Quittez pour](../../../visual-basic/language-reference/statements/exit-statement.md) fait de quitter l'exécution de la boucle et transfère le contrôle d' `For`…`Next` à l'instruction qui suit l'instruction d' `Next` .  
  
 L'instruction `Continue For` transfère immédiatement le contrôle vers l'itération suivante de la boucle.  Pour plus d'informations, consultez [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
 L'exemple suivant montre comment utiliser les instructions `Continue For` et `Exit For`.  
  
 [!code-vb[VbVbalrStatements#123](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_3.vb)]  
  
 Vous pouvez placer n'importe quel nombre d'instructions `Exit For` dans une boucle `For Each`.  Utilisée dans des boucles `For Each` imbriquées, l'instruction `Exit For` quitte la boucle la plus profonde et transfère le contrôle au niveau d'imbrication supérieur suivant.  
  
 `Exit For` est souvent utilisé après l'évaluation d'une condition, par exemple dans une structure `If`...`Then`...`Else`.  Vous pouvez utiliser `Exit For` pour les conditions suivantes :  
  
-   La poursuite de l'itération est inutile ou impossible.  Cela peut être causé par une valeur erronée ou une demande d'arrêt.  
  
-   Une exception est interceptée dans `Try`...`Catch`...`Finally`.  Vous pouvez utiliser `Exit For` à la fin du bloc `Finally`.  
  
-   Il existe une boucle sans fin, c'est\-à\-dire une boucle qui pourrait s'exécuter de nombreuses fois, voire indéfiniment.  Si vous détectez une telle condition, vous pouvez utiliser `Exit For` pour abandonner la boucle.  Pour plus d'informations, consultez [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).  
  
## Itérateurs  
 Vous utilisez *un itérateur* pour effectuer une itération personnalisée sur une collection.  Un itérateur peut être une fonction ou un utilisateur d' `Get` .  Il utilise une instruction d' `Yield` pour retourner chaque élément de la collection un par un.  
  
 Vous appelez un itérateur en utilisant une instruction d' `For Each...Next` .  Chaque itération de la boucle `For Each` appelle l'itérateur.  Lorsqu'une instruction d' `Yield` atteinte de l'itérateur, l'expression dans l'instruction d' `Yield` est retournée, et la position actuelle dans le code est conservée.  L'exécution redémarrera à partir de cet emplacement la prochaine fois que l'itérateur sera appelé.  
  
 L'exemple suivant utilise une fonction d'itérateur.  La fonction d'itérateur a une instruction d' `Yield` qui est à l'intérieur d'une boucle d' [For… next](../../../visual-basic/language-reference/statements/for-next-statement.md) .  Dans la méthode d' `ListEvenNumbers`, chaque itération du corps d'instruction d' `For Each` crée un appel à la fonction d'itérateur, qui continue à l'instruction d' `Yield` .  
  
 [!code-vb[VbVbalrStatements#127](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_4.vb)]  
  
 Pour plus d'informations, consultez [Itérateurs](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md), [yield, instruction](../../../visual-basic/language-reference/statements/yield-statement.md) et [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).  
  
## Implémentation technique  
 Lorsqu'une instruction d' `For Each`…`Next` s'exécute, Visual Basic prend la collection uniquement une fois, avant la boucle démarre.  Si votre bloc d'instructions change `element` ou `group`, ces modifications n'affectent pas l'itération de la boucle.  
  
 Lorsque tous les éléments de la collection ont été successivement assignés à `element`, la boucle `For Each` s'arrête et le contrôle est passé à l'instruction suivant l'instruction `Next`.  
  
 Si `element` n'a pas été déclaré en dehors de la boucle, vous devez la déclarer dans l'instruction d' `For Each` .  Vous pouvez déclarer explicitement le type d'`element` en utilisant une instruction `As` ou vous pouvez compter sur l'inférence de type pour assigner le type.  Dans les deux cas, la portée de `element` est le corps de la boucle.  Cependant, vous ne pouvez pas déclarer `element` à la fois à l'extérieur et à l'intérieur de la boucle.  
  
 Vous pouvez éventuellement définir `element` dans l'instruction `Next`.  Cela améliore la lisibilité de votre programme, surtout si vous avez imbriqué des boucles `For Each`.  Vous devez spécifier la même variable que celle qui apparaît dans l'instruction `For Each` correspondante.  
  
 Vous pouvez éviter de changer la valeur de `element` à l'intérieur d'une boucle.  Cette opération rendra la lecture et le débogage de votre code plus difficiles.  Modifier la valeur d' `group` n'affecte pas la collection ou ses éléments, qui étaient déterminés lorsque la boucle a été écrite la première fois.  
  
 Lorsque vous avez des boucles d'imbrication, si une instruction d' `Next` d'un niveau d'imbrication externe est produit avant qu' `Next` d'un niveau interne, le compilateur signale une erreur.  Toutefois, le compilateur peut détecter cette erreur de chevauchement uniquement si vous spécifiez `element` dans chaque instruction `Next`.  
  
 Si votre code dépend de parcourir une collection dans un ordre particulier, une boucle d' `For Each`…`Next` n'est pas le meilleur choix, à moins que vous connaissiez les caractéristiques de l'objet énumérateur que la collection expose.  L'ordre de parcours n'est pas déterminé par Visual Basic, mais par la méthode d' <xref:System.Collections.IEnumerator.MoveNext%2A> d'objet énumérateur.  Ceci signifie que vous ne pourrez peut\-être pas prévoir quel sera le premier élément de la collection retourné dans `element` ou quel sera l'élément suivant renvoyé après un élément donné.  Vous pouvez obtenir des résultats plus fiables à l'aide d'une structure de boucle différente, par exemple `For`...`Next` ou `Do`...`Loop`..  
  
 Le type de données des éléments de `group` doit pouvoir être converti en type de données de `element`.  
  
 Le type de données d' `group` doit être un type référence qui fait référence à une collection ou un tableau qui est énumérable.  La plupart du temps, cela signifie que `group` fait référence à un objet qui implémente l'interface <xref:System.Collections.IEnumerable> de l'espace de noms `System.Collections` ou l'interface <xref:System.Collections.Generic.IEnumerable%601> de l'espace de noms `System.Collections.Generic`.  `System.Collections.IEnumerable` définit la méthode <xref:System.Collections.IEnumerable.GetEnumerator%2A>, qui retourne un objet énumérateur pour la collection.  L'objet énumérateur implémente l'interface `System.Collections.IEnumerator` de l'espace de noms `System.Collections` et expose la propriété <xref:System.Collections.IEnumerator.Current%2A> et les méthodes <xref:System.Collections.IEnumerator.Reset%2A> et <xref:System.Collections.IEnumerator.MoveNext%2A>.  Visual Basic les utilise pour parcourir la collection.  
  
### Conversions restrictives  
 Lorsque `Option Strict` a la valeur `On`, les conversions restrictives provoquent ordinairement des erreurs du compilateur.  Dans une instruction `For Each`, cependant, les conversions à partir des éléments de `group` vers `element` sont évaluées et exécutées au moment de l'exécution, et les erreurs du compilateur causées par des conversions restrictives sont supprimées.  
  
 Dans l'exemple suivant, l'assignation d' `m` comme valeur initiale pour `n` ne compile pas lorsque `Option Strict` est activé parce que la conversion d' `Long` à `Integer` est une conversion restrictive.  Toutefois, dans l'instruction `For Each`, aucune erreur de compilateur n'est signalée, même si l'affectation à `number` nécessite la même conversion de `Long` à `Integer`.  Dans l'instruction `For Each` qui contient un nombre élevé, une erreur d'exécution se produit lorsque <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A> est appliqué au nombre élevé.  
  
 [!code-vb[VbVbalrStatements#89](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_5.vb)]  
  
### Appels IEnumerator  
 Lorsque l'exécution d'une boucle `For Each`...`Next` commence, Visual Basic vérifie que `group` fait référence à un objet de collection valide.  Si tel n'est pas le cas, il lève une exception.  Sinon, il appelle la méthode <xref:System.Collections.IEnumerator.MoveNext%2A> et la propriété <xref:System.Collections.IEnumerator.Current%2A> de l'objet énumérateur pour retourner le premier élément.  Si `MoveNext` indique qu'il n'y a aucun élément suivant, c'est\-à\-dire si la collection est vide, la boucle `For Each` s'arrête et le contrôle est passé à l'instruction qui suit l'instruction `Next`.  Sinon, Visual Basic affecte `element` au premier élément et exécute le bloc d'instructions.  
  
 Chaque fois que Visual Basic rencontre l'instruction `Next`, il retourne à l'instruction `For Each`.  Il appelle de nouveau `MoveNext` et `Current` pour retourner l'élément suivant et exécute à nouveau le bloc ou arrête la boucle selon le résultat.  Ce processus continue jusqu'à ce que `MoveNext` indique qu'il n'y a aucun élément suivant ou qu'une instruction `Exit For` soit rencontrée.  
  
 **Modification de la collection.** L'énumérateur objet retourné par <xref:System.Collections.IEnumerable.GetEnumerator%2A> normalement ne vous permet pas de modifier la collection n'en ajoutant, en supprimant, en substituant, ou en principale de nouveau aucun élément.  Si vous modifiez la collection après avoir lancé une boucle `For Each`...`Next`, l'objet énumérateur devient non valide et la tentative d'accès suivante à un élément provoque une exception <xref:System.InvalidOperationException>.  
  
 Toutefois, ce blocage de modification n'est pas déterminé par [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)], mais plutôt par l'implémentation de l'interface d' <xref:System.Collections.IEnumerable> .  Il est possible d'implémenter `IEnumerable` de sorte que les modifications soient autorisées pendant l'itération.  Si vous comptez effectuer des modifications dynamiques de ce type, soyez sûr que vous connaissez les caractéristiques de l'implémentation de `IEnumerable` sur la collection que vous utilisez.  
  
 **Modification d'éléments de collection.** La propriété <xref:System.Collections.IEnumerator.Current%2A> de l'objet énumérateur est [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md). Elle retourne une copie locale de chaque élément de la collection.  Cela signifie que vous ne pouvez pas modifier les éléments d'une boucle `For Each`...`Next`.  Toute modification vous effectuez à affecte uniquement la copie locale d' `Current` et n'êtes pas répercutée dans le dans la collection sous\-jacente.  Cependant, si un élément correspond à un type référence, vous pouvez modifier les membres de l'instance vers laquelle il pointe.  L'exemple suivant modifie le membre d' `BackColor` de chaque élément d' `thisControl` .  Vous ne pouvez pas, toutefois, la modification `thisControl` lui\-même.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 L'exemple précédent peut modifier le membre `BackColor` de chaque élément `thisControl`, bien qu'il ne puisse pas modifier `thisControl` lui\-même.  
  
 **Parcours de tableaux.** Étant donné que la classe <xref:System.Array> implémente l'interface <xref:System.Collections.IEnumerable>, tous les tableaux exposent la méthode <xref:System.Array.GetEnumerator%2A>.  Cela signifie que vous pouvez itérer au sein d'un tableau avec une boucle `For Each`...`Next`.  Toutefois, vous pouvez uniquement lire les éléments du tableau.  Vous ne pouvez pas les modifier.  
  
## Exemple  
 L'exemple suivant répertorie tous les dossiers dans le répertoire C:\\ à l'aide de la classe <xref:System.IO.DirectoryInfo>.  
  
 [!code-vb[VbVbalrStatements#124](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_6.vb)]  
  
## Exemple  
 L'exemple suivant affiche une procédure pour trier une collection.  L'exemple trie les instances d'une classe d' `Car` stockées dans <xref:System.Collections.Generic.List%601>.  La classe `Car` implémente l'interface <xref:System.IComparable%601> , qui exige que la méthode <xref:System.IComparable%601.CompareTo%2A> soit implémentée.  
  
 Chaque appel à la méthode d' <xref:System.IComparable%601.CompareTo%2A> effectue une comparaison unique utilisée pour trier.  Le code écrit par l'utilisateur dans la méthode `CompareTo` retourne une valeur pour chaque comparaison de l'objet en cours par un autre objet.  La valeur retournée est inférieur à zéro si l'objet actuel est inférieur à l'autre objet, supérieur à zéro si l'objet actuel est supérieur à l'autre objet, et zéro s'ils sont égaux.  Cela vous permet de définir dans le code les critères pour supérieur, inférieur à, et égal.  
  
 Dans la méthode `ListCars` , l'instruction `cars.Sort()` trie la liste.  Cet appel à la méthode <xref:System.Collections.Generic.List%601.Sort%2A> de <xref:System.Collections.Generic.List%601> entraîne l'appel de la méthode `CompareTo` automatiquement pour les objets de type `Car` dans `List`.  
  
 [!code-vb[VbVbalrStatements#125](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_7.vb)]  
  
## Voir aussi  
 [Collections](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)   
 [For...Next, instruction](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Loop Structures](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md)   
 [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md)   
 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)   
 [Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)   
 [Tableaux](../../../visual-basic/programming-guide/language-features/arrays/index.md)