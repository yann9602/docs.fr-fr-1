---
title: Function, instruction (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Function
helpviewer_keywords:
- procedures [Visual Basic], creating
- Function procedures [Visual Basic], Function statement syntax
- functions [Visual Basic], function procedures
- ParamArray keyword [Visual Basic], Function statements
- Private keyword [Visual Basic], Function statements
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- Public keyword [Visual Basic], in Function statement
- ByVal keyword [Visual Basic], Function statements
- procedures [Visual Basic], recursive
- Implements keyword [Visual Basic], Function statements
- procedures [Visual Basic], returning values
- Exit statement [Visual Basic], in Function procedures
- recursive procedures
- As keyword [Visual Basic], in Function statement
- Optional keyword [Visual Basic], Function statements
- Function statement [Visual Basic]
- Visual Basic code, Function procedures
- procedures [Visual Basic], function
- ByRef keyword [Visual Basic], Function statements
- Friend keyword [Visual Basic], Function statements
- End keyword [Visual Basic], Function statements
- Handles keyword [Visual Basic], Function statements
ms.assetid: a4497077-0f46-4ede-a27f-9e8670df52b9
caps.latest.revision: "62"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 667ab7ceb54e1f339fd645883ca2686c0cbb72b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="function-statement-visual-basic"></a>Function, instruction (Visual Basic)
Déclare le nom, paramètres et le code qui définissent une `Function` procédure.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]  
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Function ]  
    [ statements ]  
End Function  
```  
  
## <a name="parts"></a>Composants  
  
-   `attributelist`  
  
     Facultatif. Consultez [liste d’attributs](attribute-list.md).  
  
-   `accessmodifier`  
  
     Facultatif. Il peut s'agir d'une des valeurs suivantes :  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     Consultez [niveaux en Visual Basic d’accès](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
-   `proceduremodifiers`  
  
     Facultatif. Il peut s'agir d'une des valeurs suivantes :  
  
    -   [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     Facultatif. Consultez [partagé](../../../visual-basic/language-reference/modifiers/shared.md).  
  
-   `Shadows`  
  
     Facultatif. Consultez [ombres](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
-   `Async`  
  
     Facultatif. Consultez [Async](../../../visual-basic/language-reference/modifiers/async.md).  
  
-   `Iterator`  
  
     Facultatif. Consultez [itérateur](../../../visual-basic/language-reference/modifiers/iterator.md).  
  
-   `name`  
  
     Obligatoire. Nom de la procédure. Consultez [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   `typeparamlist`  
  
     Facultatif. Liste de paramètres de type pour une procédure générique. Consultez [tapez liste](type-list.md).  
  
-   `parameterlist`  
  
     Facultatif. Liste des noms de variables locales représentant les paramètres de cette procédure. Consultez [liste de paramètres](parameter-list.md).  
  
-   `returntype`  
  
     Obligatoire si `Option Strict` est `On`. Type de données de la valeur retournée par cette procédure.  
  
-   `Implements`  
  
     Facultatif. Indique que cette procédure implémente une ou plusieurs `Function` procédures, chacune étant définie dans une interface implémentée par la classe ou la structure conteneur de cette procédure. Consultez [implémente l’instruction](implements-statement.md).  
  
-   `implementslist`  
  
     Obligatoire si `Implements` est utilisé. Liste des procédures `Function` en cours d'implémentation.  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     Chaque `implementedprocedure` emploie la syntaxe et les éléments suivants :  
  
     `interface.definedname`  
  
    |Élément|Description|  
    |---|---|  
    |`interface`|Obligatoire. Nom d’une interface implémentée par cette procédure conteneur de classe ou structure.|  
    |`definedname`|Obligatoire. Nom par lequel la procédure est définie dans `interface`.|  
  
-   `Handles`  
  
     Facultatif. Indique que cette procédure peut gérer un ou plusieurs événements spécifiques. Consultez [gère](handles-clause.md).  
  
-   `eventlist`  
  
     Obligatoire si `Handles` est utilisé. Liste des événements gérés par cette procédure.  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     Chaque `eventspecifier` emploie la syntaxe et les éléments suivants :  
  
     `eventvariable.event`  
  
    |Élément|Description|  
    |---|---|  
    |`eventvariable`|Obligatoire. Variable objet déclarée avec le type de données de la classe ou structure qui déclenche l’événement.|  
    |`event`|Obligatoire. Nom de l’événement que gère de cette procédure.|  
  
-   `statements`  
  
     Facultatif. Bloc d’instructions à exécuter dans cette procédure.  
  
-   `End Function`  
  
     Termine la définition de cette procédure.  
  
## <a name="remarks"></a>Remarques  
 Tout le code exécutable doit être à l’intérieur d’une procédure. Chaque procédure, à son tour, est déclaré dans une classe, une structure ou un module qui est appelé à la classe, structure ou module conteneur.  
  
 Pour retourner une valeur au code appelant, utilisez un `Function` procédure ; sinon, utilisez un `Sub` procédure.  
  
## <a name="defining-a-function"></a>Définition d’une fonction  
 Vous pouvez définir un `Function` procédure uniquement au niveau du module. Par conséquent, le contexte de déclaration pour une fonction doit être une classe, une structure, un module ou une interface et ne peut pas être un fichier source, un espace de noms, une procédure ou un bloc. Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](declaration-contexts-and-default-access-levels.md).  
  
 `Function`les procédures par défaut d’un accès public. Vous pouvez ajuster leurs niveaux d’accès avec les modificateurs d’accès.  
  
 A `Function` procédure peut déclarer le type de données de la valeur de retour de la procédure. Vous pouvez spécifier n’importe quel type de données ou le nom d’une énumération, une structure, une classe ou une interface. Si vous ne spécifiez pas le `returntype` , la procédure retourne `Object`.  
  
 Si cette procédure utilise le `Implements` (mot clé), la classe ou la structure conteneur doit également avoir un `Implements` instruction qui suit immédiatement sa `Class` ou `Structure` instruction. Le `Implements` instruction doit inclure chaque interface spécifiée dans `implementslist`. Toutefois, le nom par lequel une interface définit les `Function` (dans `definedname`) n’a pas besoin de correspondre au nom de cette procédure (dans `name`).  
  
> [!NOTE]
>  Vous pouvez utiliser des expressions lambda pour définir des expressions de fonction inline. Pour plus d’informations, consultez [Expression de fonction](../../../visual-basic/language-reference/operators/function-expression.md) et [Expressions Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
## <a name="returning-from-a-function"></a>Retour d’une fonction  
 Lorsque le `Function` procédure retourne au code appelant, l’exécution se poursuit avec l’instruction qui suit l’instruction qui a appelé la procédure.  
  
 Pour retourner une valeur à partir d’une fonction, vous pouvez affecter la valeur pour le nom de fonction ou l’inclure dans un `Return` instruction.  
  
 La `Return` instruction assigne la valeur de retour et quitte la fonction, comme le montre l’exemple suivant simultanément.  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_1.vb)]  
  
 L’exemple suivant affecte la valeur de retour pour le nom de fonction `myFunction` , puis utilise la `Exit Function` instruction à retourner.  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_2.vb)]  
  
 Le `Exit Function` et `Return` instructions provoquent la sortie immédiate d’un `Function` procédure. Un nombre quelconque de `Exit Function` et `Return` instructions peuvent apparaître n’importe où dans la procédure, et vous pouvez mélanger `Exit Function` et `Return` instructions.  
  
 Si vous utilisez `Exit Function` sans lui assigner une valeur à `name`, la procédure retourne la valeur par défaut pour le type de données qui est spécifié dans `returntype`. Si `returntype` n’est pas spécifié, la procédure retourne `Nothing`, qui est la valeur par défaut `Object`.  
  
## <a name="calling-a-function"></a>Appel d’une fonction  
 Vous appelez un `Function` procédure en utilisant le nom de la procédure, suivi de la liste d’arguments entre parenthèses, dans une expression. Vous pouvez omettre les parenthèses uniquement si vous ne fournissez des arguments. Toutefois, votre code est plus lisible si vous incluez toujours les parenthèses.  
  
 Vous appelez un `Function` procédure fonctionne de la même façon que vous appelez n’importe quelle bibliothèque comme `Sqrt`, `Cos`, ou `ChrW`.  
  
 Vous pouvez également appeler une fonction à l’aide de la `Call` (mot clé). Dans ce cas, la valeur de retour est ignorée. Utilisation de la `Call` mot clé n’est pas recommandée dans la plupart des cas. Pour plus d’informations, consultez [instruction Call](call-statement.md).  
  
 Visual Basic réorganise quelquefois les expressions arithmétiques pour améliorer les performances internes. Pour cette raison, vous ne devez pas utiliser un `Function` procédure dans une expression arithmétique lorsque la fonction modifie la valeur des variables dans la même expression.  
  
## <a name="async-functions"></a>Fonctions Async  
 Le *Async* fonctionnalité vous permet d’appeler des fonctions asynchrones sans utiliser de rappels explicites ni fractionner manuellement votre code entre plusieurs fonctions ou expressions lambda.  
  
 Si vous marquez une fonction avec la [Async](../../../visual-basic/language-reference/modifiers/async.md) modificateur, vous pouvez utiliser la [Await](../../../visual-basic/language-reference/operators/await-operator.md) opérateur dans la fonction. Quand le contrôle atteint une `Await` expression dans le `Async` (fonction), contrôle retourne à l’appelant, et la progression de la fonction est interrompue jusqu'à ce que la tâche attendue se termine. Lorsque la tâche est terminée, l’exécution peut reprendre dans la fonction.  
  
> [!NOTE]
>  Un `Async` procédure retourne à l’appelant quand il rencontre le premier objet await qui n’est pas encore terminé ou qu’il arrive à la fin de la `Async` procédure, selon ce qui se produit en premier.  
  
 Un `Async` fonction peut avoir un type de retour de <xref:System.Threading.Tasks.Task%601> ou <xref:System.Threading.Tasks.Task>. Un exemple d’une `Async` fonction qui a un type de retour de <xref:System.Threading.Tasks.Task%601> est fourni ci-dessous.  
  
 Un `Async` fonction ne peut pas déclarer de [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) paramètres.  
  
 A [Sub, instruction](sub-statement.md) peuvent également être marquées avec le `Async` modificateur. Cela est principalement utilisé pour les gestionnaires d’événements, où une valeur ne peut pas être retournée. Un `Async``Sub` procédure ne peut pas être attendue et que l’appelant d’une `Async``Sub` procédure ne peut pas intercepter les exceptions levées par le `Sub` procédure.  
  
 Pour plus d’informations sur `Async` fonctions, consultez [programmation asynchrone avec Async et Await](../../../visual-basic/programming-guide/concepts/async/index.md), [flux de contrôle dans les programmes Async](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), et [Types de retour Async](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="iterator-functions"></a>Fonctions d’itérateur  
 Un *itérateur* fonction effectue une itération personnalisée sur une collection, comme une liste ou un tableau. Une fonction d’itérateur utilise le [Yield](yield-statement.md) instruction pour retourner chaque élément un par un. Lorsqu’un [Yield](yield-statement.md) instruction est atteinte, l’emplacement actuel dans le code est mémorisé. L’exécution est redémarrée à partir de cet emplacement lors de l’appel suivant de la fonction d’itérateur.  
  
 Vous appelez un itérateur depuis le code client en utilisant un [For Each... Suivant](for-each-next-statement.md) instruction.  
  
 Le type de retour d’une fonction d’itérateur peut être <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, ou <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Pour plus d’informations, consultez [Itérateurs](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le `Function` instruction pour déclarer le nom, des paramètres et que le code qui forment le corps d’un `Function` procédure. Le `ParamArray` modificateur permet à la fonction d’accepter un nombre variable d’arguments.  
  
 [!code-vb[VbVbalrStatements#25](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_3.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant appelle la fonction déclarée dans l’exemple précédent.  
  
 [!code-vb[VbVbalrStatements#26](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_4.vb)]  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, `DelayAsync` est un `Async``Function` qui a un type de retour de <xref:System.Threading.Tasks.Task%601>. `DelayAsync` a une instruction `Return` qui retourne un entier. Par conséquent, la déclaration de fonction de `DelayAsync` doit avoir un type de retour de `Task(Of Integer)`. Étant donné que le type de retour est `Task(Of Integer)`, l’évaluation de la `Await` expression dans `DoSomethingAsync` produit un entier. Cela est illustré dans cette déclaration : `Dim result As Integer = Await delayTask`.  
  
 Le `startButton_Click` procédure est un exemple d’un `Async Sub` procédure. Étant donné que `DoSomethingAsync` est un `Async` la tâche pour l’appel à une fonction, `DoSomethingAsync` doit être attendue, comme l’instruction suivante illustre : `Await DoSomethingAsync()`. Le `startButton_Click``Sub` procédure doit être définie avec la `Async` modificateur, car il possède un `Await` expression.  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/function-statement_5.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Sub (instruction)](sub-statement.md)  
 [Procédures Function](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)  
 [Liste de paramètres](parameter-list.md)  
 [Dim (instruction)](dim-statement.md)  
 [Call (instruction)](call-statement.md)  
 [Of](of-clause.md)  
 [tableaux de paramètres](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)  
 [Guide pratique : utiliser une classe générique](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Procédures de dépannage](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)  
 [Expressions lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [Expression de fonction](../../../visual-basic/language-reference/operators/function-expression.md)
