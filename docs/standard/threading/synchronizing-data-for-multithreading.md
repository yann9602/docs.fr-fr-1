---
title: "Synchronizing Data for Multithreading | Microsoft Docs"
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
  - "synchronization, threads"
  - "threading [.NET Framework], synchronizing threads"
  - "managed threading"
ms.assetid: b980eb4c-71d5-4860-864a-6dfe3692430a
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 16
---
# Synchronizing Data for Multithreading
Lorsque plusieurs threads peuvent effectuer des appels aux propriétés et aux méthodes d'un objet unique, il est critique que ces appels soient synchronisés.  Sinon, un thread peut interrompre l'action d'un autre thread et l'objet peut se retrouver dans un état non valide.  Une classe dont les membres sont protégés de ces interruptions s'appelle thread\-safe.  
  
 L'infrastructure du langage commun \(CLI, Common Language Infrastructure\) fournit plusieurs stratégies pour synchroniser l'accès aux membres static et d'instance :  
  
-   Régions de code synchronisées.  Vous pouvez utiliser la classe <xref:System.Threading.Monitor> ou la prise en charge par le compilateur pour que cette classe synchronise uniquement le bloc de code nécessaire, ce qui améliore les performances.  
  
-   Synchronisation manuelle.  Vous pouvez utiliser les objets de synchronisation fournis par la bibliothèque de classes du .NET Framework.  Consultez [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md), qui inclut une présentation de la classe <xref:System.Threading.Monitor>.  
  
-   Contextes synchronisés.  Vous pouvez utiliser <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> pour activer une synchronisation simple et automatique des objets <xref:System.ContextBoundObject>.  
  
-   Classes de collections dans l'espace de noms <xref:System.Collections.Concurrent?displayProperty=fullName>.  Ces classes fournissent des opérations d'ajout et de suppression synchronisées intégrées.  Pour plus d'informations, consultez [Collections thread\-safe](../../../docs/standard/collections/thread-safe/index.md).  
  
 Le Common Language Runtime fournit un modèle de thread où les classes appartiennent à un nombre de catégories qui peuvent être synchronisées de diverses manières en fonction des exigences.  Le tableau suivant répertorie le type de prise en charge disponible en matière de synchronisation pour des champs et des méthodes pour une catégorie de synchronisation donnée.  
  
|Catégorie|Champs globaux|Champs statiques|Méthodes statiques|Champs d'instance|Méthodes d'instance|Blocs de code spécifique|  
|---------------|--------------------|----------------------|------------------------|-----------------------|-------------------------|------------------------------|  
|Pas de synchronisation|Non|Non|Non|Non|Non|Non|  
|Contexte synchronisé|Non|Non|Non|Oui|Oui|Non|  
|Régions de code synchronisées|Non|Non|Seulement si marqué|Non|Seulement si marqué|Seulement si marqué|  
|Synchronisation manuelle|Manual|Manual|Manual|Manual|Manual|Manual|  
  
## Pas de synchronisation  
 Il s'agit du paramètre par défaut pour les objets.  Tout thread peut accéder à n'importe quelle méthode ou champ à tout moment.  Un seul thread à la fois peut accéder à ces objets.  
  
## Synchronisation manuelle  
 La bibliothèque de classes du .NET Framework fournit plusieurs classes permettant de synchroniser des threads.  Consultez [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
## Régions de code synchronisées  
 Vous pouvez utiliser la classe <xref:System.Threading.Monitor> ou un mot clé du compilateur pour synchroniser des blocs de code, des méthodes d'instance et des méthodes statiques.  Il n'existe pas de prise en charge pour les champs statiques synchronisés.  
  
 Visual Basic et C\# prennent en charge le marquage de blocs de code à l'aide d'un mot clé de langage particulier, l'instruction `lock` en C\# ou l'instruction `SyncLock` dans Visual Basic.  Lorsque le code est exécuté par un thread, une tentative d'acquisition du verrou est effectuée.  Si le verrou a déjà été acquis par un autre thread, le thread se bloque jusqu'à ce que le verrou soit disponible.  Lorsque le thread quitte le bloc synchronisé de code, le verrou est libéré, quelle que soit la façon dont le thread quitte le bloc.  
  
> [!NOTE]
>  Les instructions `lock` et `SyncLock` sont implémentées via <xref:System.Threading.Monitor.Enter%2A?displayProperty=fullName> et <xref:System.Threading.Monitor.Exit%2A?displayProperty=fullName>, de sorte que d'autres méthodes de <xref:System.Threading.Monitor> peuvent être utilisées conjointement dans la région synchronisée.  
  
 Vous pouvez également décorer une méthode à l'aide de **MethodImplAttribute** et **MethodImplOptions.Synchronized**, ce qui revient à utiliser **Monitor** ou l'un des mots clés du compilateur pour verrouiller le corps entier de la méthode.  
  
 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=fullName> peut s'utiliser pour libérer un thread des opérations de blocage telles que le fait d'attendre l'accès à une région synchronisée du code.  **Thread.Interrupt** s'utilise également pour libérer des threads d'opérations telles que <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName>.  
  
> [!IMPORTANT]
>  Ne verrouillez pas le type, c'est\-à\-dire `typeof(MyType)` en C\#, `GetType(MyType)` dans Visual Basic ou `MyType::typeid` en C\+\+, afin de protéger les méthodes `static` \(méthodes `Shared` dans Visual Basic\).  Utilisez à la place un objet statique privé.  De la même façon, n'utilisez pas `this` en C\# \(`Me` en Visual Basic\) pour verrouiller des méthodes d'instance.  Utilisez à la place un objet privé.  Une classe ou une instance peut être verrouillée par du code autre que le vôtre, ce qui peut provoquer des interblocages ou des problèmes de performance.  
  
### Prise en charge par le compilateur  
 Visual Basic et C\# prennent en charge un mot clé de langage qui utilise <xref:System.Threading.Monitor.Enter%2A?displayProperty=fullName> et <xref:System.Threading.Monitor.Exit%2A?displayProperty=fullName> pour verrouiller l'objet.  Visual Basic prend en charge l'instruction [SyncLock](../../../ocs/visual-basic/language-reference/statements/synclock-statement.md) ; C\# prend en charge l'instruction [lock](../Topic/lock%20Statement%20\(C%23%20Reference\).md).  
  
 Dans les deux cas, si une exception est levée dans le bloc de code, le verrou acquis par **lock** ou **SyncLock** est libéré automatiquement.  Les compilateurs C\# et Visual Basic émettent un bloc **try**\/**finally** à l'aide de **Monitor.Enter** au début de la tentative, et **Monitor.Exit** dans le bloc **finally**.  Si une exception est levée à l'intérieur du bloc **lock** ou **SyncLock**, le gestionnaire **finally** s'exécute pour vous permettre d'effectuer tout travail de nettoyage.  
  
## Contexte synchronisé  
 Vous pouvez utiliser **SynchronizationAttribute** sur n'importe quel **ContextBoundObject** pour synchroniser tous les champs et méthodes d'instance.  Tous les objets dans le même domaine de contexte partagent le même verrou.  Plusieurs threads sont autorisés à accéder aux méthodes et aux champs, toutefois un seul thread à la fois est autorisé.  
  
## Voir aussi  
 <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute>   
 [Threads and Threading](../../../docs/standard/threading/threads-and-threading.md)   
 [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md)   
 [SyncLock Statement](../../../ocs/visual-basic/language-reference/statements/synclock-statement.md)   
 [lock, instruction](../Topic/lock%20Statement%20\(C%23%20Reference\).md)