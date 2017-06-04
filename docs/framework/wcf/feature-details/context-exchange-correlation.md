---
title: "Corr&#233;lation d&#39;&#233;change de contexte | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1e2852be-3601-45ae-b507-ccc465d45c60
caps.latest.revision: 18
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 18
---
# Corr&#233;lation d&#39;&#233;change de contexte
La corrélation de contexte est basée sur le mécanisme d'échange de contexte décrit dans [.NET Context Exchange Protocol Specification](http://go.microsoft.com/fwlink/?LinkId=166059) \(en anglais\).La corrélation de contexte utilise un en\-tête ou un cookie de contexte bien connu pour lier les messages à l'instance correcte.Pour utiliser la corrélation de contexte, une liaison basée sur le contexte, telle que <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding> ou <xref:System.ServiceModel.NetTcpContextBinding>, doit être utilisée sur le point de terminaison fourni à l'objet <xref:System.ServiceModel.Activities.WorkflowServiceHost>.Cette rubrique explique comment utiliser la corrélation de contexte avec des activités de messagerie dans un service de workflow.  
  
## Utilisation de la corrélation de contexte  
 La corrélation de contexte est utilisée lorsqu'un client doit faire des appels répétés dans un service de workflow et que le service est hébergé en utilisant l'une des liaisons de contexte.Ce type de corrélation est initialisé par une paire <xref:System.ServiceModel.Activities.Receive>\/<xref:System.ServiceModel.Activities.SendReply> dans le service de workflow.Le contexte est renvoyé au client avec la réponse, puis le client joint ce contexte dans les appels ultérieurs au service.  
  
### Configuration de la corrélation de contexte dans un service de workflow  
 La corrélation de contexte est initialisée à l'aide d'un objet <xref:System.ServiceModel.Activities.ContextCorrelationInitializer>, associé à l'activité <xref:System.ServiceModel.Activities.SendReply> qui répond au message entrant initial.Dans l'exemple suivant, l'activité <xref:System.ServiceModel.Activities.SendReply> est configurée pour initialiser une corrélation de contexte.  
  
```csharp  
Variable<string> Item = new Variable<string>();  
Variable<CorrelationHandle> OrderHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = "IOrderService",  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    CorrelationInitializers =  
    {  
        new ContextCorrelationInitializer  
        {  
            CorrelationHandle = OrderHandle  
        }  
    }  
};  
```  
  
> [!NOTE]
>  Dans cet exemple, deux types de correlation sont en fait utilisés : la corrélation de contexte et la corrélation demande\-réponse.La corrélation de contexte est utilisée pour que les appels des clients soient acheminés à l'instance correcte.La corrélation demande\-réponse est utilisée à la fois par les activités <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply> pour implémenter l'opération bidirectionnelle modelée par ces activités.Dans cet exemple, seule la corrélation de contexte est explicitement configurée, et la paire <xref:System.ServiceModel.Activities.Receive>\/<xref:System.ServiceModel.Activities.SendReply> utilise la corrélation demande\-réponse par défaut, fournie par la gestion de <xref:System.ServiceModel.Activities.CorrelationHandle> implicite du <xref:System.ServiceModel.Activities.WorkflowServiceHost>.Lors de l'utilisation du modèle d'activité **ReceiveAndSendReply** dans le concepteur de workflow, la corrélation demande\-réponse est explicitement configurée.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] la corrélation demande\-réponse et la gestion implicite de handle de corrélation, consultez [Demande\-réponse](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md) et [Vue d'ensemble de la corrélation](../../../../docs/framework/wcf/feature-details/correlation-overview.md).[!INCLUDE[crabout](../../../../includes/crabout-md.md)] le modèle d'activité **ReceiveAndSendReply**, consultez [ReceiveAndSendReply](../Topic/ReceiveAndSendReply%20Template%20Designer.md).  
  
 Les activités <xref:System.ServiceModel.Activities.Receive> ultérieures dans le service de workflow peuvent référencer le <xref:System.ServiceModel.Activities.CorrelationHandle> initialisé par l'activité <xref:System.ServiceModel.Activities.SendReply> dans l'exemple précédent.  
  
```csharp  
Receive AddItem = new Receive  
{  
    ServiceContractName = "IOrderService",  
    OperationName = "AddItem",  
    CorrelatesWith = OrderHandle  
};  
```  
  
 Le point de terminaison est ensuite configuré sur le <xref:System.ServiceModel.Activities.WorkflowServiceHost> pour utiliser une liaison basée sur le contexte, telle que <xref:System.ServiceModel.BasicHttpContextBinding>.  
  
```xml  
<endpoint  
  contract=”IOrderContract”  
  binding = “basicHttpContextBinding”  
  address=”http://localhost:8080/OrderService” />  
```  
  
### Configuration de la corrélation de contexte dans un client workflow  
 Lorsque le client est un autre workflow, la corrélation de contexte doit être également configurée sur le client.Sur le workflow client, l'activité <xref:System.ServiceModel.Activities.ReceiveReply> de la paire <xref:System.ServiceModel.Activities.Send>\/<xref:System.ServiceModel.Activities.ReceiveReply> qui effectue l'appel initial au service de workflow doit être configurée avec un objet <xref:System.ServiceModel.Activities.ContextCorrelationInitializer>.  
  
```csharp  
Variable<CorrelationHandle> cchandle = new Variable<CorrelationHandle>();  
Send request = new Send  
{  
    // Activity configuration omitted.  
};  
  
ReceiveReply reply = new ReceiveReply  
{  
    Request = request,  
    CorrelationInitializers =   
    {  
        new ContextCorrelationInitializer  
        {  
            CorrelationHandle = cchandle  
        }  
    }  
};  
```  
  
 Une fois la corrélation initialisée, les activités <xref:System.ServiceModel.Activities.Send> ultérieures peuvent utiliser le <xref:System.ServiceModel.Activities.CorrelationHandle> pour appeler les méthodes sur la même instance du service.  
  
```csharp  
Send request2 = new Send  
{  
    CorrelatesWith = cchandle,  
    // Remaining activity configuration omitted.  
};  
```  
  
 Notez que dans ces exemples, la corrélation de contexte a été configurée de manière explicite.Si le workflow client n'est pas également hébergé dans un <xref:System.ServiceModel.Activities.WorkflowServiceHost>, la corrélation doit être configurée de manière explicite, sauf si les activités sont contenues dans une activité <xref:System.ServiceModel.Activities.CorrelationScope>.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] la corrélation de contexte, consultez l'exemple [NetContextExchangeCorrelation](http://msdn.microsoft.com/fr-fr/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf).  
  
 Si le client qui appelle le service de workflow n'est pas un workflow, il peut toujours répéter ses appels, à condition de retransmettre de manière explicite le contexte retourné par le premier appel au service de workflow.Les proxys générés en ajoutant une référence de service dans [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] stockent et transmettent ce contexte par défaut.