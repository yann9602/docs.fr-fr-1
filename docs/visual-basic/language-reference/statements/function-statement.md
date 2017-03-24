---
title: Function, instruction (Visual Basic) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Function
dev_langs:
- VB
helpviewer_keywords:
- procedures, creating
- Function procedures, Function statement syntax
- functions [Visual Basic], function procedures
- ParamArray keyword, Function statements
- Private keyword, Function statements
- declarations, procedures
- procedures, declaration
- Public keyword, in Function statement
- ByVal keyword, Function statements
- procedures, recursive
- Implements keyword, Function statements
- procedures, returning values
- Exit statement, in Function procedures
- recursive procedures
- As keyword, in Function statement
- Optional keyword, Function statements
- Function statement
- Visual Basic code, Function procedures
- procedures, function
- ByRef keyword, Function statements
- Friend keyword, Function statements
- End keyword, Function statements
- Handles keyword, Function statements
ms.assetid: a4497077-0f46-4ede-a27f-9e8670df52b9
caps.latest.revision: 62
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: af87477f81fab8406d726ebc8c81260b371d71c8
ms.lasthandoff: 03/13/2017

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
  
     Facultatif. Consultez la page [liste d’attributs](attribute-list.md).  
  
-   `accessmodifier`  
  
     Facultatif. Il peut s'agir d'une des valeurs suivantes :  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     Consultez la page [niveaux en Visual Basic d’accès](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
-   `proceduremodifiers`  
  
     Facultatif. Il peut s'agir d'une des valeurs suivantes :  
  
    -   [Surcharges](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     Facultatif. Consultez la page [partagé](../../../visual-basic/language-reference/modifiers/shared.md).  
  
-   `Shadows`  
  
     Facultatif. Consultez la page [ombres](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
-   `Async`  
  
     Facultatif. Consultez la page [Async](../../../visual-basic/language-reference/modifiers/async.md).  
  
-   `Iterator`  
  
     Facultatif. Consultez la page [itérateur](../../../visual-basic/language-reference/modifiers/iterator.md).  
  
-   `name`  
  
     Obligatoire. Nom de la procédure. Consultez la page [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   `typeparamlist`  
  
     Facultatif. Liste des paramètres de type pour une procédure générique. Consultez la page [tapez liste](type-list.md).  
  
-   `parameterlist`  
  
     Facultatif. Liste des noms de variables locales représentant les paramètres de cette procédure. Consultez la page [liste de paramètres](parameter-list.md).  
  
-   `returntype`  
  
     Requis si `Option Strict` est `On`. Type de données de la valeur retournée par cette procédure.  
  
-   `Implements`  
  
     Facultatif. Indique que cette procédure implémente une ou plusieurs `Function` procédures, chacune étant définie dans une interface implémentée par la classe ou la structure conteneur de cette procédure. Consultez la page [implémente l’instruction](implements-statement.md).  
  
-   `implementslist`  
  
     Obligatoire si `Implements` est utilisé. Liste des procédures `Function` en cours d'implémentation.  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     Chaque `implementedprocedure` emploie la syntaxe et les éléments suivants :  
  
     `interface.definedname`  
  
    |Élément|Description|  
    |---|---|  
    |`interface`|Obligatoire. Nom d’une interface implémentée par cette procédure classe ou la structure conteneur.|  
    |`definedname`|Obligatoire. Nom par lequel la procédure est définie dans `interface`.|  
  
-   `Handles`  
  
     Facultatif. Indique que cette procédure peut gérer un ou plusieurs événements spécifiques. Consultez la page [gère](handles-clause.md).  
  
-   `eventlist`  
  
     Obligatoire si `Handles` est utilisé. Liste des événements gérés par cette procédure.  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     Chaque `eventspecifier` emploie la syntaxe et les éléments suivants :  
  
     `eventvariable.event`  
  
    |Élément|Description|  
    |---|---|  
    |`eventvariable`|Obligatoire. Variable objet déclarée avec le type de données de la classe ou structure qui déclenche l’événement.|  
    |`event`|Obligatoire. Nom de l’événement que gère cette procédure.|  
  
-   `statements`  
  
     Facultatif. Bloc d’instructions à exécuter dans cette procédure.  
  
-   `End Function`  
  
     Met fin à la définition de cette procédure.  
  
## <a name="remarks"></a>Remarques  
 Tout le code exécutable doit être à l’intérieur d’une procédure. Chaque procédure, à son tour, est déclarée dans une classe, une structure ou un module qui correspond à la classe, structure ou module conteneur.  
  
 Pour retourner une valeur au code appelant, utilisez un `Function` procédure ; sinon, utilisez un `Sub` procédure.  
  
## <a name="defining-a-function"></a>Définition d’une fonction  
 Vous pouvez définir un `Function` procédure uniquement au niveau du module. Par conséquent, le contexte de déclaration pour une fonction doit être une classe, une structure, un module ou une interface et ne peut pas être un fichier source, un espace de noms, une procédure ou un bloc. Pour plus d’informations, consultez [contextes de déclaration et niveaux d’accès par défaut](declaration-contexts-and-default-access-levels.md).  
  
 `Function`les procédures par défaut d’un accès public. Vous pouvez régler leurs niveaux d’accès avec les modificateurs d’accès.  
  
 Un `Function` procédure peut déclarer le type de données de la valeur renvoyée de la procédure. Vous pouvez spécifier n’importe quel type de données ou le nom d’une énumération, une structure, une classe ou une interface. Si vous ne spécifiez pas le `returntype` , la procédure retourne `Object`.  
  
 Si cette procédure utilise le `Implements` (mot clé), la classe ou la structure conteneur doit également avoir un `Implements` instruction qui suit immédiatement sa `Class` ou `Structure` instruction. Le `Implements` instruction doit inclure chaque interface spécifiée dans `implementslist`. Toutefois, le nom par lequel une interface définit les `Function` (dans `definedname`) n’a pas besoin de correspondre au nom de cette procédure (dans `name`).  
  
> [!NOTE]
>  Vous pouvez utiliser des expressions lambda pour définir des expressions de fonction inline. Pour plus d’informations, consultez [Expression de fonction](../../../visual-basic/language-reference/operators/function-expression.md) et [Expressions Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
## <a name="returning-from-a-function"></a>Retour d’une fonction  
 Lorsque le `Function` procédure retourne au code appelant, l’exécution se poursuit avec l’instruction qui suit l’instruction qui a appelé la procédure.  
  
 Pour retourner une valeur à partir d’une fonction, vous pouvez assigner la valeur au nom de la fonction ou l’inclure dans un `Return` instruction.  
  
 La `Return` instruction assigne la valeur de retour et quitte la fonction, comme le montre l’exemple suivant simultanément.  
  
 [!code-vb[VbVbalrStatements&#24;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_1.vb)]  
  
 L’exemple suivant affecte la valeur de retour pour le nom de la fonction `myFunction` , puis utilise la `Exit Function` instruction à retourner.  
  
 [!code-vb[VbVbalrStatements n °&23;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_2.vb)]  
  
 Le `Exit Function` et `Return` instructions provoquent la sortie immédiate d’un `Function` procédure. Un nombre quelconque de `Exit Function` et `Return` instructions peuvent apparaître n’importe où dans la procédure, et vous pouvez mélanger `Exit Function` et `Return` instructions.  
  
 Si vous utilisez `Exit Function` sans assigner une valeur à `name`, la procédure retourne la valeur par défaut pour le type de données spécifié dans `returntype`. Si `returntype` n’est pas spécifié, la procédure retourne `Nothing`, qui est la valeur par défaut `Object`.  
  
## <a name="calling-a-function"></a>Appel d’une fonction  
 Vous appelez un `Function` procédure en utilisant le nom de procédure, suivi de la liste d’arguments entre parenthèses, dans une expression. Vous pouvez omettre les parenthèses uniquement si vous ne fournissez des arguments. Toutefois, votre code est plus lisible si vous incluez toujours les parenthèses.  
  
 Vous appelez un `Function` procédure fonctionne de la même façon que vous appelez n’importe quelle bibliothèque comme `Sqrt`, `Cos`, ou `ChrW`.  
  
 Vous pouvez également appeler une fonction à l’aide de la `Call` (mot clé). Dans ce cas, la valeur de retour est ignorée. Utilisation de le `Call` mot clé n’est pas recommandé dans la plupart des cas. Pour plus d’informations, consultez [instruction Call](call-statement.md).  
  
 Visual Basic réorganise quelquefois les expressions arithmétiques pour améliorer les performances internes. Pour cette raison, vous ne devez pas utiliser un `Function` procédure dans une expression arithmétique quand la fonction change la valeur des variables dans la même expression.  
  
## <a name="async-functions"></a>Fonctions asynchrones  
 Le *Async* fonctionnalité vous permet d’appeler des fonctions asynchrones sans utiliser de rappels explicites ou fractionner manuellement votre code entre plusieurs fonctions ou expressions lambda.  
  
 Si vous marquez une fonction avec la [Async](../../../visual-basic/language-reference/modifiers/async.md) modificateur, vous pouvez utiliser la [Await](../../../visual-basic/language-reference/operators/await-operator.md) opérateur dans la fonction. Lorsque le contrôle atteint une `Await` expression dans le `Async` (fonction), contrôle retourne à l’appelant, et la progression dans la fonction est suspendue jusqu'à ce que la tâche attendue se termine. Lorsque la tâche est terminée, l’exécution peut reprendre dans la fonction.  
  
> [!NOTE]
>  Un `Async` procédure retourne à l’appelant lorsqu’il rencontre le premier objet await qui n’est pas encore terminé ou qu’il arrive à la fin de la `Async` procédure, selon ce qui se produit en premier.  
  
 Un `Async` fonction peut avoir un type de retour de <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.Task>.</xref:System.Threading.Tasks.Task> </xref:System.Threading.Tasks.Task%601> Un exemple d’une `Async` fonction qui a un type de retour de <xref:System.Threading.Tasks.Task%601>est fourni ci-dessous.</xref:System.Threading.Tasks.Task%601>  
  
 Un `Async` fonction ne peut pas déclarer de [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) paramètres.  
  
 A [Sub, instruction](sub-statement.md) peuvent également être marqués avec le `Async` modificateur. Cela est principalement utilisé pour les gestionnaires d’événements, où une valeur ne peut pas être retournée. Un `Async``Sub` procédure ne peut pas être attendue et que l’appelant d’une `Async``Sub` procédure ne peut pas intercepter des exceptions levées par le `Sub` procédure.  
  
 Pour plus d’informations sur `Async` , consultez [programmation asynchrone avec Async et Await](../../../visual-basic/programming-guide/concepts/async/index.md), [flux de contrôle dans les programmes Async](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), et [les Types de retour Async](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="iterator-functions"></a>Fonctions d’itérateur  
 Un *itérateur* fonction effectue une itération personnalisée sur une collection, par exemple, une liste ou un tableau. Une fonction d’itérateur utilise le [Yield](yield-statement.md) instruction pour retourner chaque élément un à la fois. Lorsqu’un [Yield](yield-statement.md) instruction est atteinte, l’emplacement actuel dans le code est mémorisé. L’exécution redémarrera à partir de cet emplacement la prochaine fois que la fonction d’itérateur est appelée.  
  
 Vous appelez un itérateur depuis le code client en utilisant un [For Each... Suivant](for-each-next-statement.md) instruction.  
  
 Le type de retour d’une fonction d’itérateur peut être <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, ou <xref:System.Collections.Generic.IEnumerator%601>.</xref:System.Collections.Generic.IEnumerator%601> </xref:System.Collections.IEnumerator> </xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.IEnumerable>  
  
 Pour plus d’informations, consultez [Itérateurs](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le `Function` instruction pour déclarer le nom, les paramètres et les code formant le corps d’un `Function` procédure. Le `ParamArray` modificateur permet à la fonction d’accepter un nombre variable d’arguments.  
  
 [!code-vb[VbVbalrStatements&#25;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_3.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant appelle la fonction déclarée dans l’exemple précédent.  
  
 [!code-vb[VbVbalrStatements&#26;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_4.vb)]  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, `DelayAsync` est un `Async``Function` qui a un type de retour de <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601> `DelayAsync` a une instruction `Return` qui retourne un entier. Par conséquent, la déclaration de fonction de `DelayAsync` doit avoir un type de retour de `Task(Of Integer)`. Étant donné que le type de retour est `Task(Of Integer)`, l’évaluation de la `Await` expression dans `DoSomethingAsync` génère un nombre entier. Cela est illustré dans cette déclaration : `Dim result As Integer = Await delayTask`.  
  
 Le `startButton_Click` procédure est un exemple d’un `Async Sub` procédure. Étant donné que `DoSomethingAsync` est un `Async` la tâche pour l’appel à une fonction, `DoSomethingAsync` doit être attendue, comme le montre l’instruction suivante : `Await DoSomethingAsync()`. Le `startButton_Click``Sub` procédure doit être définie avec la `Async` modificateur, car elle possède une `Await` expression.  
  
 [!code-vb[csAsyncMethod n °&1;](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/function-statement_5.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Sub (instruction)](sub-statement.md)   
 [Procédures Function](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Liste de paramètres](parameter-list.md)   
 [Dim (instruction)](dim-statement.md)   
 [Call, instruction](call-statement.md)   
 [Of](of-clause.md)   
 [Tableaux de paramètres](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)   
 [Comment : utiliser une classe générique](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)   
 [Procédures de dépannage](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)   
 [Expressions lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [Expression de fonction](../../../visual-basic/language-reference/operators/function-expression.md)
