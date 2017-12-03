---
title: "Corrélation demande-réponse"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 29286950cfef7d8e3e2c453bbdcc307c26e641de
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="request-reply-correlation"></a>Corrélation demande-réponse
Corrélation demande-réponse est utilisée avec un <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> paire pour implémenter une opération bidirectionnelle dans un service de workflow et avec un <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> paire qui appelle une opération bidirectionnelle dans un autre site Web service. Lors de l'appel d'une opération bidirectionnelle dans un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], le service peut être soit un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] basé sur un code impératif traditionnel, soit un service de workflow. Pour utiliser la corrélation demande-réponse, une liaison bidirectionnelle doit être utilisée, telle que <xref:System.ServiceModel.BasicHttpBinding>. Qu'il s'agisse d'appeler ou d'implémenter une opération bidirectionnelle, les étapes d'initialisation de la corrélation sont similaires ; elles sont présentées dans cette section.  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a>Utilisation de la corrélation dans une opération bidirectionnelle avec Receive/SendReply  
 A <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> paire est utilisée pour implémenter une opération bidirectionnelle dans un service de workflow. L'exécution utilise la corrélation demande-réponse pour vérifier que la réponse est distribuée à l'appelant approprié. Lorsqu'un workflow est hébergé à l'aide de <xref:System.ServiceModel.Activities.WorkflowServiceHost>, ce qui est le cas des services de workflow, l'initialisation de la corrélation par défaut est suffisante. Dans ce scénario, un <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> paire est utilisée par un flux de travail, et aucune configuration de corrélation spécifique est nécessaire.  
  
```csharp  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
### <a name="explicitly-initializing-request-reply-correlation"></a>Initialisation explicite de la corrélation demande-réponse  
 Si d'autres opérations bidirectionnelles existent en parallèle, la corrélation doit être configurée de manière explicite. Cela est possible en spécifiant un <xref:System.ServiceModel.Activities.CorrelationHandle> et <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, ou en plaçant le <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> à l’intérieur d’un <xref:System.ServiceModel.Activities.CorrelationScope>. Dans cet exemple, la corrélation demande-réponse est configurée sur un <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> paire.  
  
```csharp  
Variable<CorrelationHandle> RRHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder",  
    CorrelationInitializers =  
    {  
        new RequestReplyCorrelationInitializer  
        {  
            CorrelationHandle = RRHandle  
        }  
    }  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
 Au lieu de configurer la corrélation de manière explicite, une activité <xref:System.ServiceModel.Activities.CorrelationScope> peut être utilisée. <xref:System.ServiceModel.Activities.CorrelationScope> fournit un <xref:System.ServiceModel.Activities.CorrelationHandle> implicite aux activités de messagerie qu'il contient. Dans cet exemple, un <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> paire est contenue dans un <xref:System.ServiceModel.Activities.CorrelationScope>. Aucune configuration de corrélation explicite n'est nécessaire.  
  
```csharp  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
CorrelationScope s = new CorrelationScope  
{  
    Body = new Sequence  
    {  
        Activities =   
        {  
            StartOrder,  
            // Activities that create the reply.  
            ReplyToStartOrder  
        }  
    }  
};  
  
// Construct a workflow using the CorrelationScope.  
```  
  
 Si nécessaire, des corrélations supplémentaires peuvent être configurées à l'aide de la propriété <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> des activités de messagerie respectives utilisant les types `CorrelationInitializer` souhaités.  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a>Utilisation de la corrélation dans une opération bidirectionnelle avec Send/ReceiveReply  
 Alors que le <xref:System.ServiceModel.Activities.Receive> activité peut uniquement être utilisée dans un service de workflow hébergé par <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.ServiceModel.Activities.Send> et <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> paire peut être utilisée dans n’importe quel flux de travail qui doit appeler une méthode sur un service Web. Si le workflow est hébergé à l'aide de l'objet <xref:System.ServiceModel.Activities.WorkflowServiceHost>, la corrélation par défaut décrite dans la section précédente s'applique, mais si ce n'est pas le cas, la corrélation doit être configurée soit de manière explicite à l'aide des objets <xref:System.ServiceModel.Activities.CorrelationInitializer> et <xref:System.ServiceModel.Activities.CorrelationHandle> souhaités, soit en utilisant la gestion de handle implicite de l'objet <xref:System.ServiceModel.Activities.CorrelationScope>.  
  
 Lorsque vous utilisez **ajouter une référence de Service** sur un service avec des opérations bidirectionnelles, les activités générées encapsulent un <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> paire d’activités en interne avec la corrélation demande/réponse explicitement spécifié.
