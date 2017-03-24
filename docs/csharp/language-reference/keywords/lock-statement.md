---
title: "lock, instruction (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "lock_CSharpKeyword"
  - "lock"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "lock (mot clé C#)"
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
caps.latest.revision: 43
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 43
---
# lock, instruction (r&#233;f&#233;rence C#)
Le mot clé `lock` marque un bloc d'instructions comme section critique en assurant le verrouillage par exclusion mutuelle d'un objet particulier, en exécutant une instruction, puis en annulant le verrouillage.  L'exemple suivant inclut une instruction d' `lock` .  
  
```  
  
class Account  
{  
    decimal balance;  
    private Object thisLock = new Object();  
  
    public void Withdraw(decimal amount)  
    {  
        lock (thisLock)  
        {  
            if (amount > balance)  
            {  
                throw new Exception("Insufficient funds");  
            }  
            balance -= amount;  
        }  
    }  
}  
  
```  
  
 Pour plus d'informations, consultez [Synchronisation des threads](../Topic/Thread%20Synchronization%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Notes  
 Le mot clé `lock` permet de garantir qu'un thread n'entre pas dans une section critique de code pendant qu'un autre thread est dans la section critique .  Si un autre thread tente d'entrer dans un code verrouillé, il attendra, bloquera, jusqu'à ce que l'objet soit libéré.  
  
 La section [Thread](../Topic/Threading%20\(C%23%20and%20Visual%20Basic\).md) traite du threading.  
  
 Le mot clé `lock` appelle <xref:System.Threading.Monitor.Enter%2A> au début du bloc et <xref:System.Threading.Monitor.Exit%2A> à la fin du bloc.  <xref:System.Threading.ThreadInterruptedException> est levée si <xref:System.Threading.Thread.Interrupt%2A> interrompt un thread qui attend pour écrire une instruction d' `lock` .  
  
 En général, évitez de verrouiller un type `public`, ou des instances échappant au contrôle de votre code.  Les constructions courantes `lock (this)`, `lock (typeof (MyType))` et `lock ("myLock")` violent cette directive :  
  
-   `lock (this)` pose problème s'il est possible d'accéder publiquement à l'instance.  
  
-   `lock (typeof (MyType))` pose problème s'il est possible d'accéder publiquement à `MyType`.  
  
-   `lock("myLock")` pose problème puisque tout autre code du processus utilisant la même chaîne partagera le même verrouillage.  
  
 La méthode conseillée consiste à définir un objet `private` à verrouiller, ou une variable objet `private static` pour protéger des données communes à toutes les instances.  
  
 Vous ne pouvez pas utiliser le mot clé d' [attendez](../../../csharp/language-reference/keywords/await.md) dans le corps d'une instruction d' `lock` .  
  
## Exemple  
 L'exemple suivant montre une utilisation simple des threads sans verrouillage en C\#.  
  
 [!code-cs[csrefKeywordsFixedLock#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_1.cs)]  
  
## Exemple  
 L'exemple suivant utilise des threads et `lock`.  Tant que l'instruction `lock` est présente, le bloc d'instructions est une section critique et `balance` ne deviendra jamais un nombre négatif.  
  
 [!code-cs[csrefKeywordsFixedLock#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_2.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 <xref:System.Reflection.MethodImplAttributes>   
 <xref:System.Threading.Mutex>   
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Thread](../Topic/Threading%20\(C%23%20and%20Visual%20Basic\).md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Mots clés d'instructions](../../../csharp/language-reference/keywords/statement-keywords.md)   
 [Moniteurs](../Topic/Monitors.md)   
 [Interlocked Operations](../Topic/Interlocked%20Operations.md)   
 [AutoResetEvent](../Topic/AutoResetEvent.md)   
 [Synchronisation des threads](../Topic/Thread%20Synchronization%20\(C%23%20and%20Visual%20Basic\).md)