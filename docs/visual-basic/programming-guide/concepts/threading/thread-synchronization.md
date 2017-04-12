---
title: Thread de synchronisation (Visual Basic) | Documents Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 04f485d1-8333-4510-9e72-c334e7427e7e
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ec8fa89c8921eadee428a90971d9ae4ce305a109
ms.lasthandoff: 03/13/2017

---
# <a name="thread-synchronization-visual-basic"></a>Synchronisation de threads (Visual Basic)
Les sections suivantes décrivent les fonctionnalités et les classes qui peuvent être utilisés pour synchroniser l’accès aux ressources dans les applications multithread.  
  
 Un des avantages de l’utilisation de plusieurs threads dans une application est que chaque thread s’exécute de façon asynchrone. Pour les applications Windows, ainsi, les tâches longues à exécuter en arrière-plan pendant que la fenêtre d’application et les contrôles restent réactives. Pour serveur d’applications, le multithreading fournit la capacité de gérer chaque requête entrante avec un thread différent. Sinon, chaque nouvelle demande ne serait pas prise en charge jusqu'à ce que la demande précédente avait été entièrement satisfaite.  
  
 Toutefois, la nature asynchrone des threads a pour conséquence que l’accès aux ressources telles que les handles de fichiers, les connexions réseau et la mémoire doit être coordonnée. Sinon, deux ou plusieurs threads peuvent accéder à la même ressource en même temps, chacun ignorant les actions des autres. Le résultat est une altération des données imprévisibles.  
  
 Pour les opérations simples sur les types de données numériques intégraux, synchronisation des threads peut se faire avec les membres de la <xref:System.Threading.Interlocked>classe.</xref:System.Threading.Interlocked> Pour toutes les autres données types et les ressources non thread-safe, le multithreading ne peuvent être en toute sécurité effectuées à l’aide de constructions dans cette rubrique.  
  
 Pour des informations générales sur la programmation multithread, consultez :  
  
-   [Principes fondamentaux du Threading managé](http://msdn.microsoft.com/library/b2944911-0e8f-427d-a8bb-077550618935)  
  
-   [Utilisation des Threads et du Threading](http://msdn.microsoft.com/library/9b5ec2cd-121b-4d49-b075-222cf26f2344)  
  
-   [Meilleures pratiques pour le Threading managé](http://msdn.microsoft.com/library/e51988e7-7f4b-4646-a06d-1416cee8d557)  
  
## <a name="the-lock-and-synclock-keywords"></a>Les mots-clés lock et SyncLock  
 Visual Basic `SyncLock` instruction peut être utilisée pour garantir qu’un bloc de code s’exécute jusqu'à son achèvement sans interruption par d’autres threads. Cela s’effectue en obtenant un verrou à exclusion mutuelle pour un objet donné pour la durée du bloc de code.  
  
 Un `SyncLock` instruction Obtient un objet comme argument et est suivie d’un bloc de code qui doit être exécutée par un seul thread à la fois. Exemple :  
  
```vb  
Public Class TestThreading  
    Dim lockThis As New Object  
  
    Public Sub Process()  
        SyncLock lockThis  
            ' Access thread-sensitive resources.  
        End SyncLock  
    End Sub  
End Class  
```  
  
 L’argument fourni pour le `SyncLock` mot clé doit être un objet basé sur un type référence et est utilisé pour définir l’étendue du verrou. Dans l’exemple ci-dessus, la portée de verrouillage est limitée à cette fonction car aucune référence à l’objet `lockThis` existe en dehors de la fonction. Si une telle référence existait, portée de verrouillage s’étendrait à cet objet. En principe, l’objet fourni est utilisé uniquement pour identifier de manière unique la ressource qui est partagée par plusieurs threads, afin d’être une instance de la classe arbitraire. Dans la pratique, toutefois, cet objet représente généralement la ressource pour le thread qui la synchronisation est nécessaire. Par exemple, si un objet conteneur doit être utilisé par plusieurs threads, puis le conteneur peut être passé pour verrouiller, et le bloc de code synchronisé suivant le verrouillage accéderait au conteneur. Tant que les autres threads sont verrouillés sur le même contenir avant d’y accéder, en toute sécurité l’accès à l’objet est synchronisé.  
  
 En général, il est préférable d’éviter le verrouillage sur un `public` type, ou sur des instances d’objet du contrôle de votre application. Par exemple, `lockThis` peut être problématique si l’instance est accessible au public, car le code en dehors de votre contrôle risque de verrouiller l’objet. Cela pourrait créer une situation de blocage où deux ou plusieurs threads attendent la libération du même objet. Le verrouillage sur un type de données public, par opposition à un objet, peut entraîner des problèmes pour la même raison. Verrouillage sur des chaînes littérales est particulièrement risqué, car les chaînes littérales sont *stagiaire* par le common language runtime (CLR). Cela signifie qu’il existe une seule instance d’une chaîne donnée littéral pour l’ensemble du programme, le même objet exact représente le littéral dans tous les domaines d’application, en cours d’exécution sur tous les threads. Par conséquent, un verrou placé sur une chaîne avec le même contenu n’importe où dans les verrous de processus d’application toutes les instances de cette chaîne dans l’application. Par conséquent, il est préférable de verrouiller un membre privé ou protégé qui n’est pas stagiaire. Certaines classes fournissent des membres spécifiquement pour le verrouillage. Le <xref:System.Array>type, par exemple, fournit <xref:System.Array.SyncRoot%2A>.</xref:System.Array.SyncRoot%2A> </xref:System.Array> De nombreux types de collection fournissent un `SyncRoot` membre.  
  
 Pour plus d’informations sur la `SyncLock` instruction, consultez les rubriques suivantes :  
  
-   [SyncLock (instruction)](../../../../visual-basic/language-reference/statements/synclock-statement.md)  
  
-   @System.Threading.Monitor  
  
## <a name="monitors"></a>Analyses  
 Comme le `SyncLock` (mot clé), les moniteurs empêchent des blocs de code d’être exécutés simultanément par plusieurs threads. La <xref:System.Threading.Monitor.Enter%2A>méthode ne permet qu’un seul thread de continuer dans les instructions suivantes ; tous les autres threads sont bloqués jusqu'à ce que le thread d’exécution appelle <xref:System.Threading.Monitor.Exit%2A>.</xref:System.Threading.Monitor.Exit%2A> </xref:System.Threading.Monitor.Enter%2A> Cela équivaut à l’aide de la `SyncLock` (mot clé). Exemple :  
  
```vb  
SyncLock x  
    DoSomething()  
End SyncLock  
```  
  
 Cela équivaut à :  
  
```vb  
Dim obj As Object = CType(x, Object)  
System.Threading.Monitor.Enter(obj)  
Try  
    DoSomething()  
Finally  
    System.Threading.Monitor.Exit(obj)  
End Try  
```  
  
 À l’aide de la `SyncLock` mot clé est généralement préférée à l’aide de la <xref:System.Threading.Monitor>classe directement, les deux, car `SyncLock` est plus concis et parce que `SyncLock` assure que le moniteur sous-jacent est libéré, même si le code protégé lève une exception.</xref:System.Threading.Monitor> Cela est effectué avec le `Finally` (mot clé), qui exécute son bloc de code associé, qu’une exception est levée.  
  
## <a name="synchronization-events-and-wait-handles"></a>Événements de synchronisation et Handles d’attente  
 À l’aide d’un verrou ou une analyse est utile pour empêcher l’exécution simultanée des blocs de code sensibles aux threads, mais ces constructions ne permettent pas d’un thread de communiquer un événement à un autre. Cela nécessite *les événements de synchronisation*, qui sont des objets qui ont une des deux États, signalé et non signalé, qui peut être utilisé pour activer et d’interrompre des threads. Threads peuvent être interrompus en étant obligés d’attendre un événement de synchronisation qui n’est pas signalé et peuvent être activés en modifiant l’état de l’événement signalé. Si un thread tente d’attendre un événement qui est déjà signalé, le thread continue de s’exécuter sans délai.  
  
 Il existe deux types d’événements de synchronisation : <xref:System.Threading.AutoResetEvent>et <xref:System.Threading.ManualResetEvent>.</xref:System.Threading.ManualResetEvent> </xref:System.Threading.AutoResetEvent> Ils diffèrent uniquement dans cette <xref:System.Threading.AutoResetEvent>modifications d’état signalé à non signalé automatiquement à chaque fois qu’il active un thread.</xref:System.Threading.AutoResetEvent> À l’inverse, un <xref:System.Threading.ManualResetEvent>permet à n’importe quel nombre de threads pour être activé que par leur état signalé et revient à un non signalé état lorsque son <xref:System.Threading.EventWaitHandle.Reset%2A>méthode est appelée.</xref:System.Threading.EventWaitHandle.Reset%2A> </xref:System.Threading.ManualResetEvent>  
  
 Peuvent obliger les threads à attendre les événements en appelant une de ces méthodes d’attente, tel que <xref:System.Threading.WaitHandle.WaitOne%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A>, ou <xref:System.Threading.WaitHandle.WaitAll%2A>.</xref:System.Threading.WaitHandle.WaitAll%2A> </xref:System.Threading.WaitHandle.WaitAny%2A> </xref:System.Threading.WaitHandle.WaitOne%2A> <xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=fullName>oblige le thread d’attente jusqu'à ce qu’un événement unique soit signalé, <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=fullName>bloque un thread jusqu'à ce qu’un ou plusieurs événements indiqués soient signalés, et <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=fullName>bloque le thread jusqu'à ce que tous les événements indiqués soient signalés.</xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=fullName> </xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=fullName></xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=fullName> Un événement est signalé lors de sa <xref:System.Threading.EventWaitHandle.Set%2A>méthode est appelée.</xref:System.Threading.EventWaitHandle.Set%2A>  
  
 Dans l’exemple suivant, un thread est créé et démarré par le `Main` (fonction). Le nouveau thread attend un événement à l’aide de la <xref:System.Threading.WaitHandle.WaitOne%2A>méthode.</xref:System.Threading.WaitHandle.WaitOne%2A> Le thread est suspendu jusqu'à ce que l’événement soit signalé par le thread principal qui exécute la `Main` (fonction). Une fois que l’événement soit signalé, le thread auxiliaire est retourné. Dans ce cas, étant donné que l’événement est uniquement utilisé pour l’activation d’un thread, soit le <xref:System.Threading.AutoResetEvent>ou <xref:System.Threading.ManualResetEvent>classes peuvent être utilisés.</xref:System.Threading.ManualResetEvent> </xref:System.Threading.AutoResetEvent>  
  
```vb  
Imports System.Threading  
  
Module Module1  
    Dim autoEvent As AutoResetEvent  
  
    Sub DoWork()  
        Console.WriteLine("   worker thread started, now waiting on event...")  
        autoEvent.WaitOne()  
        Console.WriteLine("   worker thread reactivated, now exiting...")  
    End Sub  
  
    Sub Main()  
        autoEvent = New AutoResetEvent(False)  
  
        Console.WriteLine("main thread starting worker thread...")  
        Dim t As New Thread(AddressOf DoWork)  
        t.Start()  
  
        Console.WriteLine("main thread sleeping for 1 second...")  
        Thread.Sleep(1000)  
  
        Console.WriteLine("main thread signaling worker thread...")  
        autoEvent.Set()  
    End Sub  
End Module  
```  
  
## <a name="mutex-object"></a>Objet mutex  
 A *mutex* est similaire à un moniteur ; elle empêche l’exécution simultanée d’un bloc de code par plusieurs threads simultanément. En fait, le nom « mutex » est une forme raccourcie du terme « mutuellement exclusif ». Toutefois, contrairement aux analyses, un mutex peut être utilisé pour synchroniser des threads de processus. Un mutex est représenté par la <xref:System.Threading.Mutex>classe.</xref:System.Threading.Mutex>  
  
 Synchronisation inter-processus, un mutex est appelé un *mutex nommé* , car il doit être utilisé dans une autre application, et par conséquent, il ne peut pas être partagé au moyen d’une variable globale ou statique. Il doit disposer d’un nom pour que les deux applications puissent accéder au même objet mutex.  
  
 Bien qu’un mutex peut être utilisé pour la synchronisation de threads intra-processus, à l’aide <xref:System.Threading.Monitor>est généralement recommandée, car les moniteurs ont été conçus spécifiquement pour le .NET Framework et par conséquent utilisent les ressources plus efficacement.</xref:System.Threading.Monitor> En revanche, la <xref:System.Threading.Mutex>classe est un wrapper d’une construction Win32.</xref:System.Threading.Mutex> Il est plus puissant qu’un moniteur, un mutex nécessite des transitions d’interopérabilité qui sont plus gourmandes que celles requises par la <xref:System.Threading.Monitor>classe.</xref:System.Threading.Monitor> Pour obtenir un exemple de l’utilisation d’un mutex, consultez [les mutex](http://msdn.microsoft.com/library/9dd06e25-12c0-4a9e-855a-452dc83803e2).  
  
## <a name="interlocked-class"></a>Interlocked (classe)  
 Vous pouvez utiliser les méthodes de la <xref:System.Threading.Interlocked>classe pour éviter les problèmes qui peuvent se produire lorsque plusieurs threads tentent simultanément de mettre à jour ou de comparer une même valeur.</xref:System.Threading.Interlocked> Les méthodes de cette classe vous permettent d’en toute sécurité incrément décrémentent, exchange et comparer des valeurs à partir de n’importe quel thread.  
  
## <a name="readerwriter-locks"></a>Verrous ReaderWriter  
 Dans certains cas, vous souhaiterez verrouiller une ressource uniquement lorsque les données sont écrites et autoriser plusieurs clients à lire simultanément des données ne sont pas actualisées. La <xref:System.Threading.ReaderWriterLock>classe applique un accès exclusif à une ressource lors de la modification par un thread, mais elle permet un accès non exclusif lors de la lecture de la ressource.</xref:System.Threading.ReaderWriterLock> Les verrous ReaderWriter constituent une alternative utile aux verrous exclusifs qui provoquent des autres threads à attendre, même lorsque ces threads n’avez pas besoin de mettre à jour les données.  
  
## <a name="deadlocks"></a>Blocages  
 Synchronisation de threads est très utile dans les applications multithread, mais le risque de création d’un `deadlock`, où plusieurs threads s’attendent mutuellement et l’application s’arrête. Un blocage est analogue à une situation dans laquelle automobiles bloquées à un arrêt de quatre processeurs, et chaque personne est en attente pour l’autre passe. Éviter les verrous mortels est important. la clé est une planification soigneuse. Vous pouvez souvent prévoir les situations de blocage par la représentation graphique des applications multithread, avant de commencer le codage.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.Thread></xref:System.Threading.Thread>   
 <xref:System.Threading.WaitHandle.WaitOne%2A></xref:System.Threading.WaitHandle.WaitOne%2A>   
 <xref:System.Threading.WaitHandle.WaitAny%2A></xref:System.Threading.WaitHandle.WaitAny%2A>   
 <xref:System.Threading.WaitHandle.WaitAll%2A></xref:System.Threading.WaitHandle.WaitAll%2A>   
 <xref:System.Threading.Thread.Join%2A></xref:System.Threading.Thread.Join%2A>   
 <xref:System.Threading.Thread.Start%2A></xref:System.Threading.Thread.Start%2A>   
 <xref:System.Threading.Thread.Sleep%2A></xref:System.Threading.Thread.Sleep%2A>   
 <xref:System.Threading.Monitor></xref:System.Threading.Monitor>   
 <xref:System.Threading.Mutex></xref:System.Threading.Mutex>   
 <xref:System.Threading.AutoResetEvent></xref:System.Threading.AutoResetEvent>   
 <xref:System.Threading.ManualResetEvent></xref:System.Threading.ManualResetEvent>   
 <xref:System.Threading.Interlocked></xref:System.Threading.Interlocked>   
 <xref:System.Threading.WaitHandle></xref:System.Threading.WaitHandle>   
 <xref:System.Threading.EventWaitHandle></xref:System.Threading.EventWaitHandle>   
 <xref:System.Threading></xref:System.Threading>   
 <xref:System.Threading.EventWaitHandle.Set%2A></xref:System.Threading.EventWaitHandle.Set%2A>   
 [Applications multithread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)   
 [SyncLock, instruction](../../../../visual-basic/language-reference/statements/synclock-statement.md)   
 [Mutex](http://msdn.microsoft.com/library/9dd06e25-12c0-4a9e-855a-452dc83803e2)   
 @System.Threading.Monitor   
 [Opérations verrouillées](http://msdn.microsoft.com/library/cbda7114-c752-4f3e-ada1-b1e8dd262f2b)   
 [AutoResetEvent](http://msdn.microsoft.com/library/6d39c48d-6b37-4a9b-8631-f2924cfd9c18)   
 [Synchronisation des données pour le Multithreading](http://msdn.microsoft.com/library/b980eb4c-71d5-4860-864a-6dfe3692430a)
