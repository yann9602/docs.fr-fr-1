---
title: Sub, instruction (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Sub
helpviewer_keywords:
- Public keyword [Visual Basic], Sub statements
- procedures [Visual Basic], creating
- declaring procedures [Visual Basic], Sub statement
- arguments [Visual Basic], Sub procedures
- As keyword [Visual Basic], Sub statements
- Optional keyword [Visual Basic], Sub statements
- declarations [Visual Basic], procedures
- Sub keyword [Visual Basic]
- Handles keyword [Visual Basic], Sub statements
- Protected Friend keyword [Visual Basic]
- ParamArray keyword [Visual Basic], Sub statements
- Implements keyword [Visual Basic], Sub statements
- Sub statement [Visual Basic]
- subroutines
- ByRef keyword [Visual Basic], Sub statements
- Sub procedures [Visual Basic], Sub statement
- recursive procedures
- Private keyword [Visual Basic], Sub statements
- Friend keyword [Visual Basic], Sub statements
- Exit statement [Visual Basic], Sub statements
- procedures [Visual Basic], Sub
- End keyword [Visual Basic], Sub statements
- ByVal keyword [Visual Basic], Sub statements
- Visual Basic code, Sub procedures
ms.assetid: e347d700-d06c-405b-b302-e9b1edb57dfc
caps.latest.revision: "52"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0a2d0d5ffdca857a3a5ca58cd38b0930f254526f
ms.sourcegitcommit: 8ed4ebc15b5ef89d06a7507dc9d5e306e30accf7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2017
---
# <a name="sub-statement-visual-basic"></a>Sub, instruction (Visual Basic)
Déclare le nom, paramètres et le code qui définissent une `Sub` procédure.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]  
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Sub ]  
    [ statements ]  
End Sub  
```  
  
## <a name="parts"></a>Composants  
  
-   `attributelist`  
  
     Facultatif. Consultez [liste d’attributs](attribute-list.md).  
  
-   `Partial`  
  
     Facultatif. Indique la définition d’une méthode partielle. Consultez [méthodes partielles](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).  
  
-   `accessmodifier`  
  
     Facultatif. Il peut s'agir d'une des valeurs suivantes :  
  
    -   [Public](../modifiers/public.md)  
  
    -   [Protected](../modifiers/protected.md)  
  
    -   [Friend](../modifiers/friend.md)  
  
    -   [Private](../modifiers/private.md)  
  
    -   `Protected Friend`  
  
     Consultez [niveaux en Visual Basic d’accès](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
-   `proceduremodifiers`  
  
     Facultatif. Il peut s'agir d'une des valeurs suivantes :  
  
    -   [Overloads](../modifiers/overloads.md)  
  
    -   [Overrides](../modifiers/overrides.md)  
  
    -   [Overridable](../modifiers/overridable.md)  
  
    -   [NotOverridable](../modifiers/notoverridable.md)  
  
    -   [MustOverride](../modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     Facultatif. Consultez [partagé](../modifiers/shared.md).  
  
-   `Shadows`  
  
     Facultatif. Consultez [ombres](../modifiers/shadows.md).  
  
-   `Async`  
  
     Facultatif. Consultez [Async](../modifiers/async.md).  
  
-   `name`  
  
     Obligatoire. Nom de la procédure. Consultez [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md). Pour créer une procédure de constructeur pour une classe, définissez le nom d’un `Sub` procédure pour le `New` (mot clé). Pour plus d’informations, consultez [durée de vie : comment les objets sont création et destruction](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).  
  
-   `typeparamlist`  
  
     Facultatif. Liste de paramètres de type pour une procédure générique. Consultez [tapez liste](type-list.md).  
  
-   `parameterlist`  
  
     Facultatif. Liste des noms de variables locales représentant les paramètres de cette procédure. Consultez [liste de paramètres](parameter-list.md).  
  
-   `Implements`  
  
     Facultatif. Indique que cette procédure implémente une ou plusieurs `Sub` procédures, chacune étant définie dans une interface implémentée par la classe ou la structure conteneur de cette procédure. Consultez [implémente l’instruction](implements-statement.md).  
  
-   `implementslist`  
  
     Obligatoire si `Implements` est utilisé. Liste des procédures `Sub` en cours d'implémentation.  
  
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
  
-   `End Sub`  
  
     Termine la définition de cette procédure.  
  
## <a name="remarks"></a>Remarques  
 Tout le code exécutable doit être à l’intérieur d’une procédure. Utilisez un `Sub` procédure lorsque vous ne souhaitez pas retourner une valeur au code appelant. Utilisez un `Function` procédure lorsque vous souhaitez retourner une valeur.  
  
## <a name="defining-a-sub-procedure"></a>Définition d’une procédure Sub  
 Vous pouvez définir un `Sub` procédure uniquement au niveau du module. Le contexte de déclaration pour une procédure sub doit, par conséquent, être une classe, une structure, un module ou une interface et ne peut pas être un fichier source, un espace de noms, une procédure ou un bloc. Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](declaration-contexts-and-default-access-levels.md).  
  
 `Sub`les procédures par défaut d’un accès public. Vous pouvez ajuster leurs niveaux d’accès à l’aide des modificateurs d’accès.  
  
 Si la procédure utilise le `Implements` (mot clé), la classe ou la structure conteneur doit avoir un `Implements` instruction qui suit immédiatement sa `Class` ou `Structure` instruction. Le `Implements` instruction doit inclure chaque interface spécifiée dans `implementslist`. Toutefois, le nom par lequel une interface définit les `Sub` (dans `definedname`) ne doit pas nécessairement correspondre au nom de cette procédure (dans `name`).  
  
## <a name="returning-from-a-sub-procedure"></a>Retour à partir d’une procédure Sub  
 Lorsqu’un `Sub` procédure retourne au code appelant, l’exécution se poursuit avec l’instruction après l’instruction qui l’a appelée.  
  
 L’exemple suivant montre un retour d’un `Sub` procédure.  
  
```vb  
Sub mySub(ByVal q As String)  
    Return  
End Sub   
```  
  
 Le `Exit Sub` et `Return` instructions provoquent la sortie immédiate d’un `Sub` procédure. Un nombre quelconque de `Exit Sub` et `Return` instructions peuvent apparaître n’importe où dans la procédure, et vous pouvez mélanger `Exit Sub` et `Return` instructions.  
  
## <a name="calling-a-sub-procedure"></a>Appel d’une procédure Sub  
 Vous appelez un `Sub` procédure en utilisant le nom de la procédure dans une instruction et en suivant ce nom à sa liste d’arguments entre parenthèses. Vous pouvez omettre les parenthèses uniquement si vous ne fournissez pas d’arguments. Toutefois, votre code est plus lisible si vous incluez toujours les parenthèses.  
  
 A `Sub` procédure et un `Function` procédure peut avoir des paramètres et exécuter une série d’instructions. Toutefois, un `Function` procédure retourne une valeur et qu’une `Sub` ne de procédure. Par conséquent, vous ne pouvez pas utiliser un `Sub` procédure dans une expression.  
  
 Vous pouvez utiliser la `Call` mot clé lorsque vous appelez un `Sub` procédure, mais ce mot clé n’est pas recommandé pour la plupart des utilisations. Pour plus d’informations, consultez [instruction Call](call-statement.md).  
  
 Visual Basic réorganise quelquefois les expressions arithmétiques pour améliorer les performances internes. Pour cette raison, si votre liste d’arguments inclut des expressions qui appellent d’autres procédures, vous ne devez pas supposer que que ces expressions seront appelées dans un ordre particulier.  
  
## <a name="async-sub-procedures"></a>Procédures Sub Async  
 À l’aide de la fonctionnalité Async, vous pouvez appeler des fonctions asynchrones sans utiliser de rappels explicites ni fractionner manuellement votre code entre plusieurs fonctions ou expressions lambda.  
  
 Si vous marquez une procédure avec le [Async](../modifiers/async.md) modificateur, vous pouvez utiliser la [Await](../../../visual-basic/language-reference/operators/await-operator.md) opérateur dans la procédure. Quand le contrôle atteint une `Await` expression dans le `Async` procédure, contrôle retourne à l’appelant, et la progression de la procédure est interrompue jusqu'à ce que la tâche attendue se termine. Lorsque la tâche est terminée, l’exécution peut reprendre dans la procédure.  
  
> [!NOTE]
>  Un `Async` procédure retourne à l’appelant quand soit le premier objet await qui n’est pas encore terminé est rencontrée ou à la fin de la `Async` procédure est atteint, selon ce qui se produit en premier.  
  
 Vous pouvez également marquer un [Function, instruction](function-statement.md) avec la `Async` modificateur. Un `Async` fonction peut avoir un type de retour de <xref:System.Threading.Tasks.Task%601> ou <xref:System.Threading.Tasks.Task>. Un exemple plus loin dans cette rubrique montre un `Async` fonction qui a un type de retour de <xref:System.Threading.Tasks.Task%601>.  
  
 `Async``Sub` procédures sont principalement utilisés pour les gestionnaires d’événements, où une valeur ne peut pas être retournée. Un `Async``Sub` procédure ne peut pas être attendue et que l’appelant d’une `Async``Sub` procédure ne peut pas intercepter des exceptions qui le `Sub` lève une exception de la procédure.  
  
 Un `Async` procédure ne peut pas déclarer de [ByRef](../modifiers/byref.md) paramètres.  
  
 Pour plus d’informations sur `Async` les procédures, consultez [programmation asynchrone avec Async et Await](../../../visual-basic/programming-guide/concepts/async/index.md), [flux de contrôle dans les programmes Async](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), et [Types de retour Async](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le `Sub` instruction afin de définir le nom, des paramètres et que le code qui forment le corps d’un `Sub` procédure.  
  
 [!code-vb[VbVbalrStatements#58](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/sub-statement_1.vb)]  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, `DelayAsync` est un `Async``Function` qui a un type de retour de <xref:System.Threading.Tasks.Task%601>. `DelayAsync` a une instruction `Return` qui retourne un entier. Par conséquent, la déclaration de fonction de `DelayAsync` doit avoir un type de retour de `Task(Of Integer)`. Étant donné que le type de retour est `Task(Of Integer)`, l’évaluation de la `Await` expression dans `DoSomethingAsync` produit un entier, comme le montre l’instruction suivante : `Dim result As Integer = Await delayTask`.  
  
 Le `startButton_Click` procédure est un exemple d’un `Async Sub` procédure. Étant donné que `DoSomethingAsync` est un `Async` la tâche pour l’appel à une fonction, `DoSomethingAsync` doit être attendue, comme le montre l’instruction suivante : `Await DoSomethingAsync()`. Le `startButton_Click``Sub` procédure doit être définie avec la `Async` modificateur, car il possède un `Await` expression.  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/sub-statement_2.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Implements (instruction)](implements-statement.md)  
 [Function (instruction)](function-statement.md)  
 [Liste de paramètres](parameter-list.md)  
 [Dim (instruction)](dim-statement.md)  
 [Call (instruction)](call-statement.md)  
 [Of](of-clause.md)  
 [tableaux de paramètres](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)  
 [Guide pratique : utiliser une classe générique](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Procédures de dépannage](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)  
 [Méthodes partielles](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
