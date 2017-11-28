---
title: Guide pratique pour utiliser un pool de threads (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 210a9235-83a6-420b-af52-2d6a58e5133f
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9ad5ffb224821c67d227297f8a5a4a1476d77b0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-thread-pool-c"></a>Guide pratique pour utiliser un pool de threads (C#)
Le *regroupement de threads* est une forme de multithreading dans lequel les tâches sont ajoutées à une file d’attente et sont automatiquement lancées lorsque les threads sont créés. Pour plus d’informations, consultez [Regroupement des threads (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md).  
  
 L’exemple suivant utilise le pool de threads .NET Framework pour calculer le résultat de `Fibonacci` pour dix nombres compris entre 20 et 40. Chaque résultat `Fibonacci` est représenté par la classe `Fibonacci`, qui fournit une méthode nommée `ThreadPoolCallback` qui effectue le calcul. Un objet représentant chaque valeur `Fibonacci` est créé, et la méthode `ThreadPoolCallback` est passée à <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>, qui assigne un thread disponible du pool pour exécuter la méthode.  
  
 Étant donné que chaque objet `Fibonacci` se voit attribuer une valeur semi-aléatoire à calculer, et parce que chaque thread est en concurrence pour le temps processeur, vous ne pouvez pas savoir à l’avance la durée nécessaire pour calculer les dix résultats. C’est pourquoi chaque objet `Fibonacci` reçoit une instance de la classe <xref:System.Threading.ManualResetEvent> pendant la construction. Chaque objet signale l’objet d’événement fourni quand son calcul est terminé, ce qui permet au thread principal de bloquer l’exécution avec <xref:System.Threading.WaitHandle.WaitAll%2A> jusqu’à ce que les dix objets `Fibonacci` aient calculé un résultat. La méthode `Main` affiche ensuite chaque résultat `Fibonacci`.  
  
## <a name="example"></a>Exemple  
  
```csharp  
using System;  
using System.Threading;  
  
public class Fibonacci  
{  
    private int _n;  
    private int _fibOfN;  
    private ManualResetEvent _doneEvent;  
  
    public int N { get { return _n; } }  
    public int FibOfN { get { return _fibOfN; } }  
  
    // Constructor.  
    public Fibonacci(int n, ManualResetEvent doneEvent)  
    {  
        _n = n;  
        _doneEvent = doneEvent;  
    }  
  
    // Wrapper method for use with thread pool.  
    public void ThreadPoolCallback(Object threadContext)  
    {  
        int threadIndex = (int)threadContext;  
        Console.WriteLine("thread {0} started...", threadIndex);  
        _fibOfN = Calculate(_n);  
        Console.WriteLine("thread {0} result calculated...", threadIndex);  
        _doneEvent.Set();  
    }  
  
    // Recursive method that calculates the Nth Fibonacci number.  
    public int Calculate(int n)  
    {  
        if (n <= 1)  
        {  
            return n;  
        }  
  
        return Calculate(n - 1) + Calculate(n - 2);  
    }  
}  
  
public class ThreadPoolExample  
{  
    static void Main()  
    {  
        const int FibonacciCalculations = 10;  
  
        // One event is used for each Fibonacci object.  
        ManualResetEvent[] doneEvents = new ManualResetEvent[FibonacciCalculations];  
        Fibonacci[] fibArray = new Fibonacci[FibonacciCalculations];  
        Random r = new Random();  
  
        // Configure and start threads using ThreadPool.  
        Console.WriteLine("launching {0} tasks...", FibonacciCalculations);  
        for (int i = 0; i < FibonacciCalculations; i++)  
        {  
            doneEvents[i] = new ManualResetEvent(false);  
            Fibonacci f = new Fibonacci(r.Next(20, 40), doneEvents[i]);  
            fibArray[i] = f;  
            ThreadPool.QueueUserWorkItem(f.ThreadPoolCallback, i);  
        }  
  
        // Wait for all threads in pool to calculate.  
        WaitHandle.WaitAll(doneEvents);  
        Console.WriteLine("All calculations are complete.");  
  
        // Display the results.  
        for (int i= 0; i<FibonacciCalculations; i++)  
        {  
            Fibonacci f = fibArray[i];  
            Console.WriteLine("Fibonacci({0}) = {1}", f.N, f.FibOfN);  
        }  
    }  
}  
```  
  
 Voici un exemple de sortie.  
  
```  
launching 10 tasks...  
thread 0 started...  
thread 1 started...  
thread 1 result calculated...  
thread 2 started...  
thread 2 result calculated...  
thread 3 started...  
thread 3 result calculated...  
thread 4 started...  
thread 0 result calculated...  
thread 5 started...  
thread 5 result calculated...  
thread 6 started...  
thread 4 result calculated...  
thread 7 started...  
thread 6 result calculated...  
thread 8 started...  
thread 8 result calculated...  
thread 9 started...  
thread 9 result calculated...  
thread 7 result calculated...  
All calculations are complete.  
Fibonacci(38) = 39088169  
Fibonacci(29) = 514229  
Fibonacci(25) = 75025  
Fibonacci(22) = 17711  
Fibonacci(38) = 39088169  
Fibonacci(29) = 514229  
Fibonacci(29) = 514229  
Fibonacci(38) = 39088169  
Fibonacci(21) = 10946  
Fibonacci(27) = 196418  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.Mutex>  
 <xref:System.Threading.WaitHandle.WaitAll%2A>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.EventWaitHandle.Set%2A>  
 <xref:System.Threading.ThreadPool>  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Monitor>  
 [Mise en pool de threads (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)  
 [Threading (C#)](../../../../csharp/programming-guide/concepts/threading/index.md)  
 [Sécurité](../../../../standard/security/index.md)
