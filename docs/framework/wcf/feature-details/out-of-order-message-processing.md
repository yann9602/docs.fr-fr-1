---
title: "Traitement des messages dans le désordre"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33fc62a5-5d59-461c-a37a-0e1b51ac763d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f70283e15bbfaf111c8e677641682538a2361942
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="out-of-order-message-processing"></a>Traitement des messages dans le désordre
Les services de workflow peuvent dépendre de l'ordre dans lequel sont envoyés les messages. Un service de workflow contient une ou plusieurs activités <xref:System.ServiceModel.Activities.Receive> et chaque activité <xref:System.ServiceModel.Activities.Receive> attend un message spécifique. Sans garanties particulières de remise par le transport, les messages envoyés par des clients peuvent être différés et par conséquent remis dans un ordre non prévu par le service de workflow. L'implémentation d'un service de workflow qui ne requiert aucun ordre particulier d'envoi des messages s'effectue en principe à l'aide d'une activité Parallèle. Pour un protocole d'application plus complexe, le workflow risque de se compliquer très rapidement.  La fonctionnalité de traitement des messages dans le désordre dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vous permet de créer un workflow de ce type, en évitant la complexité des activités Parallèles imbriquées. Le traitement des messages dans le désordre n'est possible que sur les canaux qui prennent en charge l'objet <xref:System.ServiceModel.Channels.ReceiveContext>, comme les liaisons MSMQ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="enabling-out-of-order-message-processing"></a>Activation du traitement des messages dans le désordre  
 Le traitement des messages dans le désordre est activé en définissant la propriété <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> à la valeur `true` dans le WorkflowService. L'exemple suivant montre comment définir la propriété <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> dans le code.  
  
```csharp  
// Code: Opt-in to Buffered Receive processing...  
WorkflowService service = new WorkflowService  
{  
    Name="MyService",  
    Body = workflow,  
    AllowBufferedReceive = true  
};  
```  
  
 Vous pouvez également appliquer l'attribut `AllowBufferedReceive` à un service de workflow en XAML, comme indiqué dans l'exemple suivant.  
  
```xaml  
// Xaml: Opt-in to Buffered Receive processing...  
<WorkflowService AllowBufferedReceive="True">  
   <!—the actual children activities -->  
</Sequence>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Channels.ReceiveContext>  
 [Services de workflow](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Les files d’attente et les Sessions fiables](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
