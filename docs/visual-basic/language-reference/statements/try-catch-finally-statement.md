---
title: Try... Catch... Instruction finally (Visual Basic) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Try...Catch...Finally
- vb.when
- vb.Finally
- vb.Catch
- vb.Try
dev_langs:
- VB
helpviewer_keywords:
- Try...Catch...Finally statements
- Try statement
- try-catch exception handling, Try...Catch...Finally statements
- error handling, while running code
- Try statement, Try...Catch...Finally
- Finally keyword [Visual Basic], Try...Catch...Finally
- Catch statement
- When keyword
- Visual Basic code, handling errors while running
- structured exception handling, Try...Catch...Finally statements
ms.assetid: d6488026-ccb3-42b8-a810-0d97b9d6472b
caps.latest.revision: 69
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
ms.openlocfilehash: 379359e3a338746ccd440dbe1ad58c483e562dbe
ms.lasthandoff: 03/13/2017

---
# <a name="trycatchfinally-statement-visual-basic"></a>Try...Catch...Finally, instruction (Visual Basic)
Fournit un moyen de gérer certaines ou toutes les erreurs possibles qui peuvent se produire dans un bloc de code donné, tout code en cours d’exécution.  
  
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
|`When`|Facultatif. A `Catch` instruction avec un `When` clause intercepte les exceptions uniquement lorsque `expression` a la valeur `True`. A `When` clause est appliquée uniquement après avoir vérifié que le type de l’exception, et `expression` peut faire référence à l’identificateur qui représente l’exception.|  
|`expression`|Facultatif. Doit être implicitement convertible en `Boolean`. Toute expression qui décrit un filtre générique. En général, vous permet de filtrer par numéro d’erreur. Utilisé avec `When` (mot clé) pour spécifier les circonstances dans lesquelles l’erreur est levée.|  
|`catchStatements`|Facultatif. Instructions permettant de gérer les erreurs qui se produisent dans le type `Try` bloc. Il peut s'agir d'une instruction composée.|  
|`Exit Try`|Facultatif. Mot clé qui décompose le `Try...Catch...Finally` structure. L’exécution reprend par le code qui suit immédiatement la `End Try` instruction. La `Finally` instruction sera exécutée. Interdit dans `Finally` blocs.|  
|`Finally`|Facultatif. A `Finally` bloc est toujours exécuté quand l’exécution quitte une partie de la `Try...Catch` instruction.|  
|`finallyStatements`|Facultatif. Instructions qui sont exécutées une fois que tout autre traitement d’erreur s’est produite.|  
|`End Try`|Met fin à la `Try...Catch...Finally` structure.|  
  
## <a name="remarks"></a>Remarques  
 Si vous pensez qu’une exception particulière se produise pendant une section particulière de code, placez le code dans un `Try` bloquer et utiliser un `Catch` bloc pour conserver le contrôle et gérer l’exception si elle se produit.  
  
 A `Try…Catch` instruction se compose d’un `Try` bloc suivie d’une ou plusieurs `Catch` clauses qui spécifient des gestionnaires pour différentes exceptions. Lorsqu’une exception est levée dans un `Try` bloc, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] recherche la `Catch` instruction qui gère l’exception. Si une correspondance `Catch` instruction n’est pas trouvée, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] examine la méthode qui a appelé la méthode actuelle, et ainsi de suite dans la pile des appels. Si aucune `Catch` bloc est trouvé, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] affiche un message d’exception non prise en charge pour l’utilisateur et arrête l’exécution du programme.  
  
 Vous pouvez utiliser plusieurs `Catch` instruction dans un `Try…Catch` instruction. Dans ce cas, l’ordre de la `Catch` clauses est important car ils sont examinés dans l’ordre. Interceptez les exceptions plus spécifiques avant les moins spécifiques.  
  
 Les éléments suivants `Catch` conditions de l’instruction sont les moins spécifiques et intercepte toutes les exceptions qui dérivent de la <xref:System.Exception>classe.</xref:System.Exception> Vous devez normalement utiliser une de ces variations comme dernier `Catch` bloquer la `Try...Catch...Finally` structure, après avoir intercepté toutes les exceptions spécifiques que vous attendez. Flux de contrôle ne peut jamais atteindre un `Catch` bloc qui suit une de ces variations.  
  
-   Le `type` est `Exception`, par exemple :`Catch ex As Exception`  
  
-   L’instruction n’a pas `exception` variable, par exemple :`Catch`  
  
 Lorsqu’un `Try…Catch…Finally` imbriquée dans une autre instruction `Try` bloc, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] examine d’abord chaque `Catch` instruction à l’intérieur `Try` bloc. Si aucune correspondance `Catch` instruction est trouvée, la recherche se poursuit à le `Catch` instructions d’externe `Try…Catch…Finally` bloc.  
  
 Les variables locales d’un `Try` bloc ne sont pas disponibles dans un `Catch` bloqué, car ils sont des blocs séparés. Si vous souhaitez utiliser une variable dans plusieurs blocs, déclarez la variable à l’extérieur de la `Try...Catch...Finally` structure.  
  
> [!TIP]
>  La `Try…Catch…Finally` instruction est disponible comme un extrait de code IntelliSense. Dans le Gestionnaire des extraits de Code, développez **modèles de Code - If, For Each, Try Catch, propriété, etc.**, puis **(Exceptions) de gestion des erreurs**. Pour plus d’informations, consultez [Extraits de code](https://docs.microsoft.com/visualstudio/ide/code-snippets).  
  
## <a name="finally-block"></a>Finally (bloc)  
 Si vous avez une ou plusieurs instructions doivent être exécutées avant de quitter le `Try` de la structure, utilisez un `Finally` bloc. Le contrôle passe à la `Finally` bloquer juste avant du `Try…Catch` structure. Cela est vrai même si une exception se produit n’importe où à l’intérieur de la `Try` structure.  
  
 Un `Finally` bloc est utile pour exécuter tout code qui doit s’exécuter même s’il existe une exception. Le contrôle est passé à la `Finally` bloc quelle que soit la façon dont le `Try...Catch` bloc s’arrête.  
  
 Le code dans un `Finally` bloc s’exécute même si votre code rencontre une `Return` instruction dans un `Try` ou `Catch` bloc. Contrôle ne passe pas d’un `Try` ou `Catch` bloquer correspondantes `Finally` bloquer dans les cas suivants :  
  
-   Un [End, instruction](../../../visual-basic/language-reference/statements/end-statement.md) est rencontré dans le `Try` ou `Catch` bloc.  
  
-   Un <xref:System.StackOverflowException>est levée le `Try` ou `Catch` bloc.</xref:System.StackOverflowException>  
  
 Il n’est pas valide pour transférer explicitement l’exécution dans un `Finally` bloc. Transférer l’exécution hors d’un `Finally` bloc n’est pas valide, sauf via une exception.  
  
 Si un `Try` instruction ne contient pas au moins un `Catch` bloc, il doit contenir un `Finally` bloc.  
  
> [!TIP]
>  Si vous n’avez pas à intercepter des exceptions spécifiques, le `Using` instruction se comporte comme un `Try…Finally` bloc et garantit l’élimination des ressources, quelle que soit la manière dont vous quittez le bloc. Cela est vrai même avec une exception non gérée. Pour plus d’informations, consultez [instruction à l’aide de](../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="exception-argument"></a>Argument d’exception  
 Le `Catch` bloc `exception` argument est une instance de la <xref:System.Exception>classe ou une classe qui dérive de la `Exception` classe</xref:System.Exception> Le `Exception` instance de classe correspond à l’erreur qui s’est produite dans le `Try` bloc.  
  
 Les propriétés de la `Exception` permettent d’identifier la cause et l’emplacement d’une exception de l’objet. Par exemple, le <xref:System.Exception.StackTrace%2A>propriété répertorie les méthodes appelées qui ont conduit à l’exception, afin de vous aider à trouver où l’erreur s’est produite dans le code.</xref:System.Exception.StackTrace%2A> <xref:System.Exception.Message%2A>Retourne un message décrivant l’exception.</xref:System.Exception.Message%2A> <xref:System.Exception.HelpLink%2A>Renvoie un lien vers un fichier d’aide associé.</xref:System.Exception.HelpLink%2A> <xref:System.Exception.InnerException%2A>Retourne le `Exception` objet qui a provoqué l’exception actuelle, ou si elle retourne `Nothing` s’il n’existe aucun original `Exception`.</xref:System.Exception.InnerException%2A>  
  
## <a name="considerations-when-using-a-trycatch-statement"></a>Considérations sur l’utilisation d’un bloc Try... Catch (instruction)  
 Utilisez un `Try…Catch` instruction uniquement pour signaler la présence d’événements inhabituels ou imprévus. Les raisons sont les suivantes :  
  
-   Intercepter des exceptions lors de l’exécution crée une charge supplémentaire et est susceptible d’être plus lente que la pré-vérification pour éviter les exceptions.  
  
-   Si un `Catch` bloc n’est pas traitée correctement, l’exception peut ne pas être rapportée correctement pour les utilisateurs.  
  
-   La gestion des exceptions rend plus complexe.  
  
 Vous n’avez pas toujours besoin un `Try…Catch` instruction pour vérifier une condition qui est susceptible de se produire. L’exemple suivant vérifie l’existence d’un fichier avant d’essayer de l’ouvrir. Cela réduit la nécessité d’intercepter une exception levée par le <xref:System.IO.File.OpenText%2A>méthode.</xref:System.IO.File.OpenText%2A>  
  
 [!code-vb[VbVbalrStatements&#94;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_1.vb)]  
  
 Assurez-vous que le code de `Catch` blocs peuvent correctement signaler les exceptions aux utilisateurs, que ce soit par la journalisation thread-safe ou des messages appropriés. Dans le cas contraire, les exceptions pourraient rester inconnues.  
  
## <a name="async-methods"></a>Méthodes async  
 Si vous marquez une méthode avec la [Async](../../../visual-basic/language-reference/modifiers/async.md) modificateur, vous pouvez utiliser la [Await](../../../visual-basic/language-reference/operators/await-operator.md) opérateur dans la méthode. Une instruction avec le `Await` opérateur suspend l’exécution de la méthode jusqu'à ce que la tâche attendue se termine. La tâche représente un travail en cours. Lorsque la tâche est associée la `Await` opérateur se termine, reprend l’exécution dans la même méthode. Pour plus d’informations, consultez [flux de contrôle dans les programmes Async](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
 Une tâche retournée par une méthode Async peut se terminer dans un état d’erreur, indiquant qu’elle est terminée en raison d’une exception non gérée. Une tâche peut également se terminer dans un état d’annulation, ce qui entraîne une `OperationCanceledException` levée hors de l’expression await. Pour intercepter un type d’exception, placez le `Await` expression associée à la tâche dans un `Try` bloquer et intercepter l’exception dans le `Catch` bloc. Un exemple est fourni plus loin dans cette rubrique.  
  
 Une tâche peut être dans un état d’erreur, car plusieurs exceptions étaient responsables de son défaillante. Par exemple, la tâche peut être le résultat d’un appel à <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>.</xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> Lorsque vous attendez une telle tâche, l’exception interceptée est uniquement une des exceptions, et vous ne pouvez pas prédire quelle exception sera levée. Un exemple est fourni plus loin dans cette rubrique.  
  
 Un `Await` expression ne peut pas être à l’intérieur d’un `Catch` bloc ou `Finally` bloc.  
  
## <a name="iterators"></a>Itérateurs  
 Une fonction d’itérateur ou `Get` accesseur effectue une itération personnalisée sur une collection. Un itérateur utilise un [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) instruction pour retourner chaque élément de la collection une à la fois. Vous appelez une fonction d’itérateur en utilisant un [For Each... L’instruction suivante](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
 A `Yield` instruction peut être à l’intérieur d’un `Try` bloc. A `Try` bloc qui contient un `Yield` instruction peut avoir `Catch` bloque et peut avoir un `Finally` bloc. Consultez la section « Essayez de blocs dans Visual Basic » de [itérateurs](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7) pour obtenir un exemple.  
  
 A `Yield` instruction ne peut pas être à l’intérieur d’un `Catch` bloc ou une `Finally` bloc.  
  
 Si le `For Each` corps (en dehors de la fonction d’itérateur) lève une exception, une `Catch` bloc dans la fonction d’itérateur n’est pas exécuté, mais un `Finally` bloc dans la fonction d’itérateur est exécuté. Un `Catch` bloc à l’intérieur d’une fonction d’itérateur intercepte uniquement les exceptions qui se produisent à l’intérieur de la fonction d’itérateur.  
  
## <a name="partial-trust-situations"></a>Situations de confiance partielle  
 Dans les situations de confiance partielle, tel qu’une application hébergée sur un partage réseau, `Try...Catch...Finally` n’intercepte pas les exceptions de sécurité qui se produisent avant l’appel de la méthode qui contient l’appel. L’exemple suivant, s’il est placé sur un partage de serveur et l’exécuter à partir de là, génère l’erreur « System.Security.SecurityException : Échec de la demande. » Pour plus d’informations sur les exceptions de sécurité, consultez la <xref:System.Security.SecurityException>classe.</xref:System.Security.SecurityException>  
  
 [!code-vb[VbVbalrStatements&#85;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_2.vb)]  
  
 Dans une telle situation de confiance partielle, vous devez placer le `Process.Start` instruction distinct `Sub`. L’appel initial à la `Sub` échoue. Cela permet de `Try...Catch` de l’intercepter avant le `Sub` contenant `Process.Start` est démarré et généré l’exception de sécurité.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre la structure de la `Try...Catch...Finally` instruction.  
  
 [!code-vb[VbVbalrStatements&#86;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_3.vb)]  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, la `CreateException` méthode lève un `NullReferenceException`. Le code qui génère l’exception n’est pas dans un `Try` bloc. Par conséquent, la `CreateException` méthode ne gère pas l’exception. Le `RunSample` méthode gère l’exception car l’appel à la `CreateException` méthode se trouve dans un `Try` bloc.  
  
 L’exemple inclut `Catch` instructions pour plusieurs types d’exceptions, ordonnés de la plus spécifique au plus général.  
  
 [!code-vb[VbVbalrStatements&#91;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_4.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser un `Catch When` instruction pour filtrer sur une expression conditionnelle. Si l’expression conditionnelle a la valeur `True`, le code dans la `Catch` bloc s’exécute.  
  
 [!code-vb[VbVbalrStatements&#92;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_5.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant comprend un `Try…Catch` instruction contenue dans une `Try` bloc. Interne `Catch` bloc lève une exception qui a son `InnerException` propriété définie à l’exception d’origine. Externe `Catch` bloc signale sa propre exception et l’exception interne.  
  
 [!code-vb[VbVbalrStatements&#93;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_6.vb)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre la gestion des exceptions pour les méthodes async. Pour intercepter une exception qui s’applique à une tâche asynchrone, le `Await` expression est dans un `Try` bloc de l’appelant et de l’exception est interceptée dans le `Catch` bloc.  
  
 Supprimez les marques de commentaire de la ligne `Throw New Exception` dans l'exemple pour illustrer la gestion des exceptions. L’exception est interceptée dans le `Catch` bloquer, de la tâche `IsFaulted` est définie sur `True`et de la tâche `Exception.InnerException` est définie sur l’exception.  
  
 Supprimez les commentaires de le `Throw New OperationCancelledException` ligne afin d’illustrer ce qui se passe lorsque vous annulez un processus asynchrone. L’exception est interceptée dans le `Catch` bloc et de la tâche `IsCanceled` est définie sur `True`. Toutefois, dans certaines conditions qui s’appliquent à cet exemple, `IsFaulted` a `True` et `IsCanceled` est défini sur `False`.  
  
 [!code-vb[csAsyncExceptions n °&1;](../../../csharp/language-reference/keywords/codesnippet/VisualBasic/try-catch-finally-statement_7.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre la gestion des exceptions quand plusieurs tâches peuvent entraîner plusieurs exceptions. Le `Try` bloc a le `Await` expression de la tâche qui <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>retourné.</xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> La tâche est terminée lorsque les trois tâches auquel <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>est appliqué sont terminées.</xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>  
  
 Chacune de ces trois tâches provoque une exception. Le `Catch` bloc effectue une itération dans les exceptions qui sont trouvent dans le `Exception.InnerExceptions` propriétés de la tâche qui `Task.WhenAll` retournée.  
  
 [!code-vb[csAsyncExceptions n °&3;](../../../csharp/language-reference/keywords/codesnippet/VisualBasic/try-catch-finally-statement_8.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.Information.Err%2A></xref:Microsoft.VisualBasic.Information.Err%2A>   
 <xref:System.Exception></xref:System.Exception>   
 [Exit (instruction)](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [On Error, instruction](../../../visual-basic/language-reference/statements/on-error-statement.md)   
 [Méthodes conseillées pour utiliser des extraits de Code](https://docs.microsoft.com/visualstudio/ide/best-practices-for-using-code-snippets)   
 [Gestion des exceptions](https://msdn.microsoft.com/library/dd997415)   
 [Throw (instruction)](../../../visual-basic/language-reference/statements/throw-statement.md)
