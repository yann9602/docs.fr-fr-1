---
title: "Event-based Asynchronous Pattern (EAP) | Microsoft Docs"
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
  - "asynchronous calls"
  - "asynchronous programming, design patterns"
  - "asynchronous programming"
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
caps.latest.revision: 20
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 20
---
# Event-based Asynchronous Pattern (EAP)
Il existe plusieurs façons d'exposer des fonctionnalités asynchrones à du code client.  Le modèle asynchrone basé sur les événements recommande une méthode pour obtenir des classes un comportement asynchrone.  
  
> [!NOTE]
>  Depuis le [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], la bibliothèque parallèle de tâches fournit un nouveau modèle de programmation asynchrone et parallèle.  Pour plus d'informations, consultez [Parallel Programming](../../../docs/standard/parallel-programming/index.md).  
  
## Dans cette section  
 [Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 Explique comment le modèle asynchrone basé sur les événements permet de profiter des avantages des applications multithread tout en masquant de nombreux problèmes complexes inhérents à la conception multithread.  
  
 [Implementing the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 Décrit la façon standardisée de placer dans un package une classe qui possède des fonctionnalités asynchrones.  
  
 [Meilleures pratiques pour implémenter le modèle asynchrone basé sur des événements](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 Décrit les contraintes liées à l'exposition de fonctionnalités asynchrones conformément au modèle asynchrone basé sur les événements.  
  
 [Deciding When to Implement the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 Explique dans quelles situations vous devez implémenter le modèle asynchrone basé sur les événements plutôt que le modèle <xref:System.IAsyncResult>.  
  
 [Walkthrough: Implementing a Component That Supports the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 Illustre la création d'un composant qui implémente le modèle asynchrone basé sur les événements.  Il est implémenté à l'aide de classes d'assistance à partir de l'espace de noms <xref:System.ComponentModel?displayProperty=fullName>, ce qui garantit le bon fonctionnement du composant avec n'importe quel modèle d'application.  
  
 [How to: Use Components That Support the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 Explique comment créer un composant qui prend en charge le modèle asynchrone basé sur les événements.  
  
## Référence  
 <xref:System.ComponentModel.AsyncOperation>  
 Décrit la classe <xref:System.ComponentModel.AsyncOperation> et propose des liens vers tous ses membres.  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 Décrit la classe <xref:System.ComponentModel.AsyncOperationManager> et propose des liens vers tous ses membres.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Décrit le composant <xref:System.ComponentModel.BackgroundWorker> et propose des liens vers tous ses membres.  
  
## Rubriques connexes  
 [Task Parallel Library \(TPL\)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 Décrit un modèle de programmation pour les opérations asynchrones et parallèles.  
  
 [Threading](../../../docs/standard/threading/index.md)  
 Décrit les fonctionnalités de multithreading du .NET Framework.  
  
 [Thread](../Topic/Threading%20\(C%23%20and%20Visual%20Basic\).md)  
 Décrit les fonctionnalités de multithreading des langages C\# et Visual Basic.  
  
## Voir aussi  
 [Managed Threading Best Practices](../../../docs/standard/threading/managed-threading-best-practices.md)   
 [Événements](../../../docs/standard/events/index.md)   
 [Multithreading in Components](../Topic/Multithreading%20in%20Components.md)   
 [Asynchronous Programming Design Patterns](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)