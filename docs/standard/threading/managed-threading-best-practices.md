---
title: "Meilleures pratiques pour le threading managé"
ms.custom: 
ms.date: 11/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threading [.NET Framework], design guidelines
- threading [.NET Framework], best practices
- managed threading
ms.assetid: e51988e7-7f4b-4646-a06d-1416cee8d557
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e396bb1f6a710e49e311ca1526a7aae9bca7bf90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="managed-threading-best-practices"></a>Meilleures pratiques pour le threading managé
Le multithreading nécessite une programmation attentive. Pour réduire la complexité de la plupart des tâches, il vous suffit de mettre en file d’attente les requêtes à exécuter par les threads d’un pool de threads. Cet article vous permet de remédier aux situations plus complexes, telles que la coordination du travail de plusieurs threads ou la gestion des threads bloqués.  
  
> [!NOTE]
> À compter de .NET Framework 4, la bibliothèque parallèle de tâches et PLINQ fournissent des API qui réduire la complexité et les risques de la programmation multithread. Pour plus d’informations, consultez [programmation parallèle dans .NET](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="deadlocks-and-race-conditions"></a>Interblocages et conditions de concurrence  
 Le multithreading résout les problèmes de débit et de réactivité, mais, ce faisant, occasionne de nouveaux problèmes : les interblocages et les conditions de concurrence.  
  
### <a name="deadlocks"></a>Interblocages (deadlocks)  
 Un interblocage se produit lorsque chacun des deux threads tente de verrouiller une ressource déjà verrouillée par l’autre thread. Aucun des deux threads ne peut donc poursuivre l’exécution.  
  
 De nombreuses méthodes des classes de threading managé fournissent des délais d’expiration conçus pour faciliter la détection des interblocages. Par exemple, le code suivant tente d’acquérir un verrou sur un objet nommé `lockObject`. Si le verrou n’est pas obtenu en 300 millisecondes, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> retourne `false`.  
  
```vb  
If Monitor.TryEnter(lockObject, 300) Then  
    Try  
        ' Place code protected by the Monitor here.  
    Finally  
        Monitor.Exit(lockObject)  
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
        Monitor.Exit(lockObject);  
    }  
}  
else {  
    // Code to execute if the attempt times out.  
}  
```  
  
### <a name="race-conditions"></a>Conditions de concurrence  
 Une condition de concurrence est un bogue qui survient lorsque le résultat d’un programme dépend du thread qui atteint le premier un bloc de code spécifique. L’exécution du programme à plusieurs reprises produit des résultats différents, et le résultat d’une exécution donnée n’est donc pas prévisible.  
  
 Un exemple simple de condition de concurrence correspond à l’incrémentation d’un champ. Supposons qu’une classe comporte un champ **static** privé (**Shared** en Visual Basic) qui est incrémenté chaque fois qu’une instance de la classe est créée, à l’aide d’un code tel que `objCt++;` (C#) ou `objCt += 1` (Visual Basic). Cette opération nécessite le chargement de la valeur de `objCt` dans un registre, l’incrémentation de la valeur, puis son stockage dans `objCt`.  
  
 Dans une application multithread, il est possible qu’un thread ayant chargé et incrémenté la valeur soit devancé par un autre thread qui exécute ces trois étapes ; lorsque le premier thread reprend l’exécution et stocke sa valeur, il remplace alors la valeur de `objCt` sans tenir compte du fait qu’elle a changé dans l’intervalle.  
  
 Cette condition de concurrence critique est facile à éviter en utilisant des méthodes de la <xref:System.Threading.Interlocked> class, telle que <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>. Pour découvrir d’autres techniques de synchronisation des données entre plusieurs threads, consultez l’article [Synchronisation des données pour le multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).  
  
 Des conditions de concurrence peuvent également survenir lorsque vous synchronisez les activités de plusieurs threads. Chaque fois que vous écrivez une ligne de code, vous devez prendre en compte ce qui peut se produire si un thread est devancé par un autre thread avant d’avoir exécuté la ligne (ou avant toute instruction machine individuelle composant la ligne).  
  
## <a name="number-of-processors"></a>Nombre de processeurs  
 La plupart des ordinateurs sont désormais équipés de plusieurs processeurs (également appelés cœurs), y compris les petits appareils, tels que les tablettes et les téléphones. Si vous développez des logiciels également destinés à s’exécuter sur des ordinateurs monoprocesseur, vous devez savoir que le multithreading résout différents problèmes pour les ordinateurs monoprocesseur et multiprocesseur.  
  
### <a name="multiprocessor-computers"></a>Ordinateurs multiprocesseur  
 Le multithreading offre un débit plus élevé. Dix processeurs peuvent effectuer dix fois le travail d’un seul processeur, mais uniquement si ce travail est divisé afin que les dix processeurs puissent le traiter simultanément. Les threads offrent un moyen simple de diviser le travail et d’exploiter la puissance de traitement supplémentaire. Si vous utilisez le multithreading sur un ordinateur multiprocesseur :  
  
-   Le nombre de threads pouvant s’exécuter simultanément est limité par le nombre de processeurs.  
  
-   Un thread d’arrière-plan s’exécute uniquement lorsque le nombre de threads de premier plan qui s’exécutent est inférieur au nombre de processeurs.  
  
-   Lorsque vous appelez le <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> méthode sur un thread, ce thread peut ou peut ne pas démarrer l’exécuter immédiatement, selon le nombre de processeurs et le nombre de threads actuellement en attente d’exécution.  
  
-   Des conditions de concurrence peuvent survenir, non seulement lorsque des threads sont devancés de manière inattendue, mais également parce que deux threads qui s’exécutent sur différents processeurs risquent d’entrer en concurrence pour atteindre le même bloc de code.  
  
### <a name="single-processor-computers"></a>Ordinateurs monoprocesseur  
 Le multithreading offre une meilleure réactivité à l’utilisateur de l’ordinateur et utilise la durée d’inactivité pour les tâches en arrière-plan. Si vous utilisez le multithreading sur un ordinateur monoprocesseur :  
  
-   Un seul thread s’exécute à tout moment.  
  
-   Un thread d’arrière-plan s’exécute uniquement lorsque le thread utilisateur principal est inactif. Un thread de premier plan qui s’exécute constamment prive les threads d’arrière-plan de temps processeur.  
  
-   Lorsque vous appelez le <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> méthode sur un thread, ce thread ne pas s’exécute jusqu'à ce que le thread en cours génère ou est devancé par le système d’exploitation.  
  
-   Les conditions de concurrence surviennent généralement parce que le programmeur n’a pas anticipé le fait qu’un thread puisse être devancé à un moment inopportun, ce qui permet parfois à un autre thread d’atteindre un bloc de code le premier.  
  
## <a name="static-members-and-static-constructors"></a>Membres static et constructeurs static  
 Une classe n’est pas initialisée tant que son constructeur de classe (constructeur `static` en C#, `Shared Sub New` en Visual Basic) n’a pas fini de s’exécuter. Pour empêcher l’exécution de code sur un type qui n’est pas initialisé, le common language runtime bloque tous les appels d’autres threads aux membres `static` de la classe (membres `Shared` en Visual Basic) jusqu’à la fin de l’exécution du constructeur de classe.  
  
 Par exemple, si un constructeur de classe démarre un nouveau thread, et que la procédure de thread appelle un membre `static` de la classe, le nouveau thread se bloque jusqu’à la fin du constructeur de classe.  
  
 Cela s’applique à n’importe quel type pouvant comporter un constructeur `static`.  
  
## <a name="general-recommendations"></a>Recommandations générales  
 Lorsque vous utilisez plusieurs threads, tenez compte des recommandations suivantes :  
  
-   N’utilisez pas <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> pour mettre fin à d’autres threads. L’appel de la méthode **Abort** sur un autre thread équivaut à lever une exception sur ce dernier sans connaître le stade précis du traitement atteint par ce thread.  
  
-   N’utilisez pas <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> et <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> pour synchroniser les activités de plusieurs threads. Utilisez <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, et <xref:System.Threading.Monitor>.  
  
-   Ne contrôlez pas l’exécution des threads de travail à partir de votre programme principal (à l’aide d’événements, par exemple). Concevez plutôt votre programme pour que les threads de travail soient chargés d’attendre que le travail devienne disponible, d’exécuter ce travail, puis d’en informer les autres parties de votre programme lorsqu’ils ont terminé. Si vos threads de travail ne se bloquent pas, envisagez d’utiliser les threads d’un pool de threads. <xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType>est utile dans les situations où les threads de travail se bloquent.  
  
-   N’utilisez pas de types en tant qu’objets de verrou. Autrement dit, évitez comme code `lock(typeof(X))` en c# ou `SyncLock(GetType(X))` en Visual Basic, ou l’utilisation de <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> avec <xref:System.Type> objets. Pour un type donné, il existe une seule instance de <xref:System.Type?displayProperty=nameWithType> par domaine d’application. Si le type sur lequel vous utilisez un verrou est public, un code différent du vôtre peut utiliser des verrous sur ce type, entraînant ainsi des interblocages. Pour découvrir les autres problèmes, consultez l’article [Meilleures pratiques pour la fiabilité](../../../docs/framework/performance/reliability-best-practices.md).  
  
-   Procédez avec précaution lorsque vous utilisez des verrous sur des instances, par exemple `lock(this)` en C# ou `SyncLock(Me)` en Visual Basic. Si un autre code de votre application, externe au type, utilise un verrou sur l’objet, des interblocages risquent de se produire.  
  
-   Assurez-vous qu’un thread entré dans un moniteur quitte toujours ce dernier, même si une exception se produit pendant que le thread se trouve dans le moniteur. C# [verrou](~/docs/csharp/language-reference/keywords/lock-statement.md) instruction et Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) instruction fournissent ce comportement d’automatiquement, en utilisant un **enfin** bloc pour garantir que <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> est appelé. Si vous n’êtes pas en mesure de garantir l’appel de la méthode **Exit**, vous pouvez modifier votre conception de façon à utiliser **Mutex**. Un mutex est automatiquement libéré lorsque le thread auquel il appartient a terminé.  
  
-   Utilisez plusieurs threads pour les tâches qui nécessitent des ressources différentes, et évitez d’attribuer plusieurs threads à une même ressource. Par exemple, vous tirerez avantage du fait que les tâches impliquant des E/S disposent de leur propre thread, car ce thread se bloquera lors des opérations d’E/S et permettra ainsi à d’autres threads de s’exécuter. L’entrée utilisateur est une autre ressource tirant profit d’un thread dédié. Sur un ordinateur monoprocesseur, une tâche qui exige de multiples calculs coexiste avec l’entrée utilisateur et avec les tâches qui impliquent des E/S, mais plusieurs tâches nécessitant de nombreux calculs entrent en concurrence les unes avec les autres.  
  
-   Envisagez d’utiliser les méthodes de la <xref:System.Threading.Interlocked> classe pour les modifications d’état simple, au lieu d’utiliser le `lock` instruction (`SyncLock` en Visual Basic). Le `lock` instruction est un bon outil à usage général, mais la <xref:System.Threading.Interlocked> classe fournit de meilleures performances pour les mises à jour qui doivent être atomiques. En interne, elle exécute un seul préfixe de verrou s’il n’existe aucun conflit. Lors des phases de révision du code, examinez le code semblable à celui des exemples ci-dessous. Dans le premier exemple, une variable d’état est incrémentée :  
  
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
  
     Vous pouvez améliorer les performances à l’aide de la <xref:System.Threading.Interlocked.Increment%2A> méthode à la place de la `lock` instruction, comme suit :  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    >  Dans le .NET Framework version 2.0, le <xref:System.Threading.Interlocked.Add%2A> méthode fournit des mises à jour atomiques dans les incréments supérieurs à 1.  
  
     Dans le second exemple, une variable de type référence est uniquement mise à jour s’il s’agit d’une référence null (`Nothing` en Visual Basic).  
  
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
  
     Performances peuvent être améliorées en utilisant la <xref:System.Threading.Interlocked.CompareExchange%2A> méthode à la place, comme suit :  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    >  Dans le .NET Framework version 2.0, le <xref:System.Threading.Interlocked.CompareExchange%2A> méthode a une surcharge générique qui peut être utilisée pour le remplacement de type sécurisé de tout type référence.  
  
## <a name="recommendations-for-class-libraries"></a>Recommandations relatives aux bibliothèques de classes  
 Lorsque vous concevez des bibliothèques de classes pour le multithreading, tenez compte des recommandations suivantes :  
  
-   Dans la mesure du possible, évitez toute nécessité de synchronisation. Cette consigne s’applique tout particulièrement pour le code très sollicité. Par exemple, un algorithme peut être ajusté de façon à tolérer une condition de concurrence plutôt que de l’éliminer. Une synchronisation inutile dégrade les performances et entraîne un risque d’interblocages et de conditions de concurrence.  
  
-   Définissez les données static (`Shared` en Visual Basic) comme thread-safe par défaut.  
  
-   Ne définissez pas les données d’instance comme thread-safe par défaut. L’ajout de verrous pour créer un code thread-safe diminue les performances, multiplie les conflits de verrou et occasionne un risque d’interblocages. Dans les modèles d’application communs, le code utilisateur n’est exécuté que par un seul thread à la fois, ce qui minimise la nécessité d’une cohérence de thread. C’est la raison pour laquelle les bibliothèques de classes .NET Framework ne sont pas thread-safe par défaut.  
  
-   Évitez de fournir des méthodes statiques qui modifient l’état statique. Dans les scénarios de serveur courants, l’état statique est partagé entre les requêtes, ce qui signifie que plusieurs threads peuvent exécuter ce code en même temps. Ceci occasionne un risque de bogues de threading. Envisagez d’utiliser un modèle de conception qui encapsule les données dans des instances non partagées entre les requêtes. En outre, si les données static sont synchronisées, les appels entre les méthodes statiques qui modifient l’état peuvent entraîner des interblocages ou une synchronisation redondante et dégrader ainsi les performances.  
  
## <a name="see-also"></a>Voir aussi  
 [Thread](../../../docs/standard/threading/index.md)  
 [Threads et threading](../../../docs/standard/threading/threads-and-threading.md)
