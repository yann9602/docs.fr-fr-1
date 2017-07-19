---
title: "Corr&#233;lation demande-r&#233;ponse | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Corr&#233;lation demande-r&#233;ponse
La corrélation demande\-réponse est utilisée avec une paire <xref:System.ServiceModel.Activities.Receive>\/<xref:System.ServiceModel.Activities.SendReply> pour implémenter une opération bidirectionnelle dans un service de workflow et avec une paire <xref:System.ServiceModel.Activities.Send>\/<xref:System.ServiceModel.Activities.ReceiveReply> qui appelle une opération bidirectionnelle dans un autre service Web.  Lors de l'appel d'une opération bidirectionnelle dans un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], le service peut être soit un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] basé sur un code impératif traditionnel, soit un service de workflow.  Pour utiliser la corrélation demande\-réponse, une liaison bidirectionnelle doit être utilisée, telle que <xref:System.ServiceModel.BasicHttpBinding>.  Qu'il s'agisse d'appeler ou d'implémenter une opération bidirectionnelle, les étapes d'initialisation de la corrélation sont similaires ; elles sont présentées dans cette section.  
  
## Utilisation de la corrélation dans une opération bidirectionnelle avec Receive\/SendReply  
 Une paire <xref:System.ServiceModel.Activities.Receive>\/<xref:System.ServiceModel.Activities.SendReply> sert à implémenter une opération bidirectionnelle dans un service de workflow.  L'exécution utilise la corrélation demande\-réponse pour vérifier que la réponse est distribuée à l'appelant approprié.  Lorsqu'un workflow est hébergé à l'aide de <xref:System.ServiceModel.Activities.WorkflowServiceHost>, ce qui est le cas des services de workflow, l'initialisation de la corrélation par défaut est suffisante.  Dans ce scénario, une paire <xref:System.ServiceModel.Activities.Receive>\/<xref:System.ServiceModel.Activities.SendReply> est utilisée par un workflow, et aucune configuration de corrélation spécifique n'est nécessaire.  
  
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
  
### Initialisation explicite de la corrélation demande\-réponse  
 Si d'autres opérations bidirectionnelles existent en parallèle, la corrélation doit être configurée de manière explicite.  Pour ce faire, spécifiez un objet <xref:System.ServiceModel.Activities.CorrelationHandle> et un objet <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, ou placez la paire <xref:System.ServiceModel.Activities.Receive>\/<xref:System.ServiceModel.Activities.SendReply> dans un objet <xref:System.ServiceModel.Activities.CorrelationScope>.  Dans cet exemple, la corrélation demande\-réponse est configurée sur une paire <xref:System.ServiceModel.Activities.Receive>\/<xref:System.ServiceModel.Activities.SendReply>.  
  
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
  
 Au lieu de configurer la corrélation de manière explicite, une activité <xref:System.ServiceModel.Activities.CorrelationScope> peut être utilisée.  <xref:System.ServiceModel.Activities.CorrelationScope> fournit un <xref:System.ServiceModel.Activities.CorrelationHandle> implicite aux activités de messagerie qu'il contient.  Dans cet exemple, une paire <xref:System.ServiceModel.Activities.Receive>\/<xref:System.ServiceModel.Activities.SendReply> est contenue à l'intérieur d'un <xref:System.ServiceModel.Activities.CorrelationScope>.  Aucune configuration de corrélation explicite n'est nécessaire.  
  
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
  
## Utilisation de la corrélation dans une opération bidirectionnelle avec Send\/ReceiveReply  
 Alors que l'activité <xref:System.ServiceModel.Activities.Receive> ne peut être utilisée que dans un service de workflow hébergé par <xref:System.ServiceModel.Activities.WorkflowServiceHost>, l'activité <xref:System.ServiceModel.Activities.Send> et la paire <xref:System.ServiceModel.Activities.Send>\/<xref:System.ServiceModel.Activities.ReceiveReply> peuvent être utilisées dans tout workflow qui doit appeler une méthode sur un service Web.  Si le workflow est hébergé à l'aide de l'objet <xref:System.ServiceModel.Activities.WorkflowServiceHost>, la corrélation par défaut décrite dans la section précédente s'applique, mais si ce n'est pas le cas, la corrélation doit être configurée soit de manière explicite à l'aide des objets <xref:System.ServiceModel.Activities.CorrelationInitializer> et <xref:System.ServiceModel.Activities.CorrelationHandle> souhaités, soit en utilisant la gestion de handle implicite de l'objet <xref:System.ServiceModel.Activities.CorrelationScope>.  
  
 Lors de l'utilisation de la fonction **Ajouter une référence de service** sur un service ayant des opérations bidirectionnelles, les activités générées encapsulent en interne une paire d'activités <xref:System.ServiceModel.Activities.Send>\/<xref:System.ServiceModel.Activities.ReceiveReply> et la corrélation demande\-réponse est spécifiée de manière explicite.