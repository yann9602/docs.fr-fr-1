---
title: "Asynchronous Programming Using Delegates | Microsoft Docs"
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
  - "BeginInvoke method"
  - "asynchronous programming, delegates"
  - "asynchronous delegates"
  - "calling synchronous methods in asynchronous manner"
  - "EndInvoke method"
  - "calling asynchronous methods"
  - "delegates [.NET Framework], asynchronous"
  - "synchronous calling in asynchronous manner"
ms.assetid: 38a345ca-6963-4436-9608-5c9defef9c64
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# Asynchronous Programming Using Delegates
Les délégués permettent d'appeler une méthode synchrone de manière asynchrone.  Lorsqu'un délégué est appelé de façon synchrone, la méthode `Invoke` appelle directement la méthode cible sur le thread actif.  Si la méthode `BeginInvoke` est appelée, le Common Language Runtime \(CLR\) met la requête en file d'attente et retourne immédiatement à l'appelant.  La méthode cible est appelée de façon asynchrone sur un thread à partir du pool de threads.  Le thread d'origine, qui a envoyé la requête, peut continuer l'exécution en parallèle avec la méthode cible.  Si une méthode de rappel a été spécifiée dans l'appel à la méthode `BeginInvoke`, la méthode de rappel est appelée lors du retour de la méthode cible.  Dans la méthode de rappel, la méthode `EndInvoke` obtient la valeur de retour et n'importe quel paramètre d'entrée\/de sortie ou uniquement de sortie.  Si aucune méthode de rappel n'est spécifiée lors de l'appel à `BeginInvoke`, `EndInvoke` peut être appelé à partir du thread qui a appelé `BeginInvoke`.  
  
> [!IMPORTANT]
>  Les compilateurs doivent émettre des classes déléguées avec les méthodes `Invoke`, `BeginInvoke` et `EndInvoke` à l'aide de la signature de délégué spécifiée par l'utilisateur.  Les méthodes `BeginInvoke` et `EndInvoke` doivent être décorées comme natives.  Étant donné que ces méthodes sont marquées comme étant natives, le Common Language Runtime fournit automatiquement l'implémentation au moment du chargement de la classe.  Le chargeur vérifie qu'elles ne sont pas substituées.  
  
## Dans cette section  
 [Calling Synchronous Methods Asynchronously](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 Explique l'utilisation de délégués pour appeler de façon asynchrone les méthodes ordinaires et fournit des exemples de code simples qui présentent les quatre façons d'attendre le retour d'un appel asynchrone.  
  
 [Exemple de programmation de délégués asynchrones](../Topic/Asynchronous%20Delegates%20Programming%20Sample.md)  
 Explique l'utilisation de délégués pour effectuer des appels asynchrones, dans un exemple de code plus complexe qui factorise les nombres.  
  
## Rubriques connexes  
 [Event\-based Asynchronous Pattern \(EAP\)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 Décrit la programmation asynchrone avec le .NET Framework.  
  
## Voir aussi  
 <xref:System.Delegate>