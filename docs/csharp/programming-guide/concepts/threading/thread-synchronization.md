---
title: Synchronisation des threads (C#) | Microsoft Docs
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: e42b1be6-c93c-479f-a148-be0759f1a4e1
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: f8d51aa1c50c097577a575be9b5da4b9e0effc55
ms.contentlocale: fr-fr
ms.lasthandoff: 05/10/2017

---
# <a name="thread-synchronization-c"></a>Synchronisation des threads (C#)
Les sections suivantes décrivent les fonctionnalités et les classes qui peuvent être utilisées pour synchroniser l’accès aux ressources dans les applications multithread.  
  
 L’un des avantages de l’utilisation de plusieurs threads dans une application est que chaque thread s’exécute de façon asynchrone. Pour les applications Windows, cela permet d’exécuter les tâches longues en arrière-plan pendant que la fenêtre et les contrôles de l’application restent réactifs. Pour les applications serveur, le multithreading offre la possibilité de gérer chaque demande entrante avec un thread différent. Sinon, une nouvelle demande ne serait pas prise en charge tant que la demande précédente n’aurait pas été entièrement satisfaite.  
  
 Toutefois, la nature asynchrone des threads signifie que l’accès à des ressources telles que des descripteurs de fichiers, des connexions réseau et la mémoire doit être coordonné. Sinon, deux threads ou plus pourraient accéder à la même ressource en même temps, chacun ignorant les actions des autres. Il en résulterait une altération imprévisible des données.  
  
 Pour les opérations simples sur les types de données numériques intégraux, la synchronisation des threads peut se faire avec les membres de la classe <xref:System.Threading.Interlocked>. Pour tous les autres types de données et les ressources non thread-safe, le multithreading ne peut être réalisé en toute sécurité qu’en utilisant les constructions fournies dans cette rubrique.  
  
 Pour obtenir des informations générales sur la programmation multithread, consultez :  
  
-   [Éléments fondamentaux du threading managé](../../../../standard/threading/managed-threading-basics.md)  
  
-   [Utilisation des threads et du threading](../../../../standard/threading/using-threads-and-threading.md)  
  
-   [Bonnes pratiques de threading géré](../../../../standard/threading/managed-threading-best-practices.md)  
  
## <a name="the-lock-keyword"></a>Mot clé lock  
 L’instruction C# `lock` permet de garantir qu’un bloc de code s’exécute jusqu’à son achèvement sans être interrompu par d’autres threads. Pour cela, elle obtient un verrou d’exclusion mutuelle pour un objet donné pour la durée du bloc de code.  
  
 Une instruction `lock` se voit attribuer un objet comme argument et est suivie par un bloc de code qui doit être exécuté par un seul thread à la fois. Exemple :  
  
```csharp  
public class TestThreading  
{  
    private System.Object lockThis = new System.Object();  
  
    public void Process()  
    {  
  
        lock (lockThis)  
        {  
            // Access thread-sensitive resources.  
        }  
    }  
  
}  
```  
  
 L’argument fourni au mot clé `lock` doit être un objet basé sur un type référence servant à définir la portée du verrou. Dans l’exemple ci-dessus, la portée du verrou est limitée à cette fonction car aucune référence à l’objet `lockThis` n’existe en dehors de la fonction. Si une telle référence existait, la portée du verrou s’étendrait à cet objet. À proprement parler, l’objet fourni est utilisé seulement pour identifier de manière unique la ressource qui est partagée entre plusieurs threads, si bien qu’il peut s’agir d’une instance de classe arbitraire. Dans la pratique, toutefois, cet objet représente généralement la ressource pour laquelle la synchronisation des threads est nécessaire. Par exemple, si un objet conteneur doit être utilisé par plusieurs threads, le conteneur peut être passé au verrou, et le bloc de code synchronisé suivant le verrou accéderait au conteneur. L’accès à l’objet est bien synchronisé du moment que les autres threads appliquent un verrou sur le même conteneur avant d’y accéder.  
  
 En général, il est préférable d’éviter d’appliquer un verrou sur un type `public` ou sur des instances d’objet non contrôlées par votre application. Par exemple, `lock(this)` peut être problématique si l’instance est accessible publiquement, car du code en dehors de votre contrôle risque d’appliquer également un verrou sur l’objet. Cela pourrait créer des situations de blocage où deux threads ou plus attendent la libération du même objet. L’application d’un verrou sur un type de données public, par opposition à un objet, peut entraîner des problèmes pour la même raison. L’application d’un verrou sur des chaînes littérales est particulièrement risqué, car les chaînes littérales sont *intégrées* par le CLR (Common Language Runtime). Cela signifie qu’il existe une seule instance d’une chaîne littérale donnée pour l’ensemble du programme. Un seul et même objet représente le littéral dans tous les domaines d’application en cours d’exécution, sur tous les threads. Par conséquent, un verrou placé sur une chaîne avec le même contenu n’importe où dans le processus d’application verrouille toutes les instances de cette chaîne dans l’application. Par conséquent, il est préférable de verrouiller un membre privé ou protégé qui n’est pas intégré. Certaines classes fournissent des membres spécifiquement pour le verrouillage. Le type <xref:System.Array>, par exemple, fournit <xref:System.Array.SyncRoot%2A>. De nombreux types de collection fournissent également un membre `SyncRoot`.  
  
 Pour plus d’informations sur l’instruction `lock`, consultez les rubriques suivantes :  
  
-   [lock, instruction](../../../../csharp/language-reference/keywords/lock-statement.md)  
  
-   @System.Threading.Monitor  
  
## <a name="monitors"></a>Analyses  
 Comme le mot clé `lock`, les moniteurs empêchent l’exécution simultanée de blocs de code par plusieurs threads. La méthode <xref:System.Threading.Monitor.Enter%2A> permet à un seul thread de passer aux instructions suivantes ; tous les autres threads sont bloqués jusqu’à ce que le thread d’exécution appelle <xref:System.Threading.Monitor.Exit%2A>. Cela équivaut à utiliser le mot clé `lock`. Exemple :  
  
```csharp  
lock (x)  
{  
    DoSomething();  
}  
```  
  
 Ceci équivaut à :  
  
```csharp  
System.Object obj = (System.Object)x;  
System.Threading.Monitor.Enter(obj);  
try  
{  
    DoSomething();  
}  
finally  
{  
    System.Threading.Monitor.Exit(obj);  
}  
```  
  
 L’utilisation du mot clé `lock` est généralement préférée à l’utilisation directe de la classe <xref:System.Threading.Monitor>. En effet, `lock` est plus concis et `lock` garantit la libération du moniteur sous-jacent, même si le code protégé lève une exception. Le mot clé `finally` permet cela ; il exécute son bloc de code associé qu’une exception soit levée ou non.  
  
## <a name="synchronization-events-and-wait-handles"></a>Événements de synchronisation et handles d’attente  
 L’utilisation d’un verrou ou d’un moniteur est utile pour empêcher l’exécution simultanée de blocs de code sensibles aux threads, mais ces constructions ne permettent pas à un thread de communiquer un événement à un autre. Cela nécessite des *événements de synchronisation* Ce sont des objets qui possèdent l’un des deux états suivants : signalé ou non signalé, et qui peuvent être utilisés pour activer et suspendre des threads. Il est possible de suspendre des threads en les obligeant à attendre un événement de synchronisation non signalé, et de les activer en changeant l’état de l’événement sur signalé. Si un thread tente d’attendre un événement qui est déjà signalé, le thread continue de s’exécuter sans délai.  
  
 Il existe deux types d’événements de synchronisation : <xref:System.Threading.AutoResetEvent> et <xref:System.Threading.ManualResetEvent>. Leur seule différence est que <xref:System.Threading.AutoResetEvent> passe automatiquement de l’état signalé à l’état non signalé chaque fois qu’il active un thread. À l’inverse, un <xref:System.Threading.ManualResetEvent> permet l’activation de n’importe quel nombre de threads en fonction de son état signalé et revient à un état non signalé quand sa méthode <xref:System.Threading.EventWaitHandle.Reset%2A> est appelée.  
  
 Vous pouvez obliger les threads à attendre les événements en appelant une méthode d’attente, comme <xref:System.Threading.WaitHandle.WaitOne%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A> ou <xref:System.Threading.WaitHandle.WaitAll%2A>. <xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=fullName> oblige le thread à attendre qu’un événement unique soit signalé, <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=fullName> bloque un thread jusqu'à ce qu’un ou plusieurs événements indiqués soient signalés, et <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=fullName> bloque le thread jusqu'à ce que tous les événements indiqués soient signalés. Un événement est signalé quand sa méthode <xref:System.Threading.EventWaitHandle.Set%2A> est appelée.  
  
 Dans l’exemple suivant, un thread est créé et démarré par la fonction `Main`. Le nouveau thread attend un événement à l’aide de la méthode <xref:System.Threading.WaitHandle.WaitOne%2A>. Le thread est suspendu jusqu’à ce que l’événement soit signalé par le thread principal qui exécute la fonction `Main`. Une fois que l’événement a été signalé, le thread auxiliaire est retourné. Dans ce cas, comme l’événement est uniquement utilisé pour l’activation d’un seul thread, les classes <xref:System.Threading.AutoResetEvent> ou <xref:System.Threading.ManualResetEvent> peuvent être utilisées.  
  
```csharp  
using System;  
using System.Threading;  
  
class ThreadingExample  
{  
    static AutoResetEvent autoEvent;  
  
    static void DoWork()  
    {  
        Console.WriteLine("   worker thread started, now waiting on event...");  
        autoEvent.WaitOne();  
        Console.WriteLine("   worker thread reactivated, now exiting...");  
    }  
  
    static void Main()  
    {  
        autoEvent = new AutoResetEvent(false);  
  
        Console.WriteLine("main thread starting worker thread...");  
        Thread t = new Thread(DoWork);  
        t.Start();  
  
        Console.WriteLine("main thread sleeping for 1 second...");  
        Thread.Sleep(1000);  
  
        Console.WriteLine("main thread signaling worker thread...");  
        autoEvent.Set();  
    }  
}  
```  
  
## <a name="mutex-object"></a>Objet mutex  
 Un *mutex* est similaire à un moniteur. Il empêche l’exécution simultanée d’un bloc de code par plusieurs threads à la fois. En fait, le nom « mutex » est une forme raccourcie du terme « mutuellement exclusif ». Contrairement aux moniteurs, toutefois, un mutex peut être utilisé pour synchroniser des threads entre des processus. Un mutex est représenté par la classe <xref:System.Threading.Mutex>.  
  
 Quand il est utilisé pour une synchronisation inter-processus, un mutex est qualifié de *mutex nommé*, car il doit être utilisé dans une autre application et, par conséquent, il ne peut pas être partagé au moyen d’une variable globale ou statique. Il doit se voir attribuer un nom pour que les deux applications puissent accéder au même objet mutex.  
  
 Un mutex peut être utilisé pour la synchronisation intra-processus de threads, mais l’utilisation de <xref:System.Threading.Monitor> est généralement préférée, car les moniteurs ont été conçus spécifiquement pour le .NET Framework et, par conséquent, font meilleur usage des ressources. À l’inverse, la classe <xref:System.Threading.Mutex> est un wrapper d’une construction Win32. Bien que plus puissant qu’un moniteur, un mutex nécessite des transitions d’interopérabilité qui sont plus gourmandes en ressources informatiques que celles demandées par la classe <xref:System.Threading.Monitor>. Pour obtenir un exemple d’utilisation d’un mutex, consultez [Mutex](../../../../standard/threading/mutexes.md).  
  
## <a name="interlocked-class"></a>Classe Interlocked  
 Vous pouvez utiliser les méthodes de la classe <xref:System.Threading.Interlocked> pour éviter les problèmes qui peuvent se produire quand plusieurs threads tentent simultanément de mettre à jour ou de comparer la même valeur. Les méthodes de cette classe vous permettent d’incrémenter, de décrémenter, d’échanger et de comparer en toute sécurité des valeurs à partir de n’importe quel thread.  
  
## <a name="readerwriter-locks"></a>Verrous ReaderWriter  
 Dans certains cas, vous pouvez souhaiter verrouiller une ressource seulement lors de l’écriture de données et autoriser plusieurs clients à lire simultanément les données quand celles-ci ne sont pas en cours d’actualisation. La classe <xref:System.Threading.ReaderWriterLock> applique un accès exclusif à une ressource quand un thread modifie cette ressource, mais elle permet un accès non exclusif lors de la lecture de la ressource. Les verrous ReaderWriter constituent une alternative utile aux verrous exclusifs, lesquels obligent les autres threads à attendre même lorsque ces threads n’ont pas besoin de mettre à jour les données.  
  
## <a name="deadlocks"></a>Interblocages (deadlocks)  
 La synchronisation des threads est précieuse dans les applications multithread, mais implique toujours un risque de créer un interblocage (`deadlock`), lorsque plusieurs threads s’attendent mutuellement et que l’application s’arrête. Un interblocage s’apparente au cas d’un carrefour où chaque voie est munie d’un stop et où chaque automobiliste attend que l’autre passe. Il est important d’éviter les interblocages et seule une planification rigoureuse le permet. Vous pouvez souvent prévoir un interblocage en représentant graphiquement les applications multithread avant de commencer le codage.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.Thread>   
 <xref:System.Threading.WaitHandle.WaitOne%2A>   
 <xref:System.Threading.WaitHandle.WaitAny%2A>   
 <xref:System.Threading.WaitHandle.WaitAll%2A>   
 <xref:System.Threading.Thread.Join%2A>   
 <xref:System.Threading.Thread.Start%2A>   
 <xref:System.Threading.Thread.Sleep%2A>   
 <xref:System.Threading.Monitor>   
 <xref:System.Threading.Mutex>   
 <xref:System.Threading.AutoResetEvent>   
 <xref:System.Threading.ManualResetEvent>   
 <xref:System.Threading.Interlocked>   
 <xref:System.Threading.WaitHandle>   
 <xref:System.Threading.EventWaitHandle>   
 <xref:System.Threading>   
 <xref:System.Threading.EventWaitHandle.Set%2A>   
 [Applications multithread (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)   
 [lock, instruction](../../../../csharp/language-reference/keywords/lock-statement.md)   
 [Mutex](../../../../standard/threading/mutexes.md)   
 @System.Threading.Monitor   
 [Opérations verrouillées](../../../../standard/threading/interlocked-operations.md)   
 [AutoResetEvent](../../../../standard/threading/autoresetevent.md)   
 [Synchronisation des données pour le multithreading](../../../../standard/threading/synchronizing-data-for-multithreading.md)
