---
title: "Guide pratique : utiliser la boucle ForEach pour supprimer les éléments d&quot;un BlockingCollection"
description: "Guide pratique : utiliser la boucle ForEach pour supprimer les éléments d&quot;un BlockingCollection"
keywords: .NET, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: f3db5825-b5c9-4e8b-80bc-e11760d9523e
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: ccee6060aa95b80f424a959e76ceabede473ed86
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a>Guide pratique : utiliser la boucle ForEach pour supprimer les éléments d'un BlockingCollection

Outre l’extraction d’éléments à partir d’un [BlockingCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.BlockingCollection-1) à l’aide des méthodes `Take` et `TryTake`, vous pouvez également utiliser une boucle `foreach` pour supprimer des éléments jusqu’à ce que l’ajout soit terminé et que la collection soit vide. Cela s’appelle une énumération de mutation ou énumération de consommation car, contrairement à une boucle `foreach` typique, cet énumérateur modifie la collection source en supprimant ses éléments.

## <a name="example"></a>Exemple

L’exemple suivant indique comment supprimer tous les éléments d’un `BlockingCollection<T>` à l’aide d’une boucle `foreach`. 

```csharp
using System;
using System.Collections.Concurrent;
using System.Diagnostics;
using System.Threading;
using System.Threading.Tasks;

class Example
{
   // Limit the collection size to 2000 items at any given time.
   // Set itemsToProduce to > 500 to hit the limit.
   const int upperLimit = 1000;

   // Adjust this number to see how it impacts the producing-consuming pattern.
   const int itemsToProduce = 100;

   static BlockingCollection<long> collection = new BlockingCollection<long>(upperLimit);

   // Variables for diagnostic output only.
   static Stopwatch sw = new Stopwatch();
   static int totalAdditions = 0;

   // Counter for synchronizing producers.
   static int producersStillRunning = 2;

   static void Main()
   {
       // Start the stopwatch.
       sw.Start();

       // Queue the Producer threads. Store in an array
       // for use with ContinueWhenAll
       Task[] producers = new Task[2];
       producers[0] = Task.Run(() => RunProducer("A", 0));
       producers[1] = Task.Run(() => RunProducer("B", itemsToProduce));

       // Create a cleanup task that will call CompleteAdding after
       // all producers are done adding items.
       Task cleanup = Task.Factory.ContinueWhenAll(producers, (p) => collection.CompleteAdding());

       // Queue the Consumer thread. Put this call
       // before Parallel.Invoke to begin consuming as soon as
       // the producers add items.
       Task.Run(() => RunConsumer());

       // Keep the console window open while the
       // consumer thread completes its output.
       Console.ReadKey(true);
   }

   static void RunProducer(string ID, int start)
   {

       int additions = 0;
       for (int i = start; i < start + itemsToProduce; i++)
       {
           // The data that is added to the collection.
           long ticks = sw.ElapsedTicks;

           // Display additions and subtractions.
           Console.WriteLine("{0} adding tick value {1}. item# {2}", ID, ticks, i);

           if(!collection.IsAddingCompleted)
               collection.Add(ticks);

           // Counter for demonstration purposes only.
           additions++;

           // Uncomment this line to
           // slow down the producer threads     ing.
           Thread.SpinWait(100000);
       }

       Interlocked.Add(ref totalAdditions, additions);
       Console.WriteLine("{0} is done adding: {1} items", ID, additions);
   }

   static void RunConsumer()
   {
       // GetConsumingEnumerable returns the enumerator for the
       // underlying collection.
       int subtractions = 0;
       foreach (var item in collection.GetConsumingEnumerable())
       {
           Console.WriteLine("Consuming tick value {0} : item# {1} : current count = {2}",
                   item.ToString("D18"), subtractions++, collection.Count);
       }

       Console.WriteLine("Total added: {0} Total consumed: {1} Current count: {2} ",
                           totalAdditions, subtractions, collection.Count);
       sw.Stop();

       Console.WriteLine("Press any key to exit");
   }
}

```

Cet exemple utilise une boucle `foreach` avec la méthode `BlockingCollection<T>.GetConsumingEnumerable` dans le thread consommateur, ce qui provoque la suppression de chaque élément de la collection pendant son énumération. `BlockingCollection<T>` limite le nombre maximal d’éléments présents dans la collection à tout moment. Cette façon d’énumérer la collection bloque le thread consommateur si aucun élément n’est disponible ou si la collection est vide. Dans cet exemple, le blocage n’est pas un problème, car le thread producteur ajoute des éléments plus vite qu’ils ne peuvent être consommés. 

Il n’y a aucune garantie que les éléments soient énumérés dans le même ordre que celui dans lequel ils ont été ajoutés par les threads producteurs.

Pour énumérer la collection sans la modifier, utilisez seulement `foreach` sans la méthode `GetConsumingEnumerable`. Toutefois, il est important de comprendre que ce genre d’énumération représente un instantané de la collection à un moment donné. Si d’autres threads ajoutent ou suppriment des éléments simultanément pendant l’exécution de la boucle, la boucle peut ne pas représenter l’état réel de la collection.

## <a name="see-also"></a>Voir aussi

[System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent)

[Vue d’ensemble de BlockingCollection](blockingcollection-overview.md)

