---
title: "Exceptions in Managed Threads | Microsoft Docs"
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
  - "unhandled exceptions,in managed threads"
  - "threading [.NET Framework],unhandled exceptions"
  - "threading [.NET Framework],exceptions in managed threads"
  - "managed threading"
ms.assetid: 11294769-2e89-43cb-890e-ad4ad79cfbee
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# Exceptions in Managed Threads
Depuis la version 2.0 du .NET Framework, le langage d'exécution commun permet à la plupart des exceptions non gérées dans les threads de se poursuivre normalement.  Dans la plupart des cas, cela signifie que l'exception non gérée provoque l'arrêt de l'application.  
  
> [!NOTE]
>  C'est là un changement majeur par rapport aux versions 1.0 et 1.1 du .NET Framework, qui fournissent une « barrière » pour de nombreuses exceptions non gérées, par exemple les exceptions non gérées dans les threads du pool de threads.  Consultez [Modification par rapport aux versions précédentes](#ChangeFromPreviousVersions), plus loin dans cette rubrique.  
  
 Le Common Language Runtime propose une « barrière » pour certaines exceptions non gérées utilisées pour contrôler le déroulement d'un programme :  
  
-   Un <xref:System.Threading.ThreadAbortException> est levé dans un thread en raison d'un appel à <xref:System.Threading.Thread.Abort%2A>.  
  
-   Un <xref:System.AppDomainUnloadedException> est levé dans un thread car le domaine d'application dans lequel le thread s'exécute est en cours de déchargement.  
  
-   Le Common Language Runtime ou un processus hôte met fin au thread en levant une exception interne.  
  
 Si l'une de ces exceptions n'est pas gérée dans les threads créés par le Common Language Runtime, l'exception arrête le thread, mais le Common Language Runtime ne permet pas à l'exception de poursuivre.  
  
 Si ces exceptions ne sont pas gérées dans le thread principal ou dans les threads entrés dans le runtime à partir de code non managé, elles se poursuivent normalement, ce qui se traduit par l'arrêt de l'application.  
  
> [!NOTE]
>  Il est possible que le runtime lève une exception non gérée avant que du code managé ait eu la possibilité d'installer un gestionnaire d'exceptions.  Même si le code managé n'a pas eu la possibilité de gérer l'exception, cette dernière est autorisée à se poursuivre normalement.  
  
## Exposition des problèmes de threads au cours du développement  
 Lorsque les threads sont autorisés à échouer en silence, sans arrêter l'application, il se peut que des problèmes de programmation sérieux ne soient pas détectés.  C'est problématique pour les services et autres applications qui s'exécutent pendant de longues périodes.  Les échecs successifs de threads peuvent progressivement endommager l'état du programme.  Les performances de l'application peuvent diminuer ou l'application peut se bloquer.  
  
 Autoriser des exceptions non gérées dans les threads à continuer normalement, jusqu'à ce que le système d'exploitation arrête le programme expose des problèmes de ce type pendant le développement et les tests.  Les rapports d'erreurs sur les arrêts de programme prennent en charge le débogage.  
  
<a name="ChangeFromPreviousVersions"></a>   
## Modification par rapport aux versions précédentes  
 La modification majeure concerne les threads managés.  Dans les versions 1.0 et 1.1 du .NET Framework, le Common Language Runtime fournit une « barrière » pour les exceptions non gérées dans les situations suivantes :  
  
-   Il n'y a pas, à proprement parler, d'exception non gérée sur un thread de pool de thread.  Lorsqu'une tâche lève une exception qu'elle ne gère pas, le runtime imprime la trace de la pile d'exception dans la console, puis retourne le thread dans le pool de threads.  
  
-   Il n'y a pas, à proprement parler, d'exception non gérée sur un thread créé avec la méthode <xref:System.Threading.Thread.Start%2A> de la classe <xref:System.Threading.Thread>.  Lorsque le code exécuté sur un tel thread lève une exception qu'il ne gère pas, le runtime imprime la trace de la pile d'exception dans la console, puis met fin au thread correctement.  
  
-   Il n'y a pas, à proprement parler, d'exception non gérée sur le thread finaliseur.  Lorsqu'un finaliseur lève une exception qu'il ne gère pas, le runtime imprime la trace de la pile d'exception dans la console, puis autorise le thread finaliseur à reprendre l'exécution des finaliseurs.  
  
 L'état de premier plan ou d'arrière\-plan d'un thread managé n'affecte pas ce comportement.  
  
 Pour les exceptions non gérées sur les threads provenant de code non managé, la différence est plus subtile.  La boîte de dialogue JIT du runtime est prioritaire sur la boîte de dialogue du système d'exploitation pour les exceptions managées ou les exceptions natives sur les threads passés par l'intermédiaire de code natif.  Le processus s'arrête dans tous les cas.  
  
### Migration du code  
 En général, la modification permet d'exposer des problèmes de programmation qui n'ont pas été précédemment identifiés afin qu'ils puissent être résolus.  Dans certains cas, toutefois, les programmeurs ont pu tirer parti de la « barrière » du runtime, par exemple pour arrêter des threads.  Selon les cas, ils doivent envisager l'une des stratégies de migration suivantes :  
  
-   Restructurer le code afin que le thread s'arrête correctement lors de la réception d'un signal.  
  
-   Utiliser la méthode <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName> pour abandonner le thread.  
  
-   Si un thread doit être arrêté afin que l'arrêt du processus puisse s'effectuer, faites du thread un thread d'arrière\-plan afin qu'il soit arrêté automatiquement au moment de la sortie du processus.  
  
 Dans tous les cas, la stratégie doit respecter les règles de conception des exceptions.  Consultez [Instructions de conception pour les Exceptions](../../../docs/standard/design-guidelines/exceptions.md).  
  
### Indicateur de compatibilité des applications  
 Comme mesure de compatibilité temporaire, les administrateurs peuvent placer un indicateur de compatibilité dans la section `<runtime>` du fichier de configuration de l'application.  Le Common Language Runtime rétablit alors le comportement des versions 1.0 et 1.1.  
  
```  
<legacyUnhandledExceptionPolicy enabled="1"/>  
```  
  
## Substitution de l'hôte  
 Dans le .NET Framework version 2.0, un hôte non managé peut utiliser l'interface [ICLRPolicyManager](../../../ocs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) dans l'API d'hébergement pour substituer la stratégie d'exceptions non gérées par défaut du Common Language Runtime.  La fonction [ICLRPolicyManager::SetUnhandledExceptionPolicy](../Topic/ICLRPolicyManager::SetUnhandledExceptionPolicy%20Method.md) est utilisée pour définir la stratégie des exceptions non gérées.  
  
## Voir aussi  
 [Managed Threading Basics](../../../docs/standard/threading/managed-threading-basics.md)