---
title: "Traitement ordonné des messages en mode de concurrence simple"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c50381c678a84f5602d08342d02dbf44316994c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a>Traitement ordonné des messages en mode de concurrence simple
WCF ne garantit pas sur l’ordre dans lequel les messages sont traités, à moins que le canal sous-jacent est la session.  Par exemple, un service WCF qui utilise MsmqInputChannel, ce qui n’est pas un canal de session, ne pourront pas traiter les messages dans l’ordre. Il existe certains cas où un développeur peut le comportement de traitement des commandes en mais que vous souhaitez pas utiliser des sessions. Cette rubrique décrit comment configurer ce comportement lorsqu'un service s'exécute en mode de concurrence simple.  
  
## <a name="in-order-message-processing"></a>Traitement des messages dans l'ordre  
 Un nouvel attribut nommé <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> a été ajouté à la classe <xref:System.ServiceModel.ServiceBehaviorAttribute>. Lorsque <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> a la valeur true et <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> a la valeur <xref:System.ServiceModel.ConcurrencyMode.Single> les messages envoyés au service sont traités dans l'ordre. L'extrait de code suivant illustre comment définir ces attributs.  
  
```  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 Si une autre valeur est affectée à la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>, une exception <xref:System.InvalidOperationException> est levée.  
  
## <a name="see-also"></a>Voir aussi  
 [Sessions, instanciation et accès concurrentiel](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 [Concurrence](../../../../docs/framework/wcf/samples/concurrency.md)
