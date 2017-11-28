---
title: "lock, instruction (Informations de référence sur C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords: lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
caps.latest.revision: "43"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eb48c2b1554ad2817406eaef42b4cb336ea46862
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="18325-102">lock, instruction (Informations de référence sur C#)</span><span class="sxs-lookup"><span data-stu-id="18325-102">lock Statement (C# Reference)</span></span>
<span data-ttu-id="18325-103">Le mot clé `lock` marque un bloc d’instructions comme étant une section critique en obtenant le verrou d’exclusion mutuelle pour un objet donné, en exécutant une instruction, puis en libérant le verrou.</span><span class="sxs-lookup"><span data-stu-id="18325-103">The `lock` keyword marks a statement block as a critical section by obtaining the mutual-exclusion lock for a given object, executing a statement, and then releasing the lock.</span></span> <span data-ttu-id="18325-104">L’exemple suivant inclut une instruction `lock`.</span><span class="sxs-lookup"><span data-stu-id="18325-104">The following example includes a `lock` statement.</span></span>  
  
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
  
 <span data-ttu-id="18325-105">Pour plus d’informations, consultez [Synchronisation des threads](../../programming-guide/concepts/threading/thread-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="18325-105">For more information, see [Thread Synchronization](../../programming-guide/concepts/threading/thread-synchronization.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18325-106">Remarques</span><span class="sxs-lookup"><span data-stu-id="18325-106">Remarks</span></span>  
 <span data-ttu-id="18325-107">Le mot clé `lock` garantit qu’un thread n’entre pas dans une section critique de code alors qu’un autre thread est dans cette section critique.</span><span class="sxs-lookup"><span data-stu-id="18325-107">The `lock` keyword ensures that one thread does not enter a critical section of code while another thread is in the critical section.</span></span> <span data-ttu-id="18325-108">Si un autre thread tente d’entrer dans un code verrouillé, il attend, en restant bloqué jusqu’à ce que l’objet soit libéré.</span><span class="sxs-lookup"><span data-stu-id="18325-108">If another thread tries to enter a locked code, it will wait, block, until the object is released.</span></span>  
  
 <span data-ttu-id="18325-109">La section [Threading](../../programming-guide/concepts/threading/index.md) présente le threading.</span><span class="sxs-lookup"><span data-stu-id="18325-109">The section [Threading](../../programming-guide/concepts/threading/index.md) discusses threading.</span></span>  
  
 <span data-ttu-id="18325-110">Le mot clé `lock` appelle <xref:System.Threading.Monitor.Enter%2A> au début du bloc et <xref:System.Threading.Monitor.Exit%2A> à la fin du bloc.</span><span class="sxs-lookup"><span data-stu-id="18325-110">The `lock` keyword calls <xref:System.Threading.Monitor.Enter%2A> at the start of the block and <xref:System.Threading.Monitor.Exit%2A> at the end of the block.</span></span> <span data-ttu-id="18325-111">Une exception <xref:System.Threading.ThreadInterruptedException> est levée si <xref:System.Threading.Thread.Interrupt%2A> interrompt un thread qui attend de passer une instruction `lock`.</span><span class="sxs-lookup"><span data-stu-id="18325-111">A <xref:System.Threading.ThreadInterruptedException> is thrown if <xref:System.Threading.Thread.Interrupt%2A> interrupts a thread that is waiting to enter a `lock` statement.</span></span>  
  
 <span data-ttu-id="18325-112">D’une façon générale, évitez de verrouiller sur un type `public` ou sur des instances qui sont au-delà du contrôle de votre code.</span><span class="sxs-lookup"><span data-stu-id="18325-112">In general, avoid locking on a `public` type, or instances beyond your code's control.</span></span> <span data-ttu-id="18325-113">Les constructions courantes `lock (this)`, `lock (typeof (MyType))` et `lock ("myLock")` enfreignent cette directive :</span><span class="sxs-lookup"><span data-stu-id="18325-113">The common constructs `lock (this)`, `lock (typeof (MyType))`, and `lock ("myLock")` violate this guideline:</span></span>  
  
-   <span data-ttu-id="18325-114">`lock (this)` est un problème si l’instance est accessible publiquement.</span><span class="sxs-lookup"><span data-stu-id="18325-114">`lock (this)` is a problem if the instance can be accessed publicly.</span></span>  
  
-   <span data-ttu-id="18325-115">`lock (typeof (MyType))` est un problème si `MyType` est accessible publiquement.</span><span class="sxs-lookup"><span data-stu-id="18325-115">`lock (typeof (MyType))` is a problem if `MyType` is publicly accessible.</span></span>  
  
-   <span data-ttu-id="18325-116">`lock("myLock")` est un problème, car tout autre code dans le processus utilisant la même chaîne partagera le même verrou.</span><span class="sxs-lookup"><span data-stu-id="18325-116">`lock("myLock")` is a problem because any other code in the process using the same string, will share the same lock.</span></span>  
  
 <span data-ttu-id="18325-117">La bonne pratique consiste à définir un objet `private` à verrouiller, ou une variable objet `private static` pour protéger les données communes à toutes les instances.</span><span class="sxs-lookup"><span data-stu-id="18325-117">Best practice is to define a `private` object to lock on, or a `private static` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="18325-118">Vous ne pouvez pas utiliser le mot clé [await](../../../csharp/language-reference/keywords/await.md) dans le corps d’une instruction `lock`.</span><span class="sxs-lookup"><span data-stu-id="18325-118">You can't use the [await](../../../csharp/language-reference/keywords/await.md) keyword in the body of a `lock` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18325-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="18325-119">Example</span></span>  
 <span data-ttu-id="18325-120">L’exemple suivant montre une utilisation simple des threads sans verrouillage en C#.</span><span class="sxs-lookup"><span data-stu-id="18325-120">The following sample shows a simple use of threads without locking in C#.</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="18325-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="18325-121">Example</span></span>  
 <span data-ttu-id="18325-122">L’exemple suivant utilise des threads et `lock`.</span><span class="sxs-lookup"><span data-stu-id="18325-122">The following sample uses threads and `lock`.</span></span> <span data-ttu-id="18325-123">Tant que l’instruction `lock` est présente, le bloc d’instructions est une section critique et `balance` ne devient jamais un nombre négatif.</span><span class="sxs-lookup"><span data-stu-id="18325-123">As long as the `lock` statement is present, the statement block is a critical section and `balance` will never become a negative number.</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="18325-124">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="18325-124">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="18325-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18325-125">See Also</span></span>  
 <xref:System.Reflection.MethodImplAttributes>  
 <xref:System.Threading.Mutex>  
 [<span data-ttu-id="18325-126">Référence C#</span><span class="sxs-lookup"><span data-stu-id="18325-126">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="18325-127">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="18325-127">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="18325-128">Thread</span><span class="sxs-lookup"><span data-stu-id="18325-128">Threading</span></span>](../../programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="18325-129">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="18325-129">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="18325-130">Mots clés d’instructions</span><span class="sxs-lookup"><span data-stu-id="18325-130">Statement Keywords</span></span>](../../../csharp/language-reference/keywords/statement-keywords.md)  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="18325-131">Opérations verrouillées</span><span class="sxs-lookup"><span data-stu-id="18325-131">Interlocked Operations</span></span>](../../../standard/threading/interlocked-operations.md)  
 [<span data-ttu-id="18325-132">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="18325-132">AutoResetEvent</span></span>](../../../standard/threading/autoresetevent.md)  
 [<span data-ttu-id="18325-133">Synchronisation des threads</span><span class="sxs-lookup"><span data-stu-id="18325-133">Thread Synchronization</span></span>](../../programming-guide/concepts/threading/thread-synchronization.md)
