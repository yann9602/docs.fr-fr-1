---
title: "Try...Catch...Finally Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Try...Catch...Finally"
  - "vb.when"
  - "vb.Finally"
  - "vb.Catch"
  - "vb.Try"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Try...Catch...Finally statements"
  - "Try statement"
  - "try-catch exception handling, Try...Catch...Finally statements"
  - "error handling, while running code"
  - "Try statement, Try...Catch...Finally"
  - "Finally keyword [Visual Basic], Try...Catch...Finally"
  - "Catch statement"
  - "When keyword"
  - "Visual Basic code, handling errors while running"
  - "structured exception handling, Try...Catch...Finally statements"
ms.assetid: d6488026-ccb3-42b8-a810-0d97b9d6472b
caps.latest.revision: 69
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 69
---
# Try...Catch...Finally Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Permet de traiter une partie ou l'ensemble des erreurs possibles pouvant se produire dans un bloc de code donné, tout en continuant à exécuter le code.  
  
## Syntaxe  
  
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
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`tryStatements`|Optionnel.  Instructions dans lesquelles une erreur peut se produire.  Il peut s'agir d'une instruction composée.|  
|`Catch`|Optionnel.  Plusieurs blocs `Catch` sont autorisés.  Si une exception se produit pendant le traitement du bloc `Try`, chaque instruction `Catch` est examinée dans l'ordre textuel afin de déterminer si elle gère cette exception, `exception` représentant l'exception qui a été levée.|  
|`exception`|Optionnel.  Tout nom de variable.  La valeur initiale de l'argument `exception` est la valeur de l'erreur levée.  Cet argument est utilisé avec `Catch` pour spécifier l'erreur interceptée.  S'il est omis, l'instruction `Catch` intercepte n'importe quelle exception.|  
|`type`|Optionnel.  Spécifie le type d'un filtre de classe.  Si la valeur de l'argument `exception` est l'un des types spécifiés par `type` ou un type dérivé, l'identificateur est lié à l'objet exception.|  
|`When`|Optionnel.  Une instruction `Catch` avec une clause `When` intercepte les exceptions uniquement lorsque `expression` a la valeur `True`.  Une clause `When` n'est appliquée qu'après le contrôle du type de l'exception, et `expression` peut faire référence à l'identificateur qui représente l'exception.|  
|`expression`|Optionnel.  Doit pouvoir être converti implicitement en type `Boolean`.  Toute expression qui décrit un filtre générique.  Généralement utilisé pour effectuer un filtre selon le numéro de l'erreur.  Cet argument est utilisé avec le mot clé `When` pour spécifier des circonstances permettant d'intercepter l'erreur.|  
|`catchStatements`|Optionnel.  Instruction\(s\) permettant de gérer des erreurs se produisant dans le bloc `Try` associé.  Il peut s'agir d'une instruction composée.|  
|`Exit Try`|Optionnel.  Mot clé qui décompose la structure `Try...Catch...Finally`.  L'exécution reprend par le code qui suit immédiatement l'instruction `End Try`.  L'instruction `Finally` sera toujours exécutée.  Non autorisé dans les blocs `Finally`.|  
|`Finally`|Optionnel.  Un bloc `Finally` est toujours exécuté quand l'exécution quitte une partie quelconque de l'instruction `Try...Catch`.|  
|`finallyStatements`|Optionnel.  Instructions qui sont exécutées à la fin du traitement de toutes les autres erreurs.|  
|`End Try`|Met fin à la structure `Try...Catch...Finally`.|  
  
## Notes  
 Si vous vous attendez à ce qu'une exception particulière se produise pendant une section particulière de code, mettez le code dans un bloc `Try` et utilisez un bloc `Catch` pour conserver le contrôle et gérer l'exception si elle se produit.  
  
 Une instruction `Try…Catch` est un bloc `Try` suivi par une ou plusieurs clauses `Catch`, qui spécifient les gestionnaires de diverses exceptions.  Lorsqu'une exception est levée dans un bloc `Try`, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] recherche l'instruction `Catch` qui gère l'exception.  Si une instruction `Catch` correspondante n'est pas trouvée, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] examine la méthode qui a appelé la méthode actuelle, et ainsi de suite dans la pile des appels.  Si aucun bloc `Catch` n'est trouvé, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] affiche un message d'exception non gérée destiné à l'utilisateur et arrête l'exécution du programme.  
  
 Vous pouvez utiliser plusieurs instructions `Catch` dans une instruction `Try…Catch`.  Si vous faites cela, l'ordre des clauses `Catch` est important car celles\-ci sont examinées dans l'ordre.  Interceptez les exceptions les plus spécifiques avant celles qui le sont le moins.  
  
 Les conditions de l'instruction `Catch` suivantes sont les moins spécifiques et intercepteront toutes les exceptions dérivant de la classe <xref:System.Exception>.  Vous devez normalement utiliser l'une de ces variations comme dernier bloc `Catch` dans la structure `Try...Catch...Finally`, après avoir intercepté toutes les exceptions spécifiques que vous prévoyez.  Le flux de contrôle ne peut jamais atteindre un bloc `Catch` qui suit l'une de ces variations.  
  
-   `type` a la valeur `Exception`, par exemple : `Catch ex As Exception`  
  
-   L'instruction n'a aucune variable `exception`, par exemple : `Catch`  
  
 Lorsqu'une instruction `Try…Catch…Finally` est imbriquée dans un autre bloc `Try`, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] examine d'abord chaque instruction `Catch` dans le bloc `Try` le plus profond.  Si aucune instruction `Catch` correspondante n'est trouvée, la recherche se poursuit aux instructions `Catch` du bloc externe `Try…Catch…Finally`.  
  
 Les variables locales d'un bloc `Try` ne sont pas disponibles dans un bloc `Catch`, car ce sont des blocs séparés.  Si vous voulez utiliser une variable dans plusieurs blocs, déclarez la variable à l'extérieur de la structure `Try...Catch...Finally`.  
  
> [!TIP]
>  L'instruction `Try…Catch…Finally` est disponible sous forme d'extrait de code IntelliSense.  Dans le Gestionnaire des extraits de code, développez **Modèles de code \- If, For Each, Try Catch, Property, etc.**, puis **Gestion des erreurs \(Exceptions\)**.  Pour plus d'informations, consultez [Extraits de code](/visual-studio/ide/code-snippets).  
  
## Bloc Finally  
 Si une ou plusieurs instructions doivent être exécutées avant que vous ne sortiez de la structure `Try`, utilisez un bloc `Finally`.  Le contrôle passe au bloc `Finally` juste avant de sortir de la structure `Try…Catch`.  Cela est vrai même si une exception se produit où que ce soit dans la structure `Try`.  
  
 Un bloc `Finally` est utile pour l'exécution de tout code qui doit s'exécuter même en cas d'exception.  Le contrôle est transmis au bloc `Finally` quelle que soit la méthode de sortie du bloc `Try...Catch`.  
  
 Le code dans un bloc `Finally` s'exécute même si votre code rencontre une instruction `Return` ou `Try` dans un bloc `Catch` ou .  Le contrôle ne passe pas d'un bloc `Try` ou `Catch` au bloc `Finally` correspondant dans les cas suivants :  
  
-   Une [End Statement](../../../visual-basic/language-reference/statements/end-statement.md) est rencontrée dans le bloc `Try` ou `Catch`.  
  
-   Une <xref:System.StackOverflowException> est levée dans le bloc `Try` ou `Catch`.  
  
 Il n'est pas valide pour transférer explicitement l'exécution dans un bloc d' `Finally` .  Transférer l'exécution en dehors d'un bloc d' `Finally` est pas valide, sauf dans une exception.  
  
 Si une instruction `Try` ne contient pas au moins un bloc `Catch`, elle doit contenir un bloc `Finally`.  
  
> [!TIP]
>  Si vous n'avez pas besoin d'intercepter des exceptions spécifiques, l'instruction `Using` se comporte comme un bloc `Try…Finally` et garantit l'élimination des ressources, quelle que soit la manière dont vous quittez le bloc.  Cela est vrai même avec une exception non gérée.  Pour plus d'informations, consultez [Using Statement](../../../visual-basic/language-reference/statements/using-statement.md).  
  
## Argument d'exception  
 L'argument `exception` du bloc `Catch` est une instance de la classe <xref:System.Exception> ou une classe qui dérive de la classe `Exception`.  L'instance de la classe `Exception` correspond à l'erreur qui s'est produite dans le bloc `Try`.  
  
 Les propriétés de l'objet `Exception` permettent d'identifier la cause et l'emplacement d'une exception.  Par exemple, la propriété <xref:System.Exception.StackTrace%2A> répertorie les méthodes appelées qui ont abouti à l'exception, ce qui vous permet de rechercher l'emplacement de l'erreur dans le code.  <xref:System.Exception.Message%2A> renvoie un message qui décrit l'exception.  <xref:System.Exception.HelpLink%2A> renvoie un lien vers un fichier d'aide associé.  <xref:System.Exception.InnerException%2A> renvoie l'objet `Exception` qui a provoqué l'exception en cours, ou renvoie `Nothing` s'il n'existe aucune `Exception` originale.  
  
## Considérations sur l'utilisation d'une instruction Try…Catch  
 Utilisez une instruction `Try…Catch` uniquement pour signaler que des événements inhabituels ou imprévus se sont produits.  Cette opération se produit pour les raisons suivantes :  
  
-   L'interception d'exceptions lors de l'exécution crée une charge mémoire supplémentaire et est susceptible d'être plus lente que la pré\-vérification pour éviter les exceptions.  
  
-   Si un bloc `Catch` n'est pas correctement traité, l'exception ne sera peut\-être pas rapportée de façon correcte aux utilisateurs.  
  
-   La gestion des exceptions rend plus complexe un programme.  
  
 Une instruction `Try…Catch` n'est pas toujours nécessaire pour rechercher une condition qui risque probablement de se produire.  L'exemple suivant vérifie si un fichier existe avant de tenter de l'ouvrir.  Cela réduit la nécessité d'intercepter une exception levée par la méthode <xref:System.IO.File.OpenText%2A>.  
  
 [!code-vb[VbVbalrStatements#94](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/try-catch-finally-statem_1.vb)]  
  
 Veiller à ce que le code dans les blocs `Catch` puisse signaler correctement les exceptions aux utilisateurs, que ce soit par la journalisation thread\-safe ou des messages appropriés.  Sinon, les exceptions pourraient rester inconnues.  
  
## Méthodes Async  
 Si vous marquez une méthode avec le modificateur d' [Async](../../../visual-basic/language-reference/modifiers/async.md) , vous pouvez utiliser l'opérateur d' [attendez](../../../visual-basic/language-reference/operators/await-operator.md) dans la méthode.  Une instruction avec l'opérateur d' `Await` interrompt l'exécution de la méthode jusqu'à ce que la tâche se termine attendue.  La tâche représente le travail actif.  Lorsque la tâche associée à l'opérateur d' `Await` terminée, l'exécution se poursuit dans la même méthode.  Pour plus d'informations, consultez [Flux de contrôle dans les programmes Async](../Topic/Control%20Flow%20in%20Async%20Programs%20\(C%23%20and%20Visual%20Basic\).md).  
  
 Une tâche retournée par une méthode Async peut se terminer dans un état censuré, indiquant qu'elle est terminée en raison d'une exception non gérée.  Une tâche peut également se terminer dans un état canceled, ce qui entraîne `OperationCanceledException` est levée en dehors de l'expression d'attente.  Pour intercepter l'un ou l'autre type d'exception, définissez l'expression d' `Await` associée à la tâche dans un bloc d' `Try` , et intercepter l'exception dans le bloc d' `Catch` .  Un exemple est plus loin dans cette rubrique.  
  
 Une tâche peut être dans un état censuré car plusieurs exceptions ont été chargées de sa dislocation.  Par exemple, la tâche peut être le résultat d'un appel à <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>.  Lorsque vous attendez une telle tâche, l'exception est interceptée une seule des exceptions, et vous ne pouvez pas prévoir une exception est interceptée.  Un exemple est plus loin dans cette rubrique.  
  
 Une expression d' `Await` ne peut pas être dans un bloc d' `Catch` ou de bloc d' `Finally` .  
  
## Itérateurs  
 Une fonction d'itérateur ou un utilisateur d' `Get` effectue une itération au sein d'une collection.  Un itérateur utilise une instruction de [rendement](../../../visual-basic/language-reference/statements/yield-statement.md) pour retourner chaque élément de la collection un par un.  Vous appelez une fonction d'itérateur à l'aide de [For Each...Next, instruction](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
 Une instruction d' `Yield` peut se trouver dans un bloc d' `Try` .  Un bloc d' `Try` qui contient une instruction d' `Yield` peut avoir des blocs d' `Catch` , et peut avoir un bloc d' `Finally` .  Consultez des « bloc try la section dans Visual Basic » d' [Itérateurs](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md) pour un exemple.  
  
 Une instruction d' `Yield` ne peut pas être dans un bloc d' `Catch` ou d'un bloc d' `Finally` .  
  
 Si le corps d' `For Each` \(en dehors de la fonction d'itérateur\) lève une exception, un bloc d' `Catch` dans la fonction d'itérateur n'est pas exécuté, mais un bloc d' `Finally` dans la fonction d'itérateur est exécuté.  Un bloc d' `Catch` à l'intérieur d'une fonction d'itérateur intercepte uniquement les exceptions qui se produisent à l'intérieur de la fonction d'itérateur.  
  
## Situations d'un niveau de confiance partiel  
 Dans les situations d'un niveau de confiance partiel, comme une application hébergée sur un partage réseau, `Try...Catch...Finally` n'intercepte pas les exceptions de sécurité qui se produisent avant que la méthode qui contient l'appel ne soit appelée.  L'exemple suivant, s'il est placé sur un partage réseau et exécuté à cet endroit, produit l'erreur : "System.Security.SecurityException: Échec de la demande". Pour plus d'informations sur les exceptions de sécurité, consultez la classe <xref:System.Security.SecurityException>.  
  
 [!code-vb[VbVbalrStatements#85](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/try-catch-finally-statem_2.vb)]  
  
 Dans la situation d'un niveau de confiance partiel, vous devez placer l'instruction `Process.Start` dans un `Sub` séparé.  L'appel initial au `Sub` échoue.  Cela permet à `Try...Catch` de l'intercepter avant le démarrage du `Sub` qui contient `Process.Start` et l'exécution de l'exception de sécurité.  
  
## Exemple  
 L'exemple ci\-dessous illustre la structure de l'instruction `Try...Catch...Finally`.  
  
 [!code-vb[VbVbalrStatements#86](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/try-catch-finally-statem_3.vb)]  
  
## Exemple  
 Dans l'exemple suivant, la méthode `CreateException` lève une `NullReferenceException`.  Le code qui génère l'exception n'est pas dans un bloc `Try`.  Par conséquent, la méthode `CreateException` ne gère pas l'exception.  La méthode `RunSample` gère l'exception car l'appel à la méthode `CreateException` est dans un bloc `Try`.  
  
 L'exemple inclut des instructions `Catch` pour plusieurs types d'exceptions, classées de la plus spécifique à la plus générale.  
  
 [!code-vb[VbVbalrStatements#91](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/try-catch-finally-statem_4.vb)]  
  
## Exemple  
 L'exemple suivant montre comment utiliser une instruction `Catch When` pour filtrer sur une expression conditionnelle.  Si l'expression conditionnelle a la valeur `True`, le code dans le bloc `Catch` s'exécute.  
  
 [!code-vb[VbVbalrStatements#92](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/try-catch-finally-statem_5.vb)]  
  
## Exemple  
 L'exemple suivant a une instruction `Try…Catch` contenue dans un bloc `Try`.  Le bloc interne `Catch` lève une exception dont la propriété `InnerException` est définie sur l'exception d'origine.  Le bloc `Catch` externe signale sa propre exception et l'exception interne.  
  
 [!code-vb[VbVbalrStatements#93](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/try-catch-finally-statem_6.vb)]  
  
## Exemple  
 L'exemple suivant illustre la gestion des exceptions pour les méthodes async.  Pour intercepter une exception qui s'applique à une tâche async, l'expression d' `Await` est dans un bloc d' `Try` de l'appelant, et l'exception est interceptée dans le bloc d' `Catch` .  
  
 Supprimez les marques de commentaire de la ligne de `Throw New Exception` l'exemple pour illustrer la gestion des exceptions.  L'exception est interceptée dans le bloc d' `Catch` , la propriété d' `IsFaulted` de la tâche a `True`, et la propriété d' `Exception.InnerException` de la tâche a pour valeur l'exception.  
  
 Supprimez les marques de commentaire de la ligne de `Throw New OperationCancelledException` pour illustrer ce qui se produit lorsque vous supprimez un processus asynchrone.  L'exception est interceptée dans le bloc d' `Catch` , et la propriété d' `IsCanceled` de la tâche a `True`.  Toutefois, dans certaines conditions qui ne s'appliquent pas à cet exemple, `IsFaulted` a la valeur `True` et `IsCanceled` a la valeur `False`.  
  
 [!code-vb[csAsyncExceptions#1](../../../csharp/language-reference/keywords/codesnippet/visualbasic/try-catch-finally-statem_7.vb)]  
  
## Exemple  
 L'exemple suivant illustre la gestion des exceptions lorsque plusieurs tâches peuvent entraîner de plusieurs exceptions.  Le bloc d' `Try` a l'expression d' `Await` pour la tâche à <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> est retournée.  La tâche est terminée lorsque les trois tâches auxquelles <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> est appliqué sont terminées.  
  
 Les trois causes de tâches une exception.  Le bloc d' `Catch` itère au sein de les exceptions, qui se trouvent dans la propriété d' `Exception.InnerExceptions` de la tâche à `Task.WhenAll` est retournée.  
  
 [!code-vb[csAsyncExceptions#3](../../../csharp/language-reference/keywords/codesnippet/visualbasic/try-catch-finally-statem_8.vb)]  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Information.Err%2A>   
 <xref:System.Exception>   
 [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [On Error Statement](../../../visual-basic/language-reference/statements/on-error-statement.md)   
 [Meilleures pratiques pour l'utilisation des extraits de code](/visual-studio/ide/best-practices-for-using-code-snippets)   
 [Gestion des exceptions](../Topic/Exception%20Handling%20\(Task%20Parallel%20Library\).md)   
 [Throw Statement](../../../visual-basic/language-reference/statements/throw-statement.md)