---
title: "loaderLock MDA | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "deadlocks [.NET Framework]"
  - "LoaderLock MDA"
  - "MDAs (managed debugging assistants), loader locks"
  - "managed debugging assistants (MDAs), loader locks"
  - "operating system loader locks"
  - "loader locks"
  - "locks, threads"
ms.assetid: 8c10fa02-1b9c-4be5-ab03-451d943ac1ee
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# loaderLock MDA
L'Assistant Débogage managé \(MDA, Managed Debugging Assistant\) `loaderLock` détecte des tentatives d'exécution du code managé sur un thread qui détient le verrou du système d'exploitation Microsoft Windows.  Toute exécution de ce type est illégale car elle peut mener à des interblocages et à l'utilisation de DLL avant qu'elles aient été initialisées par le chargeur du système d'exploitation.  
  
## Symptômes  
 Lors de l'exécution de code à l'intérieur du verrou du chargeur du système d'exploitation, la cause d'échec la plus courante est l'interblocage des threads lors de leur tentative d'appel à d'autres fonctions Win32 qui ont également besoin du verrou du chargeur.  Les fonctions `LoadLibrary`, `GetProcAddress`, `FreeLibrary` et `GetModuleHandle` en sont quelques exemples.  Il est possible que l'application n'appelle pas directement ces fonctions ; le Common Language ‏Runtime \(CLR\) peut appeler ces fonctions à la suite d'un appel de niveau supérieur comme <xref:System.Reflection.Assembly.Load%2A> ou du premier appel à une méthode d'appel de code non managé.  
  
 Des interblocages peuvent également se produire si un thread attend le début ou la fin de l'exécution d'un autre thread.  Lorsqu'un thread démarre ou termine son exécution, il doit acquérir le verrou du chargeur du système d'exploitation pour remettre des événements aux DLL concernées.  
  
 Enfin, dans certains cas, des appels de DLL peuvent se produire avant que ces DLL aient été correctement initialisées par le chargeur du système d'exploitation.  À la différence des échecs dus à un interblocage, qui peuvent être diagnostiqués par l'examen des piles de tous les threads impliqués dans l'interblocage, il est très difficile de diagnostiquer l'utilisation de DLL non initialisées sans utiliser cet Assistant Débogage managé.  
  
## Cause  
 Des assemblys C\+\+ combinant du code managé\/non managé créés pour les versions 1.0 ou 1.1 du .NET Framework tentent généralement d'exécuter le code managé à l'intérieur du verrou du chargeur à moins que certaines mesures spéciales aient été prises, par exemple, une liaison à **\/NOENTRY**.  Pour une description détaillée de ces problèmes, consultez « Mixed DLL Loading Problem » dans MSDN Library.  
  
 Des assemblys C\+\+ combinant du code managé\/non managé et créés pour le .NET Framework version 2.0 sont moins vulnérables à ces problèmes et présentent des risques plus limités, au même titre que les applications qui utilisent des DLL non managées enfreignant les règles du système d'exploitation.  Par exemple, si le point d'entrée `DllMain` d'une DLL non managée appelle `CoCreateInstance` pour obtenir un objet managé qui a été exposé à COM, cela se traduit par une tentative d'exécution du code managé à l'intérieur du verrou du chargeur.  Pour plus d'informations sur les problèmes liés au verrou du chargeur dans .NET Framework version 2.0 ou ultérieure, consultez [Initialisation d'assemblys mixtes](../Topic/Initialization%20of%20Mixed%20Assemblies.md).  
  
## Résolution  
 Dans Visual C\+\+ .NET 2002 et Visual C\+\+ .NET 2003, les DLL compilées avec l'option du compilateur `/clr` pouvaient s'interbloquer de façon non déterministe lors du chargement ; ce problème a été appelé le problème de chargement de DLL mixtes ou de verrouillage du chargeur.  Dans Visual C\+\+ 2005 et les versions ultérieures, le non\-déterminisme a été pratiquement supprimé du processus de chargement de DLL mixtes.  Toutefois, il reste quelques scénarios dans lesquels le verrouillage du chargeur peut se produire \(de façon déterministe\).  Pour obtenir un compte détaillé des causes et résolutions concernant les problèmes de verrouillage de chargeur restants, consultez [Initialisation d'assemblys mixtes](../Topic/Initialization%20of%20Mixed%20Assemblies.md).  Si cette rubrique ne présente pas votre problème de verrouillage de chargeur, vous devez examiner la pile des threads pour déterminer la raison du verrouillage du chargeur et la marche à suivre pour corriger le problème.  Examinez la trace de la pile du thread qui a activé cet Assistant Débogage managé.  Le thread tente d'exécuter un appel illégal dans le code managé tout en maintenant le verrouillage du chargeur du système d'exploitation.  Vous verrez probablement le point d'entrée `DllMain` ou un point d'entrée équivalent d'une DLL sur la pile.  Les règles du système d'exploitation quant aux actions autorisées à l'intérieur d'un tel point d'entrée sont assez limitées.  Ces règles interdisent toute exécution managée.  
  
## Effet sur le runtime  
 En général, plusieurs threads à l'intérieur du processus donneront lieu à un interblocage.  Il est probable que l'un ces threads soit un thread chargé d'exécuter un garbage collection, par conséquent, cet interblocage peut avoir une incidence majeure sur tout le processus.  En outre, il empêchera toute opération supplémentaire exigeant le verrouillage du chargeur du système d'exploitation, comme le chargement et le déchargement des assemblys ou des DLL ainsi que le démarrage et l'arrêt des threads.  
  
 Dans certaines circonstances exceptionnelles, il est également possible que des violations d'accès ou des problèmes similaires soient déclenchés dans des DLL appelées avant d'avoir été initialisées.  
  
## Sortie  
 Cet Assistant Débogage managé signale une tentative d'exécution managée illégale.  Vous devez examiner la pile du thread pour déterminer la raison du verrouillage du chargeur et comment résoudre le problème.  
  
## Configuration  
  
```  
<mdaConfig>  
  <assistants>  
    <loaderLock/>  
  </assistants>  
</mdaConfig>  
```  
  
## Voir aussi  
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)