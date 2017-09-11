---
title: "lock, instruction (Informations de référence sur C#)"
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 00dcbb9feec11587265bf61667d91c2c1598065b
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="f35f3-102">lock, instruction (Informations de référence sur C#)</span><span class="sxs-lookup"><span data-stu-id="f35f3-102">lock Statement (C# Reference)</span></span>
<span data-ttu-id="f35f3-103">Le mot clé `lock` marque un bloc d’instructions comme étant une section critique en obtenant le verrou d’exclusion mutuelle pour un objet donné, en exécutant une instruction, puis en libérant le verrou.</span><span class="sxs-lookup"><span data-stu-id="f35f3-103">The `lock` keyword marks a statement block as a critical section by obtaining the mutual-exclusion lock for a given object, executing a statement, and then releasing the lock.</span></span> <span data-ttu-id="f35f3-104">L’exemple suivant inclut une instruction `lock`.</span><span class="sxs-lookup"><span data-stu-id="f35f3-104">The following example includes a `lock` statement.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="f35f3-105">Pour plus d’informations, consultez [Synchronisation des threads](http://msdn.microsoft.com/library/413e1f28-a2c5-4eec-8338-aa43e7982ff4).</span><span class="sxs-lookup"><span data-stu-id="f35f3-105">For more information, see [Thread Synchronization](http://msdn.microsoft.com/library/413e1f28-a2c5-4eec-8338-aa43e7982ff4).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f35f3-106">Remarques</span><span class="sxs-lookup"><span data-stu-id="f35f3-106">Remarks</span></span>  
 <span data-ttu-id="f35f3-107">Le mot clé `lock` garantit qu’un thread n’entre pas dans une section critique de code alors qu’un autre thread est dans cette section critique.</span><span class="sxs-lookup"><span data-stu-id="f35f3-107">The `lock` keyword ensures that one thread does not enter a critical section of code while another thread is in the critical section.</span></span> <span data-ttu-id="f35f3-108">Si un autre thread tente d’entrer dans un code verrouillé, il attend, en restant bloqué jusqu’à ce que l’objet soit libéré.</span><span class="sxs-lookup"><span data-stu-id="f35f3-108">If another thread tries to enter a locked code, it will wait, block, until the object is released.</span></span>  
  
 <span data-ttu-id="f35f3-109">La section [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c) présente le threading.</span><span class="sxs-lookup"><span data-stu-id="f35f3-109">The section [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c) discusses threading.</span></span>  
  
 <span data-ttu-id="f35f3-110">Le mot clé `lock` appelle <xref:System.Threading.Monitor.Enter%2A> au début du bloc et <xref:System.Threading.Monitor.Exit%2A> à la fin du bloc.</span><span class="sxs-lookup"><span data-stu-id="f35f3-110">The `lock` keyword calls <xref:System.Threading.Monitor.Enter%2A> at the start of the block and <xref:System.Threading.Monitor.Exit%2A> at the end of the block.</span></span> <span data-ttu-id="f35f3-111">Une exception <xref:System.Threading.ThreadInterruptedException> est levée si <xref:System.Threading.Thread.Interrupt%2A> interrompt un thread qui attend de passer une instruction `lock`.</span><span class="sxs-lookup"><span data-stu-id="f35f3-111">A <xref:System.Threading.ThreadInterruptedException> is thrown if <xref:System.Threading.Thread.Interrupt%2A> interrupts a thread that is waiting to enter a `lock` statement.</span></span>  
  
 <span data-ttu-id="f35f3-112">D’une façon générale, évitez de verrouiller sur un type `public` ou sur des instances qui sont au-delà du contrôle de votre code.</span><span class="sxs-lookup"><span data-stu-id="f35f3-112">In general, avoid locking on a `public` type, or instances beyond your code's control.</span></span> <span data-ttu-id="f35f3-113">Les constructions courantes `lock (this)`, `lock (typeof (MyType))` et `lock ("myLock")` enfreignent cette directive :</span><span class="sxs-lookup"><span data-stu-id="f35f3-113">The common constructs `lock (this)`, `lock (typeof (MyType))`, and `lock ("myLock")` violate this guideline:</span></span>  
  
-   <span data-ttu-id="f35f3-114">`lock (this)` est un problème si l’instance est accessible publiquement.</span><span class="sxs-lookup"><span data-stu-id="f35f3-114">`lock (this)` is a problem if the instance can be accessed publicly.</span></span>  
  
-   <span data-ttu-id="f35f3-115">`lock (typeof (MyType))` est un problème si `MyType` est accessible publiquement.</span><span class="sxs-lookup"><span data-stu-id="f35f3-115">`lock (typeof (MyType))` is a problem if `MyType` is publicly accessible.</span></span>  
  
-   <span data-ttu-id="f35f3-116">`lock("myLock")` est un problème, car tout autre code dans le processus utilisant la même chaîne partagera le même verrou.</span><span class="sxs-lookup"><span data-stu-id="f35f3-116">`lock("myLock")` is a problem because any other code in the process using the same string, will share the same lock.</span></span>  
  
 <span data-ttu-id="f35f3-117">La bonne pratique consiste à définir un objet `private` à verrouiller, ou une variable objet `private static` pour protéger les données communes à toutes les instances.</span><span class="sxs-lookup"><span data-stu-id="f35f3-117">Best practice is to define a `private` object to lock on, or a `private static` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="f35f3-118">Vous ne pouvez pas utiliser le mot clé [await](../../../csharp/language-reference/keywords/await.md) dans le corps d’une instruction `lock`.</span><span class="sxs-lookup"><span data-stu-id="f35f3-118">You can't use the [await](../../../csharp/language-reference/keywords/await.md) keyword in the body of a `lock` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f35f3-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="f35f3-119">Example</span></span>  
 <span data-ttu-id="f35f3-120">L’exemple suivant montre une utilisation simple des threads sans verrouillage en C#.</span><span class="sxs-lookup"><span data-stu-id="f35f3-120">The following sample shows a simple use of threads without locking in C#.</span></span>  
  
 <span data-ttu-id="f35f3-121">[!code-cs[csrefKeywordsFixedLock#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f35f3-121">[!code-cs[csrefKeywordsFixedLock#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="f35f3-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="f35f3-122">Example</span></span>  
 <span data-ttu-id="f35f3-123">L’exemple suivant utilise des threads et `lock`.</span><span class="sxs-lookup"><span data-stu-id="f35f3-123">The following sample uses threads and `lock`.</span></span> <span data-ttu-id="f35f3-124">Tant que l’instruction `lock` est présente, le bloc d’instructions est une section critique et `balance` ne devient jamais un nombre négatif.</span><span class="sxs-lookup"><span data-stu-id="f35f3-124">As long as the `lock` statement is present, the statement block is a critical section and `balance` will never become a negative number.</span></span>  
  
 <span data-ttu-id="f35f3-125">[!code-cs[csrefKeywordsFixedLock#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="f35f3-125">[!code-cs[csrefKeywordsFixedLock#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="f35f3-126">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="f35f3-126">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f35f3-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f35f3-127">See Also</span></span>  
 <span data-ttu-id="f35f3-128"><xref:System.Reflection.MethodImplAttributes></span><span class="sxs-lookup"><span data-stu-id="f35f3-128"><xref:System.Reflection.MethodImplAttributes></span></span>   
 <span data-ttu-id="f35f3-129"><xref:System.Threading.Mutex></span><span class="sxs-lookup"><span data-stu-id="f35f3-129"><xref:System.Threading.Mutex></span></span>   
 <span data-ttu-id="f35f3-130">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="f35f3-130">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="f35f3-131">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f35f3-131">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="f35f3-132">[Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c) </span><span class="sxs-lookup"><span data-stu-id="f35f3-132">[Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c) </span></span>  
 <span data-ttu-id="f35f3-133">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="f35f3-133">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="f35f3-134">[Mots clés d’instructions](../../../csharp/language-reference/keywords/statement-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="f35f3-134">[Statement Keywords](../../../csharp/language-reference/keywords/statement-keywords.md) </span></span>  
 <span data-ttu-id="f35f3-135">@System.Threading.Monitor</span><span class="sxs-lookup"><span data-stu-id="f35f3-135">@System.Threading.Monitor</span></span>   
 <span data-ttu-id="f35f3-136">[Opérations verrouillées](../../../standard/threading/interlocked-operations.md) </span><span class="sxs-lookup"><span data-stu-id="f35f3-136">[Interlocked Operations](../../../standard/threading/interlocked-operations.md) </span></span>  
 <span data-ttu-id="f35f3-137">[AutoResetEvent](../../../standard/threading/autoresetevent.md) </span><span class="sxs-lookup"><span data-stu-id="f35f3-137">[AutoResetEvent](../../../standard/threading/autoresetevent.md) </span></span>  
 [<span data-ttu-id="f35f3-138">Synchronisation des threads</span><span class="sxs-lookup"><span data-stu-id="f35f3-138">Thread Synchronization</span></span>](http://msdn.microsoft.com/library/413e1f28-a2c5-4eec-8338-aa43e7982ff4)

