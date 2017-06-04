---
title: "Constrained Execution Regions | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "constrained execution regions"
  - "CERs"
ms.assetid: 99354547-39c1-4b0b-8553-938e8f8d1808
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 9
---
# Constrained Execution Regions
Une région d'exécution limitée fait partie d'un mécanisme visant à créer du code managé fiable.  Elle définit une zone dans laquelle le Common Language Runtime \(CLR\) est limité dans la levée d'exceptions hors plage qui empêcheraient le code dans la zone de s'exécuter dans son intégralité.  Dans cette région, le code utilisateur est limité dans l'exécution de code qui entraînerait la levée d'exceptions hors plage.  La méthode <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> doit précéder immédiatement un bloc `try` et marquer les blocs `catch`, `finally` et `fault` comme des régions d'exécution limitée.  Une fois marqué comme une région d'exécution limitée, le code doit appeler uniquement un autre code possédant des contrats de fiabilité élevée et il ne doit pas allouer ou effectuer des appels virtuels à des méthodes non préparées ou peu fiables, sauf si le code est préparé à gérer des échecs.  Le Common Language Runtime \(CLR\) retarde les abandons de thread pour le code qui s'exécute dans une région d'exécution limitée.  
  
 Les régions d'exécution limitée sont utilisées dans le CLR sous différentes formes en plus d'un bloc `try` annoté, en particulier dans les finaliseurs critiques qui s'exécutent dans les classes dérivées de la classe <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject> et dans du code exécuté à l'aide de la méthode <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A>.  
  
## Préparation préliminaire de la région d'exécution limitée  
 Le Common Language Runtime \(CLR\) prépare les régions d'exécution limitée à l'avance pour éviter des conditions de mémoire insuffisante.  La préparation préliminaire est nécessaire afin que le Common Language Runtime ne provoque pas de condition de mémoire insuffisante pendant la compilation juste\-à\-temps ou le chargement de types.  
  
 Le développeur est tenu d'indiquer qu'une région de code est une région d'exécution limitée :  
  
-   La région d'exécution limitée de niveau supérieur et les méthodes dans le graphique des appels complet possédant l'attribut <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> sont préparées à l'avance.  <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> peut déclarer uniquement des garanties de <xref:System.Runtime.ConstrainedExecution.Cer> ou <xref:System.Runtime.ConstrainedExecution.Cer>.  
  
-   Il n'est pas possible d'effectuer une préparation préliminaire pour les appels qui ne peuvent pas être déterminés de façon statique, tels que la distribution \(dispatch\) virtuelle.  Utilisez, dans ce cas, la méthode <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>.  Lors de l'utilisation de la méthode <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A>, l'attribut <xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute> doit être appliqué au code de nettoyage.  
  
## Contraintes  
 Les utilisateurs sont limités dans le type de code qu'ils peuvent écrire dans une région d'exécution limitée.  Le code ne peut pas provoquer d'exception hors plage, comme c'est parfois le cas lors des opérations suivantes :  
  
-   Allocation explicite  
  
-   Boxing  
  
-   Acquisition d'un verrou  
  
-   Appel virtuel de méthodes non préparées  
  
-   Appel à des méthodes présentant un contrat de fiabilité faible ou inexistant  
  
 Dans le .NET Framework version 2.0, ces contraintes sont des indications.  Les diagnostics sont fournis par l'intermédiaire d'outils d'analyse de code.  
  
## Contrats de fiabilité  
 <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> est un attribut personnalisé qui documente les garanties de fiabilité et l'état d'altération d'une méthode donnée.  
  
### Garanties de fiabilité  
 Les garanties de fiabilité, représentées par les valeurs de l'énumération <xref:System.Runtime.ConstrainedExecution.Cer>, indiquent le degré de fiabilité d'une méthode donnée :  
  
-   <xref:System.Runtime.ConstrainedExecution.Cer>.  En présence de conditions exceptionnelles, la méthode peut échouer.  Dans ce cas, elle indique à la méthode appelante si elle a réussi ou échoué.  La méthode doit être contenue dans une région d'exécution limitée pour garantir qu'elle peut signaler la valeur de retour.  
  
-   <xref:System.Runtime.ConstrainedExecution.Cer>.  La méthode, le type ou l'assembly sont dépourvus du concept de région d'exécution limitée et il est peu sûr de les appeler dans une région d'exécution limitée sans limitation substantielle des risques d'altération d'état.  Ils ne tirent pas parti des garanties qu'offrent une région d'exécution limitée.  Cela implique ce qui suit :  
  
    1.  En présence de conditions exceptionnelles, la méthode peut échouer.  
  
    2.  La méthode peut signaler ou non qu'elle a échoué.  
  
    3.  La méthode n'est pas écrite pour utiliser une région d'exécution limitée, ce qui constitue le scénario le plus probable.  
  
    4.  Si une méthode, un type ou un assembly n'est pas marqué de manière explicite pour réussir, il est implicitement identifié comme <xref:System.Runtime.ConstrainedExecution.Cer>.  
  
-   <xref:System.Runtime.ConstrainedExecution.Cer>.  En présence de conditions exceptionnelles, la réussite de la méthode est garantie.  Pour atteindre ce niveau de fiabilité, vous devez toujours construire une région d'exécution limitée autour de la méthode qui est appelée, même lorsqu'elle est appelée dans une région qui n'est pas une région d'exécution limitée.  Une méthode réussit si elle accomplit ce qui est prévu, bien que la réussite reste une notion subjective.  Par exemple, si vous marquez Count avec `ReliabilityContractAttribute(Cer.Success)`, cela implique que lorsqu'elle est exécutée dans une région d'exécution limitée, elle retourne toujours le nombre d'éléments contenus dans <xref:System.Collections.ArrayList> et ne peut jamais laisser les champs internes dans un état indéterminé.  Toutefois, la méthode <xref:System.Threading.Interlocked.CompareExchange%2A> est également marquée comme réussie, étant entendu que la réussite peut signifier l'impossibilité de remplacer la valeur par une nouvelle valeur en raison d'une condition de concurrence critique.  L'essentiel est que la méthode se comporte de la façon prévue et documentée et le code d'une région d'exécution limitée ne doit pas être écrit pour attendre un comportement inhabituel autre que celui d'un code correct mais peu fiable.  
  
### Niveaux d'altération  
 Les niveaux d'altération, représentés par les valeurs de l'énumération <xref:System.Runtime.ConstrainedExecution.Consistency>, indiquent l'étendue de l'état d'altération dans un environnement donné :  
  
-   <xref:System.Runtime.ConstrainedExecution.Consistency>.  Face à des conditions exceptionnelles, le CLR \(Common Language Runtime\) n'offre aucune garantie quant à la cohérence de l'état dans le domaine d'application actuel.  
  
-   <xref:System.Runtime.ConstrainedExecution.Consistency>.  Face à des conditions exceptionnelles, il est garanti que la méthode limitera l'altération de l'état à l'instance actuelle.  
  
-   <xref:System.Runtime.ConstrainedExecution.Consistency>. Face à des conditions exceptionnelles, le CLR n'offre aucune garantie quant à la cohérence de l'état ; cela signifie que ces conditions peuvent altérer le processus.  
  
-   <xref:System.Runtime.ConstrainedExecution.Consistency>.  En présence de conditions exceptionnelles, il est garanti que la méthode n'altérera pas l'état.  
  
## Bloc try\/catch\/finally de fiabilité  
 `try/catch/finally` est un mécanisme de gestion des exceptions avec le même niveau de garanties de prévisibilité que la version non managée.  Le bloc `catch/finally` est la région d'exécution limitée.  Les méthodes figurant dans le bloc exigent une préparation préliminaire et ne doivent pas être interruptibles.  
  
 Dans le .NET Framework version 2.0, le code informe le runtime qu'une tentative est fiable en appelant <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> qui précède immédiatement un bloc try.  <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> est membre de <xref:System.Runtime.CompilerServices.RuntimeHelpers>, une classe de prise en charge de compilateur.  Appelez <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> dès qu'elle est disponible via les compilateurs.  
  
## Régions non interruptibles  
 Une région non interruptible regroupe un jeu d'instructions dans une région d'exécution limitée.  
  
 Dans le .NET Framework version 2.0, dans l'attente d'une disponibilité via la prise en charge de compilateur, le code utilisateur crée des régions non interruptibles avec un bloc try\/catch\/finally fiable qui contient un bloc try\/catch vide précédé d'un appel de la méthode <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>.  
  
## Objet finaliseur critique  
 Un objet <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject> garantit que le garbage collection exécutera le finaliseur.  Dès son allocation, le finaliseur et son graphique des appels sont préparés à l'avance.  La méthode du finaliseur s'exécute dans une région d'exécution limitée et doit respecter toutes les contraintes sur les régions d'exécution limitée et les finaliseurs.  
  
 Tout type héritant de <xref:System.Runtime.InteropServices.SafeHandle> et de <xref:System.Runtime.InteropServices.CriticalHandle> a la garantie que son finaliseur s'exécute dans une région d'exécution limitée.  Implémentez <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> dans les classes dérivées de <xref:System.Runtime.InteropServices.SafeHandle> pour exécuter du code tenu de libérer le handle.  
  
## Code non autorisé dans les régions d'exécution limitée  
 Les opérations suivantes ne sont pas autorisées dans les régions d'exécution limitée :  
  
-   Allocations explicites  
  
-   Acquisition d'un verrou  
  
-   Boxing  
  
-   Accès de tableau multidimensionnel  
  
-   Appels de méthode par réflexion  
  
-   <xref:System.Threading.Monitor.Enter%2A> ou <xref:System.IO.FileStream.Lock%2A>.  
  
-   Vérifications de la sécurité.  N'exécutez pas de demandes, liez uniquement les demandes  
  
-   <xref:System.Reflection.Emit.OpCodes.Isinst> et <xref:System.Reflection.Emit.OpCodes.Castclass> pour les objets COM et les proxies  
  
-   Obtention ou définition de champs sur un proxy transparent  
  
-   Sérialisation.  
  
-   Délégués et pointeurs fonction  
  
## Voir aussi  
 [Reliability Best Practices](../../../docs/framework/performance/reliability-best-practices.md)