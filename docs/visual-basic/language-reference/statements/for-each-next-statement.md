---
title: For Each...Next, instruction (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ForEach
- vb.ForEachNext
- vb.Each
- ForEachNext
helpviewer_keywords:
- infinite loops
- Next statement [Visual Basic], For Each...Next
- endless loops
- loop structures [Visual Basic], For Each...Next
- loops, endless
- Each keyword [Visual Basic]
- instructions, repeating
- For Each statement [Visual Basic]
- collections, instruction repetition
- loops, infinite
- For Each...Next statements
- For keyword [Visual Basic], For Each...Next statements
- Exit statement [Visual Basic], For Each...Next statements
- iteration
ms.assetid: ebce3120-95c3-42b1-b70b-fa7da40c75e2
caps.latest.revision: "56"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4aefacd33e0b3c8f64fd26929af06469136237f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="for-eachnext-statement-visual-basic"></a>For Each...Next, instruction (Visual Basic)
Répète un groupe d’instructions pour chaque élément dans une collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
For Each element [ As datatype ] In group  
    [ statements ]  
    [ Continue For ]  
    [ statements ]  
    [ Exit For ]  
    [ statements ]  
Next [ element ]  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`element`|Requis dans le `For Each` instruction. Facultatif dans la `Next` instruction. Variable. Utilisé pour itérer sur les éléments de la collection.|  
|`datatype`|Obligatoire si `element` n’est pas déjà déclaré. Type de données de `element`.|  
|`group`|Obligatoire. Une variable avec un type qui est un type de collection ou d’un objet. Fait référence à la collection sur laquelle le `statements` doivent être répétées.|  
|`statements`|Facultatif. Une ou plusieurs instructions entre `For Each` et `Next` qui s’exécutent sur chaque élément de `group`.|  
|`Continue For`|Facultatif. Transfère le contrôle au début de la `For Each` boucle.|  
|`Exit For`|Facultatif. Transfère le contrôle de le `For Each` boucle.|  
|`Next`|Obligatoire. Termine la définition de la `For Each` boucle.|  
  
## <a name="simple-example"></a>Exemple simple  
 Utilisez un `For Each`... `Next` boucle lorsque vous souhaitez répéter un ensemble d’instructions pour chaque élément d’une collection ou un tableau.  
  
> [!TIP]
>  A [pour... L’instruction suivante](../../../visual-basic/language-reference/statements/for-next-statement.md) fonctionne bien lorsque vous pouvez associer chaque itération d’une boucle à une variable de contrôle et déterminer les valeurs initiale et finale de cette variable. Toutefois, lorsque vous êtes confronté à une collection, le concept de valeurs initiales et finales n’est pas significatif, et vous ne connaissez pas forcément la collection est le nombre d’éléments. Dans ce type de cas, un `For Each`... `Next` boucle est souvent un meilleur choix.  
  
 Dans l’exemple suivant, la `For Each`...`Next` instruction effectue une itération dans tous les éléments d’une collection de listes.  
  
 [!code-vb[VbVbalrStatements#121](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_1.vb)]  
  
 Pour plus d’exemples, consultez [Collections](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b) et [tableaux](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="nested-loops"></a>Boucles imbriquées  
 Vous pouvez imbriquer `For Each` boucles en plaçant une boucle à l’intérieur d’une autre.  
  
 L’exemple suivant illustre des structures `For Each`...`Next` structures.  
  
 [!code-vb[VbVbalrStatements#122](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_2.vb)]  
  
 Lorsque vous imbriquez des boucles, chaque boucle doit posséder un unique `element` variable.  
  
 Vous pouvez également imbriquer des différents types de structures de contrôle dans d’autres. Pour plus d’informations, consultez [Structures de contrôle imbriquées](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-for-and-continue-for"></a>Pour et continuez pour  
 Le [Exit For](../../../visual-basic/language-reference/statements/exit-statement.md) instruction provoque l’exécution quitter le `For`...`Next` boucle et les transfère le contrôle à l’instruction qui suit la `Next` instruction.  
  
 La `Continue For` instruction transfère le contrôle immédiatement à l’itération suivante de la boucle. Pour plus d’informations, consultez [instruction Continue](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
 L’exemple suivant montre comment utiliser le `Continue For` et `Exit For` instructions.  
  
 [!code-vb[VbVbalrStatements#123](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_3.vb)]  
  
 Vous pouvez placer n’importe quel nombre de `Exit For` instructions dans un `For Each` boucle. Lorsqu’il est utilisé dans imbriqués `For Each` boucles, `Exit For` quitte le contrôle le plus profond et transfère au niveau d’imbrication supérieur suivant.  
  
 `Exit For`est souvent utilisé après l’évaluation d’une condition, par exemple, dans un `If`... `Then`... `Else` structure. Vous souhaiterez peut-être utiliser `Exit For` dans les cas suivants :  
  
-   Pour continuer à effectuer une itération est inutile ou impossible. Cela peut être dû à une valeur erronée ou une demande d’arrêt.  
  
-   Une exception est interceptée dans un `Try`... `Catch`... `Finally`. Vous pouvez utiliser `Exit For` à la fin de la `Finally` bloc.  
  
-   Il existe une boucle infinie, ce qui est une boucle qui pourrait exécuter un importantes ou infini même le nombre de fois. Si vous détectez une telle condition, vous pouvez utiliser `Exit For` pour abandonner la boucle. Pour plus d’informations, consultez [faire... Instruction de boucle](../../../visual-basic/language-reference/statements/do-loop-statement.md).  
  
## <a name="iterators"></a>Itérateurs  
 Vous utilisez un *itérateur* pour effectuer une itération personnalisée sur une collection. Un itérateur peut être une fonction ou un `Get` accesseur. Il utilise un `Yield` instruction pour retourner chaque élément de la collection un à la fois.  
  
 Vous appelez un itérateur en utilisant un `For Each...Next` instruction. Chaque itération de la boucle `For Each` appelle l’itérateur. Quand un `Yield` instruction est atteint dans l’itérateur, l’expression dans la `Yield` instruction est retournée et l’emplacement actuel dans le code est conservé. L’exécution est redémarrée à partir de cet emplacement la prochaine fois que l’itérateur est appelé.  
  
 L’exemple suivant utilise une fonction d’itérateur. La fonction d’itérateur a un `Yield` instruction qui se trouve dans un [pour... Suivant](../../../visual-basic/language-reference/statements/for-next-statement.md) boucle. Dans le `ListEvenNumbers` (méthode), chaque itération de la `For Each` corps de l’instruction crée un appel à la fonction d’itérateur, qui passe à la prochaine `Yield` instruction.  
  
 [!code-vb[VbVbalrStatements#127](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_4.vb)]  
  
 Pour plus d’informations, consultez [itérateurs](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7), [instruction Yield](../../../visual-basic/language-reference/statements/yield-statement.md), et [itérateur](../../../visual-basic/language-reference/modifiers/iterator.md).  
  
## <a name="technical-implementation"></a>Implémentation technique  
 Lorsqu’un `For Each`...`Next` instruction s’exécute, Visual Basic évalue la collection qu’une seule fois, avant le démarrage de la boucle. Si votre bloc d’instructions modifie `element` ou `group`, ces modifications n’affectent pas l’itération de la boucle.  
  
 Lorsque tous les éléments de la collection ont été assignés successivement à `element`, le `For Each` boucle s’arrête et le contrôle passe à l’instruction qui suit la `Next` instruction.  
  
 Si `element` n’a pas été déclarée en dehors de cette boucle, vous devez la déclarer dans le `For Each` instruction. Vous pouvez déclarer le type de `element` explicitement en utilisant un `As` instruction, ou vous pouvez compter sur l’inférence de type pour assigner le type. Dans les deux cas, la portée de `element` est le corps de la boucle. Toutefois, vous ne pouvez pas déclarer `element` à la fois à l’extérieur et à l’intérieur de la boucle.  
  
 Vous pouvez éventuellement spécifier `element` dans la `Next` instruction. Cela améliore la lisibilité de votre programme, surtout si vous avez imbriqué `For Each` boucles. Vous devez spécifier la même variable que celle qui s’affiche dans le `For Each` instruction.  
  
 Vous souhaiterez peut-être éviter de modifier la valeur de `element` à l’intérieur d’une boucle. Cela peut rendre plus difficile à lire et déboguer votre code. Modification de la valeur de `group` n’affecte pas la collection ou ses éléments qui ont été déterminées lors de la première entrée de la boucle.  
  
 Lorsque vous êtes imbrication de boucles, si un `Next` d’un niveau d’imbrication externe est rencontrée avant la `Next` d’un niveau interne, le compilateur signale une erreur. Toutefois, le compilateur peut détecter cette erreur de chevauchement uniquement si vous spécifiez `element` dans chaque `Next` instruction.  
  
 Si votre code dépend du parcours d’une collection dans un ordre particulier, un `For Each`... `Next` boucle n’est pas le meilleur choix, sauf si vous connaissez les caractéristiques de l’objet énumérateur exposé par la collection. L’ordre de parcours n’est pas déterminé par Visual Basic, mais par le <xref:System.Collections.IEnumerator.MoveNext%2A> méthode de l’objet énumérateur. Par conséquent, vous ne pouvez peut-être pas prédire quel élément de la collection est le premier à être retournée dans `element`, ou qui est le suivant renvoyé après un élément donné. Vous pouvez obtenir des résultats plus fiables à l’aide d’une structure de boucle différente, comme `For`... `Next` ou `Do`... `Loop`.  
  
 Type de données de `element` doit être tel que le type de données des éléments de `group` peut être converti en il.  
  
 Type de données de `group` doit être un type référence qui fait référence à une collection ou un tableau qui est énumérable. Plus souvent, cela signifie que `group` fait référence à un objet qui implémente le <xref:System.Collections.IEnumerable> interface de la `System.Collections` espace de noms ou le <xref:System.Collections.Generic.IEnumerable%601> interface de le `System.Collections.Generic` espace de noms. `System.Collections.IEnumerable`définit le <xref:System.Collections.IEnumerable.GetEnumerator%2A> (méthode), qui retourne un objet énumérateur pour la collection. L’objet énumérateur implémente la `System.Collections.IEnumerator` interface de la `System.Collections` espace de noms et expose le <xref:System.Collections.IEnumerator.Current%2A> propriété et la <xref:System.Collections.IEnumerator.Reset%2A> et <xref:System.Collections.IEnumerator.MoveNext%2A> méthodes. Visual Basic utilise pour parcourir la collection.  
  
### <a name="narrowing-conversions"></a>conversions restrictives  
 Lorsque `Option Strict` a la valeur `On`, les conversions restrictives provoquent ordinairement des erreurs du compilateur. Dans un `For Each` instruction, toutefois, les conversions à partir des éléments dans `group` à `element` sont évaluées et exécutées au moment de l’exécution, et les erreurs du compilateur provoquées par les conversions restrictives sont supprimées.  
  
 Dans l’exemple suivant, l’affectation de `m` comme valeur initiale pour `n` ne se compile pas lorsque `Option Strict` est activé, car la conversion d’un `Long` à un `Integer` est une conversion restrictive. Dans le `For Each` instruction, toutefois, aucune erreur du compilateur n’est signalée, même si l’assignation à `number` nécessite la même conversion de `Long` à `Integer`. Dans le `For Each` se produit une erreur d’exécution de l’instruction qui contient un grand nombre, lorsque <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A> est appliqué à un grand nombre.  
  
 [!code-vb[VbVbalrStatements#89](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_5.vb)]  
  
### <a name="ienumerator-calls"></a>Appels IEnumerator  
 Lors de l’exécution d’un `For Each`... `Next` commence, Visual Basic vérifie que `group` fait référence à un objet de collection valide. Si ce n’est pas le cas, elle lève une exception. Sinon, elle appelle la <xref:System.Collections.IEnumerator.MoveNext%2A> (méthode) et le <xref:System.Collections.IEnumerator.Current%2A> propriété de l’objet énumérateur pour retourner le premier élément. Si `MoveNext` indique qu’il n’existe aucun élément suivant, autrement dit, si la collection est vide, le `For Each` boucle s’arrête et le contrôle passe à l’instruction qui suit la `Next` instruction. Dans le cas contraire, Visual Basic définit `element` au premier élément et exécute le bloc d’instructions.  
  
 Chaque fois que Visual Basic rencontre le `Next` instruction, il renvoie à la `For Each` instruction. Il appelle de nouveau `MoveNext` et `Current` pour retourner l’élément suivant, puis exécute le bloc soit arrête la boucle en fonction du résultat. Ce processus se poursuit jusqu'à ce que `MoveNext` indique qu’il n’existe aucun élément suivant ou `Exit For` est rencontrée.  
  
 **Modification de la Collection.** L’objet énumérateur retourné par <xref:System.Collections.IEnumerable.GetEnumerator%2A> ne vous permettent de modifier la collection par l’ajout, de suppression, de remplacement ou de réorganisation d’éléments. Si vous modifiez la collection après avoir lancé une `For Each`... `Next` boucle, l’objet énumérateur devienne non valide, et la prochaine tentative d’accéder à un élément provoque une <xref:System.InvalidOperationException> exception.  
  
 Toutefois, ce blocage de modification n’est pas déterminé par [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], mais plutôt par l’implémentation de la <xref:System.Collections.IEnumerable> interface. Il est possible d’implémenter `IEnumerable` d’une manière qui autorise la modification pendant l’itération. Si vous comptez effectuer cette modification dynamique, assurez-vous que vous comprenez les caractéristiques de la `IEnumerable` implémentation sur la collection que vous utilisez.  
  
 **Modification des éléments de la Collection.** Le <xref:System.Collections.IEnumerator.Current%2A> la propriété de l’objet énumérateur est [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md), et retourne une copie locale de chaque élément de la collection. Cela signifie que vous ne pouvez pas modifier les éléments dans un `For Each`... `Next` boucle. Toute modification apportée affecte uniquement la copie locale de `Current` et n’est pas répercutée dans la collection sous-jacente. Toutefois, si un élément est un type référence, vous pouvez modifier les membres de l’instance vers laquelle il pointe. L’exemple suivant modifie le `BackColor` membre de chaque `thisControl` élément. Toutefois, vous ne pouvez pas modifier `thisControl` lui-même.  
  
```vb  
Sub lightBlueBackground(ByVal thisForm As System.Windows.Forms.Form)  
    For Each thisControl As System.Windows.Forms.Control In thisForm.Controls  
        thisControl.BackColor = System.Drawing.Color.LightBlue  
    Next thisControl  
End Sub  
```  
  
 L’exemple précédent peut modifier le `BackColor` membre de chaque `thisControl` élément, bien qu’il ne peut pas modifier `thisControl` lui-même.  
  
 **Parcours de tableaux.** Étant donné que la <xref:System.Array> la classe implémente le <xref:System.Collections.IEnumerable> interface, tous les tableaux exposent le <xref:System.Array.GetEnumerator%2A> (méthode). Cela signifie que vous pouvez itérer au sein d’un tableau avec un `For Each`... `Next` boucle. Toutefois, vous pouvez uniquement lire les éléments du tableau. Vous ne pouvez pas les modifier.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant répertorie tous les dossiers dans le répertoire C:\ à l’aide de la <xref:System.IO.DirectoryInfo> classe.  
  
 [!code-vb[VbVbalrStatements#124](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_6.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre une procédure de tri d’une collection. L’exemple trie les instances d’un `Car` classe qui sont stockés dans un <xref:System.Collections.Generic.List%601>. La classe `Car` implémente l’interface <xref:System.IComparable%601>, ce qui implique l’implémentation de la méthode <xref:System.IComparable%601.CompareTo%2A>.  
  
 Chaque appel à la <xref:System.IComparable%601.CompareTo%2A> méthode effectue une comparaison unique qui est utilisée pour le tri. Le code écrit par l’utilisateur dans la méthode `CompareTo` retourne une valeur pour chaque comparaison de l’objet actuel avec un autre objet. La valeur retournée est inférieure à zéro si l’objet actuel est inférieur à l’autre objet, supérieure à zéro l’objet actuel est supérieur à l’autre et égale à zéro s’ils sont égaux. Cela vous permet de définir dans le code les critères définissant « supérieur à », « inférieur à » et « égal à ».  
  
 Dans la méthode `ListCars`, l’instruction `cars.Sort()` trie la liste. Cet appel à la méthode <xref:System.Collections.Generic.List%601.Sort%2A> de <xref:System.Collections.Generic.List%601> entraîne l’appel automatique de la méthode `CompareTo` pour les objets `Car` dans `List`.  
  
 [!code-vb[VbVbalrStatements#125](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_7.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Collections](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)  
 [For...Next (instruction)](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Structures de boucle](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [While...End While (instruction)](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [Do...Loop (instruction)](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [Conversions étendues et restrictives](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Initialiseurs d’objets : types nommés et anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Initialiseurs de collection](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [Tableaux](../../../visual-basic/programming-guide/language-features/arrays/index.md)
