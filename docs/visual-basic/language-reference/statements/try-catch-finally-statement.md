---
title: Try...Catch...Finally, instruction (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Try...Catch...Finally
- vb.when
- vb.Finally
- vb.Catch
- vb.Try
helpviewer_keywords:
- Try...Catch...Finally statements
- Try statement [Visual Basic]
- try-catch exception handling, Try...Catch...Finally statements
- error handling, while running code
- Try statement [Visual Basic], Try...Catch...Finally
- Finally keyword [Visual Basic], Try...Catch...Finally
- Catch statement [Visual Basic]
- When keyword [Visual Basic]
- Visual Basic code, handling errors while running
- structured exception handling, Try...Catch...Finally statements
ms.assetid: d6488026-ccb3-42b8-a810-0d97b9d6472b
caps.latest.revision: "69"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 56dd7fc339c452d64eb18211337b9a7674a83e1c
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2017
---
# <a name="trycatchfinally-statement-visual-basic"></a>Try...Catch...Finally, instruction (Visual Basic)
Fournit un moyen de gérer certaines ou toutes les erreurs possibles qui peuvent se produire dans un bloc de code donné lors de code en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Try  
    [ tryStatements ]  
    [ Exit Try ]  
[ Catch [ exception [ As type ] ] [ When expression ]  
    [ catchStatements ]  
    [ Exit Try ] ]  
[ Catch ... ]  
[ Finally  
    [ finallyStatements ] ]  
End Try  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`tryStatements`|Facultatif. Instructions où une erreur peut se produire. Il peut s'agir d'une instruction composée.|  
|`Catch`|Facultatif. Plusieurs `Catch` blocs autorisés. Si une exception se produit lors du traitement de la `Try` bloquer, chacun `Catch` instruction est examinée dans l’ordre textuel afin de déterminer si elle gère l’exception, avec `exception` représentant l’exception qui a été levée.|  
|`exception`|Facultatif. Tout nom de variable. La valeur initiale de l'argument `exception` est la valeur de l'erreur levée. Utilisé avec `Catch` pour spécifier l’erreur interceptée. Si omis, la `Catch` instruction intercepte toute exception.|  
|`type`|Facultatif. Spécifie le type de filtre de la classe. Si la valeur de `exception` est du type spécifié par `type` ou d’un type dérivé, l’identificateur est lié à l’objet exception.|  
|`When`|Facultatif. A `Catch` instruction avec un `When` clause intercepte les exceptions uniquement lorsque `expression` prend la valeur `True`. A `When` clause est appliquée uniquement après la vérification du type de l’exception, et `expression` peut faire référence à l’identificateur qui représente l’exception.|  
|`expression`|Facultatif. Doit être implicitement convertible en `Boolean`. Toute expression qui décrit un filtre générique. En général permet de filtrer par numéro d’erreur. Utilisé avec `When` mot clé pour spécifier les circonstances dans lesquelles l’erreur est interceptée.|  
|`catchStatements`|Facultatif. Instructions permettant de gérer les erreurs qui se produisent dans le type `Try` bloc. Il peut s'agir d'une instruction composée.|  
|`Exit Try`|Facultatif. Mot clé qui décompose le `Try...Catch...Finally` structure. L’exécution se poursuit avec le code qui suit immédiatement la `End Try` instruction. La `Finally` instruction sera exécutée. Interdit dans `Finally` blocs.|  
|`Finally`|Facultatif. A `Finally` bloc est toujours exécuté quand l’exécution quitte une partie de la `Try...Catch` instruction.|  
|`finallyStatements`|Facultatif. Instructions qui sont exécutées une fois que tout autre traitement d’erreur s’est produite.|  
|`End Try`|Met fin à la `Try...Catch...Finally` structure.|  
  
## <a name="remarks"></a>Remarques  
 Si vous pensez qu’une exception particulière se produise pendant une section particulière de code, placez le code dans un `Try` bloquer et d’utiliser un `Catch` bloc pour conserver le contrôle et de gérer l’exception si elle se produit.  
  
 A `Try…Catch` instruction se compose d’un `Try` bloc suivi par une ou plusieurs `Catch` clauses qui spécifient des gestionnaires pour différentes exceptions. Lorsqu’une exception est levée dans un `Try` bloc, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] recherche le `Catch` instruction qui gère l’exception. Si une correspondance `Catch` instruction n’est trouvée, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] examine la méthode qui a appelé la méthode actuelle, et ainsi de suite la pile des appels. Si aucun `Catch` bloc est trouvé, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] affiche un message d’exception non gérée à l’utilisateur et arrête l’exécution du programme.  
  
 Vous pouvez utiliser plusieurs `Catch` instruction dans un `Try…Catch` instruction. Dans ce cas, l’ordre de la `Catch` clauses est important, car ils sont examinés dans l’ordre. Interceptez les exceptions plus spécifiques avant les moins spécifiques.  
  
 Les éléments suivants `Catch` conditions de l’instruction sont les moins spécifiques et intercepte toutes les exceptions qui dérivent de la <xref:System.Exception> classe. Vous devez normalement utiliser une de ces variations comme dernier `Catch` bloquer la `Try...Catch...Finally` structure, après avoir intercepté toutes les exceptions spécifiques que vous attendez. Flux de contrôle ne peut jamais atteindre un `Catch` bloc qui suit une de ces variantes.  
  
-   Le `type` est `Exception`, par exemple :`Catch ex As Exception`  
  
-   L’instruction n’a aucun `exception` variable, par exemple :`Catch`  
  
 Lorsqu’un `Try…Catch…Finally` instruction est imbriquée dans une autre `Try` bloc, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] examine d’abord chaque `Catch` instruction à l’intérieur `Try` bloc. Si aucune correspondance `Catch` instruction est trouvée, la recherche se poursuit vers le `Catch` instructions d’externe `Try…Catch…Finally` bloc.  
  
 Les variables locales d’un `Try` bloc ne sont pas disponibles dans un `Catch` bloqué, car ils sont des blocs séparés. Si vous souhaitez utiliser une variable dans plusieurs blocs, déclarez la variable en dehors de la `Try...Catch...Finally` structure.  
  
> [!TIP]
>  La `Try…Catch…Finally` instruction n’est disponible en tant qu’un extrait de code IntelliSense. Dans le Gestionnaire des extraits de Code, développez **modèles de Code - If, For Each, Try Catch, propriété, etc.**, puis **(Exceptions) de gestion des erreurs**. Pour plus d’informations, consultez [Extraits de code](/visualstudio/ide/code-snippets).  
  
## <a name="finally-block"></a>Finally (bloc)  
 Si vous avez une ou plusieurs instructions qui doivent s’exécuter avant de quitter la `Try` de la structure, utilisez un `Finally` bloc. Le contrôle passe à la `Finally` bloquer juste avant du `Try…Catch` structure. Cela est vrai même si une exception se produit n’importe où à l’intérieur de la `Try` structure.  
  
 A `Finally` bloc est utile pour l’exécution de tout code qui doit s’exécuter même s’il existe une exception. Le contrôle est passé à la `Finally` bloc quelle que soit la façon dont le `Try...Catch` bloc se termine.  
  
 Le code dans un `Finally` bloc s’exécute même si votre code rencontre une `Return` instruction dans un `Try` ou `Catch` bloc. Contrôle ne passe pas d’un `Try` ou `Catch` bloquer correspondant `Finally` bloquer dans les cas suivants :  
  
-   Un [l’instruction End](../../../visual-basic/language-reference/statements/end-statement.md) est rencontré dans le `Try` ou `Catch` bloc.  
  
-   A <xref:System.StackOverflowException> est levée dans le `Try` ou `Catch` bloc.  
  
 Il n’est pas valide pour transférer explicitement l’exécution dans un `Finally` bloc. Transfert de l’exécution d’un `Finally` bloc n’est pas valide, sauf via une exception.  
  
 Si un `Try` instruction ne contient pas au moins un `Catch` bloc, il doit contenir un `Finally` bloc.  
  
> [!TIP]
>  Si vous n’avez pas à intercepter des exceptions spécifiques, le `Using` instruction se comporte comme un `Try…Finally` bloc et garantit l’élimination des ressources, quelle que soit la manière dont vous quittez le bloc. Cela est vrai même avec une exception non gérée. Pour plus d’informations, consultez [using, instruction](../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="exception-argument"></a>Argument d’exception  
 Le `Catch` bloc `exception` argument est une instance de la <xref:System.Exception> classe ou une classe qui dérive de la `Exception` classe. Le `Exception` instance de la classe correspond à l’erreur qui s’est produite dans le `Try` bloc.  
  
 Les propriétés de la `Exception` permettent d’identifier la cause et l’emplacement d’une exception de l’objet. Par exemple, le <xref:System.Exception.StackTrace%2A> propriété répertorie les méthodes appelées qui a provoqué l’exception, vous permettant de trouver où l’erreur s’est produite dans le code. <xref:System.Exception.Message%2A>Retourne un message qui décrit l’exception. <xref:System.Exception.HelpLink%2A>Renvoie un lien vers un fichier d’aide associé. <xref:System.Exception.InnerException%2A>Retourne le `Exception` objet qui a provoqué l’exception actuelle, ou si elle retourne `Nothing` s’il n’existe aucun original `Exception`.  
  
## <a name="considerations-when-using-a-trycatch-statement"></a>Considérations sur l’utilisation d’un bloc Try... Catch, instruction  
 Utilisez un `Try…Catch` instruction uniquement pour signaler la présence d’événements inhabituels ou imprévus. Raisons possibles sont les suivantes :  
  
-   Interception d’exceptions lors de l’exécution crée une charge supplémentaire et est susceptible d’être plus lente que la pré-vérification pour éviter les exceptions.  
  
-   Si un `Catch` bloc n’est pas géré correctement, l’exception peuvent ne pas être déclarée correctement pour les utilisateurs.  
  
-   La gestion des exceptions rend plus complexe.  
  
 Vous n’avez pas toujours besoin une `Try…Catch` instruction pour vérifier une condition qui est susceptible de se produire. L’exemple suivant vérifie l’existence d’un fichier avant de tenter de l’ouvrir. Cela réduit la nécessité d’intercepter une exception levée par le <xref:System.IO.File.OpenText%2A> (méthode).  
  
 [!code-vb[VbVbalrStatements#94](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_1.vb)]  
  
 Assurez-vous que le code de `Catch` blocs peuvent signaler correctement les exceptions aux utilisateurs, que ce soit par la journalisation thread-safe ou des messages appropriés. Dans le cas contraire, les exceptions pourraient rester inconnues.  
  
## <a name="async-methods"></a>Méthodes async  
 Si vous marquez une méthode avec le [Async](../../../visual-basic/language-reference/modifiers/async.md) modificateur, vous pouvez utiliser la [Await](../../../visual-basic/language-reference/operators/await-operator.md) opérateur dans la méthode. Une instruction avec le `Await` opérateur suspend l’exécution de la méthode jusqu'à ce que la tâche attendue se termine. La tâche représente un travail en cours. Lorsque la tâche est associée la `Await` opérateur se termine, reprend l’exécution dans la même méthode. Pour plus d’informations, consultez [flux de contrôle dans les programmes Async](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
 Une tâche retournée par une méthode Async peut se terminer dans un état d’erreur, indiquant qu’il est terminé en raison d’une exception non gérée. Une tâche peut également se terminer dans un état annulé, ce qui entraîne une `OperationCanceledException` sont levées en dehors de l’expression await. Pour intercepter un type d’exception, placez le `Await` expression qui est associé à la tâche dans un `Try` bloquer et d’intercepter l’exception dans le `Catch` bloc. Un exemple est fourni plus loin dans cette rubrique.  
  
 Une tâche peut être dans un état d’erreur, car plusieurs exceptions ont été responsables de son défaillante. Par exemple, la tâche peut être le résultat d'un appel à <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Lorsque vous attendez une telle tâche, l’exception interceptée est uniquement une des exceptions, et vous ne pouvez pas prédire quelle exception est interceptée. Un exemple est fourni plus loin dans cette rubrique.  
  
 Un `Await` expression ne peut pas être à l’intérieur d’un `Catch` bloc ou `Finally` bloc.  
  
## <a name="iterators"></a>Itérateurs  
 Une fonction d’itérateur ou `Get` accesseur effectue une itération personnalisée sur une collection. Un itérateur utilise une [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) instruction pour retourner chaque élément de la collection un à la fois. Vous appelez une fonction d’itérateur en utilisant un [For Each... L’instruction suivante](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
 A `Yield` instruction peut être à l’intérieur d’un `Try` bloc. A `Try` bloc qui contient un `Yield` instruction peut avoir `Catch` bloque et peut avoir un `Finally` bloc. Consultez la section « Essayez de blocs dans Visual Basic » de [itérateurs](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7) pour obtenir un exemple.  
  
 A `Yield` instruction ne peut pas être à l’intérieur d’un `Catch` bloc ou une `Finally` bloc.  
  
 Si le `For Each` corps (en dehors de la fonction d’itérateur) lève une exception, une `Catch` bloc dans la fonction d’itérateur n’est pas exécutée, mais un `Finally` bloc dans la fonction d’itérateur est exécuté. A `Catch` bloc à l’intérieur d’une fonction d’itérateur intercepte uniquement les exceptions qui se produisent à l’intérieur de la fonction d’itérateur.  
  
## <a name="partial-trust-situations"></a>Situations de confiance partielle  
 Dans les situations de confiance partielle, par exemple, une application hébergée sur un partage réseau, `Try...Catch...Finally` n’intercepte pas les exceptions de sécurité qui se produisent avant l’appel de la méthode qui contient l’appel. L’exemple suivant, s’il est placé sur un partage de serveur et l’exécuter à partir de là, génère l’erreur « System.Security.SecurityException : Échec de la demande. » Pour plus d’informations sur les exceptions de sécurité, consultez la <xref:System.Security.SecurityException> classe.  
  
 [!code-vb[VbVbalrStatements#85](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_2.vb)]  
  
 Dans ce cas de confiance partielle, vous devez placer le `Process.Start` instruction dans une fonction `Sub`. L’appel initial à la `Sub` échoue. Cela permet de `Try...Catch` à intercepter avant le `Sub` contenant `Process.Start` est démarré et l’exception de sécurité.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre la structure de la `Try...Catch...Finally` instruction.  
  
 [!code-vb[VbVbalrStatements#86](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_3.vb)]  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, la `CreateException` méthode lève une exception un `NullReferenceException`. Le code qui génère l’exception n’est pas dans un `Try` bloc. Par conséquent, le `CreateException` méthode ne gère pas l’exception. Le `RunSample` méthode gère l’exception, car l’appel à la `CreateException` méthode se trouve dans un `Try` bloc.  
  
 L’exemple inclut `Catch` instructions pour plusieurs types d’exceptions, classés à partir de la plus spécifique à la plus générale.  
  
 [!code-vb[VbVbalrStatements#91](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_4.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser un `Catch When` instruction pour filtrer sur une expression conditionnelle. Si l’expression conditionnelle a la valeur `True`, le code dans le `Catch` bloc s’exécute.  
  
 [!code-vb[VbVbalrStatements#92](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_5.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant comprend une `Try…Catch` instruction contenue dans une `Try` bloc. Interne `Catch` bloc lève une exception qui a son `InnerException` propriété définie à l’exception d’origine. Externe `Catch` bloc signale sa propre exception et l’exception interne.  
  
 [!code-vb[VbVbalrStatements#93](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_6.vb)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre la gestion des exceptions pour les méthodes async. Pour intercepter une exception qui s’applique à une tâche async, la `Await` expression est dans un `Try` bloc de l’appelant et de l’exception est interceptée dans le `Catch` bloc.  
  
 Supprimez les marques de commentaire de la ligne `Throw New Exception` dans l'exemple pour illustrer la gestion des exceptions. L’exception est interceptée dans le `Catch` bloquer, de la tâche `IsFaulted` est définie sur `True`et de la tâche `Exception.InnerException` est définie sur l’exception.  
  
 Supprimez les marques de commentaire de la ligne `Throw New OperationCancelledException` pour montrer ce qui se passe quand vous annulez un processus asynchrone. L’exception est interceptée dans le `Catch` bloc et de la tâche `IsCanceled` est définie sur `True`. Toutefois, sous certaines conditions qui s’appliquent à cet exemple, `IsFaulted` a la valeur `True` et `IsCanceled` a la valeur `False`.  
  
 [!code-vb[csAsyncExceptions#1](../../../csharp/language-reference/keywords/codesnippet/VisualBasic/try-catch-finally-statement_7.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre la gestion des exceptions quand plusieurs tâches peuvent entraîner plusieurs exceptions. Le `Try` bloc contient la `Await` expression pour la tâche qui <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> retourné. La tâche est terminée quand les trois tâches auxquelles <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> est appliqué sont terminées.  
  
 Chacune de ces trois tâches provoque une exception. Le `Catch` bloc effectue une itération dans les exceptions qui sont trouvent dans le `Exception.InnerExceptions` propriété de la tâche qui `Task.WhenAll` retourné.  
  
 [!code-vb[csAsyncExceptions#3](../../../csharp/language-reference/keywords/codesnippet/VisualBasic/try-catch-finally-statement_8.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:System.Exception>  
 [Exit (instruction)](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [On Error (instruction)](../../../visual-basic/language-reference/statements/on-error-statement.md)  
 [Bonnes pratiques pour l’utilisation des extraits de code](/visualstudio/ide/best-practices-for-using-code-snippets)  
 [Gestion des exceptions](../../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md)  
 [Throw (instruction)](../../../visual-basic/language-reference/statements/throw-statement.md)
