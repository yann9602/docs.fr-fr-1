---
title: "lock, instruction (Informations de référence sur C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- lock_CSharpKeyword
- lock
dev_langs:
- CSharp
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
caps.latest.revision: 43
author: BillWagner
ms.author: wiwagn
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 020be199391789360ae9a25858bef54d8259ae56
ms.lasthandoff: 03/13/2017

---
# <a name="lock-statement-c-reference"></a>lock, instruction (Informations de référence sur C#)
Le mot clé `lock` marque un bloc d’instructions comme étant une section critique en obtenant le verrou d’exclusion mutuelle pour un objet donné, en exécutant une instruction, puis en libérant le verrou. L’exemple suivant inclut une instruction `lock`.  
  
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
  
 Pour plus d’informations, consultez [Synchronisation des threads](http://msdn.microsoft.com/library/413e1f28-a2c5-4eec-8338-aa43e7982ff4).  
  
## <a name="remarks"></a>Remarques  
 Le mot clé `lock` garantit qu’un thread n’entre pas dans une section critique de code alors qu’un autre thread est dans cette section critique. Si un autre thread tente d’entrer dans un code verrouillé, il attend, en restant bloqué jusqu’à ce que l’objet soit libéré.  
  
 La section [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c) présente le threading.  
  
 Le mot clé `lock` appelle <xref:System.Threading.Monitor.Enter%2A> au début du bloc et <xref:System.Threading.Monitor.Exit%2A> à la fin du bloc. Une <xref:System.Threading.ThreadInterruptedException> est levée si <xref:System.Threading.Thread.Interrupt%2A> interrompt un thread qui attend d’entrer dans une instruction `lock`.  
  
 D’une façon générale, évitez de verrouiller sur un type `public` ou sur des instances qui sont au-delà du contrôle de votre code. Les constructions courantes `lock (this)`, `lock (typeof (MyType))` et `lock ("myLock")` enfreignent cette directive :  
  
-   `lock (this)` est un problème si l’instance est accessible publiquement.  
  
-   `lock (typeof (MyType))` est un problème si `MyType` est accessible publiquement.  
  
-   `lock("myLock")` est un problème, car tout autre code dans le processus utilisant la même chaîne partagera le même verrou.  
  
 La bonne pratique consiste à définir un objet `private` à verrouiller, ou une variable objet `private static` pour protéger les données communes à toutes les instances.  
  
 Vous ne pouvez pas utiliser le mot clé [await](../../../csharp/language-reference/keywords/await.md) dans le corps d’une instruction `lock`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une utilisation simple des threads sans verrouillage en C#.  
  
 [!code-cs[csrefKeywordsFixedLock#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_1.cs)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise des threads et `lock`. Tant que l’instruction `lock` est présente, le bloc d’instructions est une section critique et `balance` ne devient jamais un nombre négatif.  
  
 [!code-cs[csrefKeywordsFixedLock#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_2.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Reflection.MethodImplAttributes>   
 <xref:System.Threading.Mutex>   
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [Mots clés d’instructions](../../../csharp/language-reference/keywords/statement-keywords.md)   
 @System.Threading.Monitor   
 [Interlocked Operations](http://msdn.microsoft.com/library/cbda7114-c752-4f3e-ada1-b1e8dd262f2b)   
 [AutoResetEvent](http://msdn.microsoft.com/library/6d39c48d-6b37-4a9b-8631-f2924cfd9c18)   
 [Synchronisation des threads](http://msdn.microsoft.com/library/413e1f28-a2c5-4eec-8338-aa43e7982ff4)
