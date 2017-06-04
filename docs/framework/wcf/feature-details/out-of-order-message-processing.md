---
title: "Traitement des messages dans le d&#233;sordre | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 33fc62a5-5d59-461c-a37a-0e1b51ac763d
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Traitement des messages dans le d&#233;sordre
Les services de workflow peuvent dépendre de l'ordre dans lequel sont envoyés les messages.Un service de workflow contient une ou plusieurs activités <xref:System.ServiceModel.Activities.Receive> et chaque activité <xref:System.ServiceModel.Activities.Receive> attend un message spécifique.Sans garanties particulières de remise par le transport, les messages envoyés par des clients peuvent être différés et par conséquent remis dans un ordre non prévu par le service de workflow.L'implémentation d'un service de workflow qui ne requiert aucun ordre particulier d'envoi des messages s'effectue en principe à l'aide d'une activité Parallèle.Pour un protocole d'application plus complexe, le workflow risque de se compliquer très rapidement.La fonctionnalité de traitement des messages dans le désordre dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vous permet de créer un workflow de ce type, en évitant la complexité des activités Parallèles imbriquées.Le traitement des messages dans le désordre n'est possible que sur les canaux qui prennent en charge l'objet <xref:System.ServiceModel.Channele.ReceiveContext>, comme les liaisons MSMQ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## Activation du traitement des messages dans le désordre  
 Le traitement des messages dans le désordre est activé en définissant la propriété <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> à la valeur `true` dans le WorkflowService.L'exemple suivant montre comment définir la propriété <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> dans le code.  
  
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
  
## Voir aussi  
 <xref:System.ServiceModel.Channels.ReceiveContext>   
 [Services de workflow](../../../../docs/framework/wcf/feature-details/workflow-services.md)   
 [Files d'attente et sessions fiables](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)