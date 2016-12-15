---
title: "try-catch (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "try"
  - "try_CSharpKeyword"
  - "catch"
  - "catch_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "catch (mot clé C#)"
  - "try-catch (instruction C#)"
ms.assetid: cb5503c7-bfa1-4610-8fc2-ddcd2e84c438
caps.latest.revision: 45
caps.handback.revision: 43
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# try-catch (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'instruction try\-catch consiste en un bloc `try` suivi d'une ou plusieurs clauses `catch` qui spécifient des gestionnaires pour différentes exceptions.  
  
## Notes  
 Quand une exception est levée, le Common Language Runtime \(CLR\) recherche l'instruction `catch` qui gère cette exception.  Si la méthode en cours d'exécution ne contient pas un tel bloc `catch`, le CLR examine la méthode qui a appelé la méthode actuelle, puis remonte la pile des appels.  Si aucun bloc `catch` n'est trouvé, alors le CLR affiche un message d'exception non gérée à l'utilisateur et arrête l'exécution du programme.  
  
 Le bloc `try` contient le code protégé susceptible de provoquer l'exception.  Le bloc est exécuté jusqu'à ce qu'une exception soit levée ou qu'il se soit correctement terminé.  Par exemple, la tentative suivante d'effectuer un cast d'un objet `null` déclenche l'exception <xref:System.NullReferenceException> :  
  
```c#  
object o2 = null;  
try  
{  
    int i2 = (int)o2;   // Error  
}  
```  
  
 Bien que la clause `catch` puisse être utilisée sans arguments pour intercepter tout type d'exception, cette utilisation est déconseillée.  En général, vous devez intercepter uniquement les exceptions desquelles vous savez comment récupérer.  Par conséquent, vous devez toujours spécifier un argument d'objet dérivé de <xref:System.Exception?displayProperty=fullName>, par exemple :  
  
```c#  
catch (InvalidCastException e)   
{  
}  
```  
  
 Il est possible d'utiliser plusieurs clauses `catch` spécifiques dans la même instruction try\-catch.  Dans ce cas, l'ordre des clauses `catch` est important car les clauses `catch` sont examinées dans l'ordre.  Interceptez les exceptions plus spécifiques avant les moins spécifiques.  Le compilateur produit une erreur si vous organisez vos blocs catch de sorte qu'un bloc ultérieur ne puisse jamais être atteint.  
  
 L'utilisation d'arguments `catch` constitue un moyen de filtrer les exceptions à gérer.  Vous pouvez également utiliser une expression de prédicat qui examine l'exception de plus près pour déterminer si elle doit être gérée.  Si l'expression de prédicat retourne la valeur false, alors la recherche d'un gestionnaire se poursuit.  
  
```c#  
Catch (ArgumentException e) if (e.ParamName == “…”)  
{  
}  
```  
  
 L'utilisation de filtres d'exceptions est préférable à une interception et une nouvelle levée \(voir explication ci\-dessous\), car les filtres laissent la pile intact.  Si un gestionnaire ultérieur vide la pile, vous pouvez déterminer d'où l'exception provient à l'origine, au lieu de déterminer simplement le dernier emplacement auquel elle a été levée.  Une utilisation courante des expressions de filtre d'exception est liée à la journalisation.  Vous pouvez créer une fonction de prédicat qui renvoie toujours false et dont la sortie est journalisée ; vous pouvez journaliser des exceptions au fur et à mesure sans avoir à les gérer ni à les lever de nouveau.  
  
 Une instruction [throw](../../../csharp/language-reference/keywords/throw.md) peut être utilisée dans un bloc `catch` pour lever une nouvelle fois l'exception interceptée par l'instruction `catch`.  L'exemple suivant extrait des informations sources d'une exception <xref:System.IO.IOException>, puis lève l'exception à la méthode parente.  
  
```c#  
catch (FileNotFoundException e)  
{  
    // FileNotFoundExceptions are handled here.  
}  
catch (IOException e)  
{  
    // Extract some information from this exception, and then   
    // throw it to the parent method.  
    if (e.Source != null)  
        Console.WriteLine("IOException source: {0}", e.Source);  
    throw;  
}  
```  
  
 Vous pouvez intercepter une seule exception et lever une exception différente.  Dans ce cas, spécifiez l'exception que vous interceptez en tant qu'exception interne, comme illustré dans l'exemple suivant.  
  
```c#  
catch (InvalidCastException e)   
{  
    // Perform some action here, and then throw a new exception.  
    throw new YourCustomException("Put your error message here.", e);  
}  
```  
  
 Vous pouvez également lever à nouveau une exception quand une condition spécifiée a la valeur true, comme illustré dans l'exemple suivant.  
  
```c#  
  
catch (InvalidCastException e)  
{  
    if (e.Data == null)  
    {  
        throw;  
    }  
    else  
    {  
        // Take some action.  
    }  
 }  
```  
  
 Dans un bloc `try`, initialisez uniquement les variables qui y sont déclarées.  Sinon, une exception peut se produire avant la fin de l'exécution du bloc.  Par exemple, dans l'exemple de code suivant, la variable `n` est initialisée à l'intérieur du bloc `try`.  Une tentative d'utilisation de cette variable en dehors du bloc `try` dans l'instruction `Write(n)` génère une erreur du compilateur.  
  
```c#  
static void Main()   
{  
    int n;  
    try   
    {  
        // Do not initialize this variable here.  
        n = 123;  
    }  
    catch  
    {  
    }  
    // Error: Use of unassigned local variable 'n'.  
    Console.Write(n);  
}  
```  
  
 Pour plus d'informations sur l'interception, consultez [try\-catch\-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).  
  
## Exceptions dans les méthodes async  
 Une méthode async est marquée par un modificateur [async](../../../csharp/language-reference/keywords/async.md) et contient généralement une ou plusieurs expressions ou instructions await.  Une expression await applique l'opérateur [await](../../../csharp/language-reference/keywords/await.md) à un <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>.  
  
 Quand le contrôle atteint un `await` dans la méthode async, la progression de la méthode est interrompue jusqu'à ce que la tâche attendue se termine.  Quand la tâche est terminée, l'exécution peut reprendre dans la méthode.  Pour plus d'informations, consultez [Programmation asynchrone avec Async et Await](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md) et [Flux de contrôle dans les programmes Async](../Topic/Control%20Flow%20in%20Async%20Programs%20\(C%23%20and%20Visual%20Basic\).md).  
  
 La tâche terminée à laquelle `await` est appliqué peut être dans un état d'erreur en raison d'une exception non gérée dans la méthode qui retourne la tâche.  L'attente de la tâche lève une exception.  Une tâche peut également se terminer dans un état annulé si le processus asynchrone qui la retourne est annulé.  L'attente d'une tâche annulée lève une `OperationCanceledException`.  Pour plus d'informations sur la façon d'annuler un processus asynchrone, consultez [Réglage de votre application Async](../Topic/Fine-Tuning%20Your%20Async%20Application%20\(C%23%20and%20Visual%20Basic\).md).  
  
 Pour intercepter l'exception, attendez la tâche dans un bloc `try`, puis interceptez l'exception dans le bloc `catch` associé.  Pour obtenir un exemple, consultez la section « Exemple ».  
  
 Une tâche peut être dans un état d'erreur car plusieurs exceptions se sont produites dans la méthode async attendue.  Par exemple, la tâche peut être le résultat d'un appel à <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>.  Quand vous attendez une telle tâche, une seule des exceptions est interceptée et vous ne pouvez pas prévoir laquelle.  Pour obtenir un exemple, consultez la section « Exemple ».  
  
## Exemple  
 Dans l'exemple suivant, le bloc `try` contient un appel à la méthode `ProcessString` qui risque de provoquer une exception.  La clause `catch` clause contient le gestionnaire d'exceptions qui affiche simplement un message à l'écran.  Quand l'instruction `throw` est appelée depuis `MyMethod`, le système recherche l'instruction `catch` et affiche le message `Exception caught`.  
  
 [!code-cs[csrefKeywordsExceptions#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_1.cs)]  
  
## Exemple  
 Dans l'exemple suivant, deux blocs catch sont utilisés, et l'exception la plus spécifique, qui apparaît la première, est interceptée.  
  
 Pour intercepter l'exception la moins spécifique, vous pouvez remplacer l'instruction throw dans `ProcessString` par l'instruction suivante : `throw new Exception()`.  
  
 Si vous placez le bloc catch le moins spécifique en premier dans l'exemple, le message d'erreur suivant s'affiche : `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.  
  
 [!code-cs[csrefKeywordsExceptions#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_2.cs)]  
  
## Exemple  
 L'exemple suivant illustre la gestion des exceptions pour les méthodes async.  Pour intercepter une exception levée par une tâche async, placez l'expression `await` dans un bloc `try` et interceptez\-la dans un bloc `catch`.  
  
 Supprimez les marques de commentaire de la ligne `throw new Exception` dans l'exemple pour illustrer la gestion des exceptions.  La propriété `IsFaulted` de la tâche a la valeur `True`, la propriété `Exception.InnerException` de la tâche a la valeur de l'exception et l'exception est interceptée dans le bloc `catch`.  
  
 Supprimez les marques de commentaire de la ligne `throw new OperationCancelledException` pour illustrer ce qui se passe quand vous annulez un processus asynchrone.  La propriété `IsCanceled` de la tâche a la valeur `true` et l'exception est interceptée dans le bloc `catch`.  Sous certaines conditions qui s'appliquent à cet exemple, la propriété `IsFaulted` de la tâche a la valeur `true` et `IsCanceled` a la valeur `false`.  
  
 [!code-cs[csAsyncExceptions#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_3.cs)]  
  
## Exemple  
 L'exemple suivant illustre la gestion des exceptions quand plusieurs tâches peuvent entraîner plusieurs exceptions.  Le bloc `try` attend la tâche retournée par un appel à <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>.  La tâche est terminée quand les trois tâches auxquelles WhenAll est appliqué sont terminées.  
  
 Chacune de ces trois tâches provoque une exception.  Le bloc `catch` itère au sein des exceptions, qui sont trouvent dans la propriété `Exception.InnerExceptions` de la tâche retournée par <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>.  
  
 [!code-cs[csAsyncExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_4.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Instructions try, throw et catch \(C\+\+\)](/visual-cpp/cpp/try-throw-and-catch-statements-cpp)   
 [Instructions de gestion des exceptions](../../../csharp/language-reference/keywords/exception-handling-statements.md)   
 [throw](../../../csharp/language-reference/keywords/throw.md)   
 [try\-finally](../../../csharp/language-reference/keywords/try-finally.md)   
 [Comment : lever explicitement des exceptions](../Topic/How%20to:%20Explicitly%20Throw%20Exceptions.md)