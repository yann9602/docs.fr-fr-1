---
title: "Managed Threading Best Practices | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "threading [.NET Framework], design guidelines"
  - "threading [.NET Framework], best practices"
  - "managed threading"
ms.assetid: e51988e7-7f4b-4646-a06d-1416cee8d557
caps.latest.revision: 19
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 19
---
# Managed Threading Best Practices
Le multithreading exige une programmation attentive.  Vous pouvez réduire la complexité pour la plupart des tâches en mettant les demandes en file d'attente pour une exécution par un thread du pool.  Cette rubrique traite des situations les plus difficiles telles que la coordination du travail de plusieurs threads ou la gestion des threads qui bloquent.  
  
> [!NOTE]
>  Dans le [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], la bibliothèque parallèle de tâches et PLINQ fournissent des API qui réduisent en partie la complexité et les risques de la programmation multithread.  Pour plus d'informations, consultez [Parallel Programming](../../../docs/standard/parallel-programming/index.md).  
  
## Interblocages et conditions de concurrence critique  
 Le multithreading résout les problèmes de débit et de réactivité, mais ce faisant il introduit de nouveaux problèmes : les interblocages et les conditions de concurrence critique.  
  
### Interblocages  
 Un interblocage se produit lorsque l'un des deux threads essaie de verrouiller une ressource que l'autre thread a déjà verrouillée.  Aucun thread ne peut avancer.  
  
 De nombreuses méthodes des classes de thread managé fournissent des délais pour vous aider à détecter des interblocages.  Par exemple, le code suivant tente d'acquérir un verrou sur l'instance actuelle.  Si ce verrou n'est pas obtenu en 300 millisecondes, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=fullName> retourne **false**.  
  
```vb  
If Monitor.TryEnter(lockObject, 300) Then  
    Try  
        ' Place code protected by the Monitor here.  
    Finally  
        Monitor.Exit(Me)  
    End Try  
Else  
    ' Code to execute if the attempt times out.  
End If  
```  
  
```csharp  
if (Monitor.TryEnter(lockObject, 300)) {  
    try {  
        // Place code protected by the Monitor here.  
    }  
    finally {  
        Monitor.Exit(this);  
    }  
}  
else {  
    // Code to execute if the attempt times out.  
}  
```  
  
### Conditions de concurrence critique  
 Une condition de concurrence critique est une bogue qui se produit lorsque le résultat d'un programme dépend du premier des threads, parmi au moins deux threads, qui atteint un bloc de code particulier.  L'exécution répétée du programme produit des résultats différents, et il est impossible de prédire le résultat d'une exécution donnée.  
  
 Un exemple simple de condition de concurrence critique est l'incrémentation d'un champ.  Supposons qu'une classe possède un champ **static** privé \(**Shared** en Visual Basic\) qui est incrémenté à chaque création d'une instance de la classe à l'aide de code tel que `objCt++;` \(C\#\) ou `objCt += 1` \(Visual Basic\).  Cette opération nécessite le chargement dans un registre de la valeur à partir de `objCt`, l'incrémentation de cette valeur et son stockage dans `objCt`.  
  
 Dans une application multithread, un thread qui a chargé et incrémenté la valeur peut être interrompu par un autre thread qui effectue les trois étapes ; lorsque le premier thread reprend l'exécution et stocke sa valeur, il remplace `objCt` sans tenir compte du fait que la valeur a changé entre\-temps.  
  
 Cette condition de concurrence critique particulière est évitée facilement en utilisant des méthodes de la classe <xref:System.Threading.Interlocked>, comme <xref:System.Threading.Interlocked.Increment%2A?displayProperty=fullName>.  Pour plus d'informations sur d'autres techniques permettant de synchroniser des données entre plusieurs threads, consultez [Synchronisation des données pour le multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).  
  
 Les conditions de concurrence critique peuvent également se produire lorsque vous synchronisez les activités de plusieurs threads.  Chaque fois que vous écrivez une ligne de code, vous devez anticiper ce qui peut se produire si un thread était interrompu avant l'exécution de la ligne \(ou avant les instructions machine individuelles qui composent la ligne\), et qu'un autre thread prenne le relais.  
  
## Nombre de processeurs  
 La plupart des ordinateurs ont désormais plusieurs processeurs \(également appelés cœurs\), même des petits appareils tels que les tablettes et les téléphones.  Si vous savez que vous développez un logiciel qui s'exécutera également sur des ordinateurs à un seul processeur, vous devez être conscient que le multithreading résout différents problèmes pour les ordinateurs à un seul processeur et les ordinateurs multiprocesseurs.  
  
### Ordinateurs multiprocesseurs  
 Le multithreading fournit un débit supérieur.  Dix processeurs peuvent effectuer dix fois plus de travail qu'un seul processeur, mais uniquement si le travail est divisé de telle sorte que les dix processeurs puissent travailler simultanément ; les threads fournissent un moyen facile de diviser le travail et de tirer parti de la puissance de traitement supplémentaire.  Si vous utilisez le multithreading sur un ordinateur multiprocesseur :  
  
-   Le nombre de threads qui peuvent s'exécuter simultanément est limité par le nombre de processeurs.  
  
-   Un thread d'arrière\-plan s'exécute uniquement lorsque le nombre de threads de premier plan est inférieur au nombre de processeurs.  
  
-   Lorsque vous appelez la méthode <xref:System.Threading.Thread.Start%2A?displayProperty=fullName> sur un thread, ce thread peut ou ne peut pas démarrer son exécution immédiatement selon le nombre de processeurs et le nombre de threads qui attendent actuellement de s'exécuter.  
  
-   Les conditions de concurrence critique peuvent se produire non seulement du fait de l'interruption inattendue des threads mais parce que deux threads qui s'exécutent sur des processeurs différents s'acheminent peut\-être vers le même bloc de code.  
  
### Ordinateurs à processeurs uniques  
 Le multithreading fournit une plus grande réactivité à l'utilisateur de l'ordinateur et utilise le temps d'inactivité pour les tâches en arrière\-plan.  Si vous utilisez le multithreading sur un ordinateur à processeur unique :  
  
-   Seul un thread s'exécute à tout moment.  
  
-   Un thread en arrière\-plan s'exécute uniquement lorsque le thread utilisateur principal est inactif.  Un thread en premier plan qui s'exécute constamment prive les threads en arrière\-plan de temps processeur.  
  
-   Lorsque vous appelez la méthode <xref:System.Threading.Thread.Start%2A?displayProperty=fullName> sur un thread, ce thread ne s'exécute pas tant que le thread en cours ne cède pas ou n'est pas interrompu par le système d'exploitation.  
  
-   Les conditions de concurrence critique se produisent généralement parce que le programmeur n'a pas anticipé le fait qu'un thread peut être interrompu à un moment délicat, ce qui permet parfois à un autre thread de parvenir au bloc de code le premier.  
  
## Membres statiques et constructeurs statiques  
 Une classe n'est pas initialisée tant que l'exécution de son constructeur de classe \(constructeur `static` en C\#, `Shared Sub New` dans Visual Basic\) n'est pas terminée.  Pour empêcher l'exécution de code sur un type non initialisé, le Common Language Runtime bloque tous les appels d'autres threads aux membres `static` de la classe \(membres `Shared` dans Visual Basic\) jusqu'à ce que l'exécution du constructeur de classe soit terminée.  
  
 Par exemple, si un constructeur de classe démarre un nouveau thread et que la procédure de thread appelle un membre `static` de la classe, le nouveau thread se bloque jusqu'à ce que le constructeur de classe ait terminé.  
  
 Cela s'applique à tout type pouvant disposer d'un constructeur `static`.  
  
## Recommandations générales  
 Observez les recommandations suivantes lors de l'utilisation de plusieurs threads :  
  
-   N'utilisez pas <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName> pour mettre fin à d'autres threads.  L'appel à **Abort** sur un autre thread revient à lever une exception sur ce thread, sans savoir à quel point ce thread est parvenu dans son traitement.  
  
-   N'utilisez pas  <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName> et <xref:System.Threading.Thread.Resume%2A?displayProperty=fullName> pour synchroniser les activités de plusieurs threads.  Utilisez <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent> et <xref:System.Threading.Monitor>.  
  
-   Ne contrôlez pas l'exécution des threads de travail à partir de votre programme principal \(en utilisant des événements, par exemple\).  À la place, concevez votre programme de telle sorte que les threads de travail soient chargés d'attendre que du travail soit disponible, d'exécuter ce travail et de notifier les autres parties de votre programme une fois terminé.  Si vos threads de travail ne provoquent pas de blocage, utilisez des threads du pool de threads.  <xref:System.Threading.Monitor.PulseAll%2A?displayProperty=fullName> est utile dans les cas où les threads de travail se bloquent.  
  
-   N'utilisez pas de types comme objets lock.  Autrement dit, évitez les codes tels que `lock(typeof(X))` en C\# ou `SyncLock(GetType(X))` dans Visual Basic, ou l'utilisation de <xref:System.Threading.Monitor.Enter%2A?displayProperty=fullName> avec des objets <xref:System.Type>.  Pour un type donné, il existe une seule instance de <xref:System.Type?displayProperty=fullName> par domaine d'application.  Si le type sur lequel vous acquérez un verrou est public, tout code, autre que le vôtre, peut acquérir des verrous sur celui\-ci, ce qui entraîne des interblocages.  Pour plus d'informations, consultez [Reliability Best Practices](../../../docs/framework/performance/reliability-best-practices.md).  
  
-   Soyez vigilants lors du verrouillage d'instances, par exemple `lock(this)` en C\# ou `SyncLock(Me)` dans Visual Basic.  Si un autre code de votre application, externe au type, acquiert un verrou sur l'objet, des interblocages peuvent se produire.  
  
-   Veillez à ce qu'un thread qui est entré dans un moniteur quitte toujours ce moniteur, même si une exception se produit tandis que le thread se trouve dans le moniteur.  L'instruction C\# [lock](../Topic/lock%20Statement%20\(C%23%20Reference\).md) et l'instruction Visual Basic [SyncLock](../../../ocs/visual-basic/language-reference/statements/synclock-statement.md) fournissent ce comportement automatiquement en se servant d'un bloc **finally** pour garantir l'appel à <xref:System.Threading.Monitor.Exit%2A?displayProperty=fullName>.  Si vous ne pouvez pas garantir l'appel à **Exit**, envisagez de changer votre design afin d'utiliser **Mutex**.  Un mutex est libéré automatiquement lorsque le thread qui le possède prend fin.  
  
-   Utilisez plusieurs threads pour des tâches qui nécessitent des ressources différentes, et évitez d'assigner plusieurs threads à une seule ressource.  Par exemple, toutes les tâches d'E\/S ont intérêt à posséder leur propre thread, car ce thread bloquera lors des opérations d'E\/S empêchant ainsi l'exécution d'autres threads.  Les entrées d'utilisateur sont une autre ressource qui tire profit d'un thread dédié.  Sur un ordinateur à un seul processeur, une tâche qui implique des calculs intensifs cohabite avec les entrées d'utilisateur et avec des tâches d'E\/S, mais les tâches consommant beaucoup de calcul entrent en concurrence.  
  
-   Envisagez l'utilisation des méthodes de la classe <xref:System.Threading.Interlocked> pour les modifications d'état simples, plutôt que l'instruction `lock` \(`SyncLock` en Visual Basic\).  L'instruction `lock` est un bon outil à usage général, mais la classe <xref:System.Threading.Interlocked> fournit de meilleures performances pour les mises à jour qui doivent être atomiques.  En interne, il exécute un préfixe de verrouillage seul s'il n'y a aucun conflit.  Lors de la révision du code, recherchez le code correspondant à celui illustré dans les exemples suivants.  Dans le premier exemple, une variable d'état est incrémentée :  
  
    ```vb  
    SyncLock lockObject  
        myField += 1  
    End SyncLock  
    ```  
  
    ```csharp  
    lock(lockObject)   
    {  
        myField++;  
    }  
    ```  
  
     Vous pouvez améliorer les performances à l'aide de la méthode <xref:System.Threading.Interlocked.Increment%2A> au lieu de l'instruction `lock`, comme suit :  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    >  Dans le .NET Framework version 2.0, la méthode <xref:System.Threading.Interlocked.Add%2A> fournit des mises à jour atomiques dans les incréments supérieurs à 1.  
  
     Dans le deuxième exemple, une variable de type référence est mise à jour uniquement s'il s'agit d'une référence null \(`Nothing` en Visual Basic\).  
  
    ```vb  
    If x Is Nothing Then  
        SyncLock lockObject  
            If x Is Nothing Then  
                x = y  
            End If  
        End SyncLock  
    End If  
    ```  
  
    ```csharp  
    if (x == null)  
    {  
        lock (lockObject)  
        {  
            if (x == null)  
            {  
                x = y;  
            }  
        }  
    }  
    ```  
  
     Les performances peuvent être améliorées en utilisant à la place la méthode <xref:System.Threading.Interlocked.CompareExchange%2A>, comme suit :  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    >  Dans le .NET Framework version 2.0, la méthode <xref:System.Threading.Interlocked.CompareExchange%2A> a une surcharge générique qui peut être utilisée pour le remplacement de type sécurisé de tout type référence.  
  
## Recommandations pour les bibliothèques de classes  
 Tenez compte des indications suivantes lors de la conception de bibliothèques de classes pour le multithreading :  
  
-   Évitez le besoin de synchronisation, si possible.  C'est particulièrement vrai dans le cas de code très utilisé.  Par exemple, un algorithme peut être ajusté pour tolérer une condition de concurrence critique plutôt que de l'éliminer.  Une synchronisation inutile diminue les performances et entraîne des possibilités d'interblocage et de conditions de concurrence critique.  
  
-   Rendez les données statiques \(`Shared` en Visual Basic\) thread\-safe par défaut.  
  
-   Ne rendez pas les données d'instance thread\-safe par défaut.  L'ajout de verrous pour créer du code thread\-safe diminue les performances, augmente les conflits de verrouillage et entraîne des possibilités d'interblocages.  Dans les modèles d'application courants, un seul thread à la fois exécute le code utilisateur, ce qui réduit le besoin de sécurité des threads.  Pour cette raison, les bibliothèques de classes .NET Framework ne sont pas thread\-safe par défaut.  
  
-   Évitez de fournir des méthodes statiques qui modifient l'état statique.  Dans les scénarios de serveur courants, l'état statique est partagé par plusieurs demandes, ce qui signifie que plusieurs threads peuvent exécuter ce code en même temps.  Cela entraîne la possibilité de bogues liés aux threads.  Envisagez d'utiliser un modèle de design qui encapsule des données dans des instances qui ne sont pas partagées par plusieurs demandes.  En outre, si les données statiques sont synchronisées, les appels entre les méthodes statiques qui altèrent l'état peuvent entraîner des interblocages ou une synchronisation redondante, ce qui a une incidence néfaste sur les performances.  
  
## Voir aussi  
 [Threading](../../../docs/standard/threading/index.md)   
 [Threads and Threading](../../../docs/standard/threading/threads-and-threading.md)