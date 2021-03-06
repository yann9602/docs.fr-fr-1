---
title: "Programmation asynchrone à l'aide de délégués"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BeginInvoke method
- asynchronous programming, delegates
- asynchronous delegates
- calling synchronous methods in asynchronous manner
- EndInvoke method
- calling asynchronous methods
- delegates [.NET Framework], asynchronous
- synchronous calling in asynchronous manner
ms.assetid: 38a345ca-6963-4436-9608-5c9defef9c64
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e84c004c8efc58c6d6ad55674470bec13fc0bab8
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="asynchronous-programming-using-delegates"></a>Programmation asynchrone à l'aide de délégués
Les délégués permettent d’appeler une méthode synchrone de manière asynchrone. Lorsque vous appelez un délégué de manière synchrone, la méthode `Invoke` appelle la méthode cible directement sur le thread actuel. Si la méthode `BeginInvoke` est appelée, le common language runtime (CLR) met en file d’attente la demande et retourne immédiatement à l’appelant. La méthode cible est appelée de façon asynchrone sur un thread du pool de threads. Le thread d’origine, qui a envoyé la demande, est libre de continuer à s’exécuter en parallèle avec la méthode cible. Si une méthode de rappel a été spécifiée dans l’appel à la méthode `BeginInvoke`, la méthode de rappel est appelée lorsque la méthode cible se termine. Dans la méthode de rappel, la méthode `EndInvoke` obtient la valeur de retour et d’éventuels paramètres d’entrée/sortie ou de sortie uniquement. Si aucune méthode de rappel n’est spécifiée lors de l’appel à `BeginInvoke`, `EndInvoke` peut être appelé depuis le thread qui a appelé `BeginInvoke`.  
  
> [!IMPORTANT]
>  Les compilateurs doivent émettre des classes déléguées avec les méthodes `Invoke`, `BeginInvoke` et `EndInvoke` à l’aide de la signature de délégué spécifiée par l’utilisateur. Les méthodes `BeginInvoke` et `EndInvoke` doivent être décorées comme étant natives. Étant donné que ces méthodes sont marquées comme étant natives, le CLR fournit automatiquement l’implémentation au moment du chargement de la classe. Le chargeur garantit qu’elles ne sont pas remplacées.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Appel de méthodes synchrones de façon asynchrone](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 Décrit l’utilisation de délégués pour effectuer des appels asynchrones à des méthodes ordinaires et fournit des exemples de code simples qui présentent les quatre façons d’attendre un appel asynchrone à retourner.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Modèle asynchrone basé sur les événements (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 Décrit la programmation asynchrone avec le .NET Framework.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Delegate>
