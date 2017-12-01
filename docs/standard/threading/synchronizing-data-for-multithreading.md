---
title: "Synchronisation des données pour le multithreading"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- synchronization, threads
- threading [.NET Framework], synchronizing threads
- managed threading
ms.assetid: b980eb4c-71d5-4860-864a-6dfe3692430a
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a17eba2f930fda06d643d78c73c117e89ae86928
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="synchronizing-data-for-multithreading"></a>Synchronisation des données pour le multithreading
Lorsque plusieurs threads peuvent appeler les propriétés et méthodes d’un objet unique, il est essentiel que ces appels soient synchronisés. Sinon, un thread peut interrompre l’action d’un autre thread, et l’objet peut être laissé dans un état non valide. Une classe dont les membres sont protégés de ces interruptions est appelée « thread-safe ».  
  
 L’infrastructure Common Language Infrastructure fournit plusieurs stratégies pour synchroniser l’accès aux membres statiques et d’instance :  
  
-   Régions de code synchronisées. Vous pouvez utiliser la <xref:System.Threading.Monitor> classe ou du compilateur de prise en charge de cette classe synchronise uniquement le bloc de code a besoin, améliorer les performances.  
  
-   Synchronisation manuelle. Vous pouvez utiliser les objets de synchronisation fournis par la bibliothèque de classes .NET Framework. Consultez [vue d’ensemble des Primitives de synchronisation](../../../docs/standard/threading/overview-of-synchronization-primitives.md), qui inclut une présentation de la <xref:System.Threading.Monitor> classe.  
  
-   Contextes synchronisés. Vous pouvez utiliser la <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> pour activer la synchronisation simple et automatique pour <xref:System.ContextBoundObject> objets.  
  
-   Classes de collection dans le <xref:System.Collections.Concurrent?displayProperty=nameWithType> espace de noms. Ces classes fournissent des opérations d’ajout et de suppression intégrées et synchronisées. Pour plus d’informations, consultez [Collections thread-safe](../../../docs/standard/collections/thread-safe/index.md).  
  
 Le common language runtime fournit un modèle de thread dans lequel les classes se répartissent en plusieurs catégories qui peuvent être synchronisées de différentes manières, selon les besoins. Le tableau suivant indique le type de prise en charge de la synchronisation fourni pour les champs et méthodes dans une catégorie de synchronisation donnée.  
  
|Catégorie|Champs globaux|Champs statiques|Méthodes statiques|Champs d’instance|Méthodes d’instance|Blocs de code spécifiques|  
|--------------|-------------------|-------------------|--------------------|---------------------|----------------------|--------------------------|  
|Aucune synchronisation|Non|Non|Non|Non|Non|Non|  
|Contexte synchronisé|Non|Non|Non|Oui|Oui|Non|  
|Régions de code synchronisées|Non|Non|Seulement en cas de marquage|Non|Seulement en cas de marquage|Seulement en cas de marquage|  
|Synchronisation manuelle|Manuel|Manuel|Manuel|Manuel|Manuel|Manuel|  
  
## <a name="no-synchronization"></a>Aucune synchronisation  
 Il s’agit de la valeur par défaut pour les objets. N’importe quel thread peut accéder à toute méthode ou champ et ce, à tout moment. Par contre, un seul thread à la fois doit accéder à ces objets.  
  
## <a name="manual-synchronization"></a>Synchronisation manuelle  
 La bibliothèque de classes .NET Framework fournit plusieurs classes pour la synchronisation des threads. Voir [Vue d’ensemble des primitives de synchronisation](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
## <a name="synchronized-code-regions"></a>Régions de code synchronisées  
 Vous pouvez utiliser la <xref:System.Threading.Monitor> classe ou un mot clé de compilateur pour synchroniser des blocs de code, des méthodes d’instance et des méthodes statiques. Les champs statiques synchronisés ne sont pas pris en charge.  
  
 Visual Basic et C# prennent en charge le marquage de blocs de code avec un mot-clé d’un langage spécifique, l’instruction `lock` en C# ou l’instruction `SyncLock` en Visual Basic. Lorsque le code est exécuté par un thread, une tentative d’acquisition du verrou est effectuée. Si le verrou a déjà été acquis par un autre thread, le thread se bloque jusqu’à ce qu’il devienne disponible. Lorsque le thread quitte le bloc de code synchronisé (d’une manière ou d’une autre), le verrou est libéré.  
  
> [!NOTE]
>  Le `lock` et `SyncLock` instructions sont implémentées à l’aide de <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> et <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType>, afin d’autres méthodes de <xref:System.Threading.Monitor> peut être utilisé conjointement avec celles-ci dans la région synchronisée.  
  
 Vous pouvez également décorer une méthode avec un élément **MethodImplAttribute** et un élément **MethodImplOptions.Synchronized**, ce qui a le même effet que l’utilisation de l’élément **Monitor** ou de l’un des mots-clés de compilateur pour verrouiller l’intégralité du corps de la méthode.  
  
 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>peut être utilisé pour libérer un thread des opérations de blocage telles que l’attente de l’accès à une région synchronisée du code. **Thread.Interrupt** est également utilisé pour libérer des threads d’opérations telles que <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
>  Ne verrouillez pas le type (`typeof(MyType)` en C#, `GetType(MyType)` en Visual Basic, ou `MyType::typeid` en C++) pour protéger les méthodes `static` (méthodes `Shared` dans Visual Basic). Utilisez plutôt un objet statique privé. De même, n’utilisez pas `this` en C# (`Me` en Visual Basic) pour verrouiller des méthodes d’instance. Utilisez plutôt un objet privé. Une classe ou une instance peut être verrouillée par un code autre que le vôtre, ce qui peut entraîner des blocages ou des problèmes de performances.  
  
### <a name="compiler-support"></a>Prise en charge du compilateur  
 Visual Basic et c# prennent en charge le mot clé de langage qui utilise <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> et <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> pour verrouiller l’objet. Visual Basic prend en charge l’instruction [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) et C#, l’instruction [lock](~/docs/csharp/language-reference/keywords/lock-statement.md).  
  
 Dans les deux cas, si une exception est déclenchée dans le bloc de code, le verrou acquis par l’instruction **lock** ou **SyncLock** est automatiquement libéré. Les compilateurs C# et Visual Basic émettent un bloc **try**/**finally** avec **Monitor.Enter** au début de la tentative, et **Monitor.Exit** dans le bloc **finally**. Si une exception est déclenchée dans le bloc **lock** ou **SyncLock**, le gestionnaire **finally** s’exécute pour vous permettre d’effectuer d’éventuelles tâches de nettoyage.  
  
## <a name="synchronized-context"></a>Contexte synchronisé  
 Vous pouvez utiliser l’élément **SynchronizationAttribute** sur n’importe quel élément **ContextBoundObject** pour synchroniser tous les champs et méthodes d’instance. Tous les objets d’un même domaine de contexte partagent le même verrou. Plusieurs threads sont autorisés à accéder aux méthodes et champs, mais un seul thread est autorisé à la fois.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute>  
 [Threads et threading](../../../docs/standard/threading/threads-and-threading.md)  
 [Vue d’ensemble des primitives de synchronisation](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 [SyncLock (instruction)](~/docs/visual-basic/language-reference/statements/synclock-statement.md)  
 [lock, instruction](~/docs/csharp/language-reference/keywords/lock-statement.md)
