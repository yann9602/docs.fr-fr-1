---
title: "Meilleures pratiques : interm&#233;diaires | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# Meilleures pratiques : interm&#233;diaires
Il faut veiller à gérer les erreurs correctement lors de l'appel d'intermédiaires afin de s'assurer que les canaux du côté du service sur l'intermédiaire sont fermés correctement.  
  
 Prenons le scénario suivant.Un client appelle un intermédiaire qui appelle à sont tour un service principal.Le service principal définit un contrat sans erreur ; par conséquent toute erreur générée à partir de ce service sera traitée comme une erreur typée.Le service principal lève une exception <xref:System.ApplicationException> et WCF abandonne correctement le canal du côté du service.L'exception <xref:System.ApplicationException> apparaît en tant que <xref:System.ServiceModel.FaultException> levée pour l'intermédiaire.L'intermédiaire lève de nouveau l'exception <xref:System.ApplicationException>.WCF interprète cela comme une erreur non typée de l'intermédiaire et la transfère au client.Lors de la réception de l'erreur, l'intermédiaire et le client mettent en défaillance leurs canaux du côté du client.Cependant, le canal du côté du service de l'intermédiaire reste ouvert, car WCF ne sait pas que l'erreur est irrécupérable.  
  
 La meilleure pratique dans ce scénario consiste à déterminer si l'erreur du service est irrécupérable et le cas échéant, l'intermédiaire doit mettre en défaillance son canal du côté du service tel que l'indique l'extrait de code ci\-dessous.  
  
```csharp  
catch (Exception e)  
{  
    bool faulted = service.State == CommunicationState.Faulted;  
    service.Abort();  
    if (faulted)  
    {  
        throw new ApplicationException(e.Message);  
    }  
    Else  
    {  
        throw;  
    }  
}  
  
```  
  
## Voir aussi  
 [Gestion des erreurs WCF](../../../docs/framework/wcf/wcf-error-handling.md)   
 [Spécification et gestion des erreurs dans les contrats et les services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)