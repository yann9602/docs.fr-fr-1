---
title: "Meilleures pratiques : Intermédiaires"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bfedfbd0177018de4affce67f16ee5f713f7d5de
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="best-practices-intermediaries"></a>Meilleures pratiques : Intermédiaires
La prudence est de mise pour une gestion correcte des erreurs lors de l'appel des intermédiaires afin de s'assurer que les canaux du côté service sur l'intermédiaire sont fermés.  
  
 Prenons le scénario suivant : Un client appelle un intermédiaire qui appelle un service principal.  Le service principal ne définit pas de contrat d'erreur ; par conséquent, les erreurs détectées par ce service seront traitées comme une erreur non typée.  Le service principal lève une <xref:System.ApplicationException> et WCF abandonne le canal côté service. <xref:System.ApplicationException> apparaît ensuite en tant qu'exception <xref:System.ServiceModel.FaultException> levée sur l'intermédiaire. L'intermédiaire relève l'exception <xref:System.ApplicationException>. WCF interprète cette erreur comme une erreur non typée de l'intermédiaire et la transfère au client. Lors de la réception de l'erreur, l'intermédiaire et le client entraînent la défaillance de leurs canaux côté client. Le canal côté service de l'intermédiaire reste cependant ouvert, car WCF ignore que l'erreur est irrécupérable.  
  
 La meilleure pratique dans ce scénario consiste à détecter si l'erreur provenant du service est irrécupérable, et le cas échéant, si l'intermédiaire doit provoquer une défaillance de son canal côté service comme l'illustre l'extrait de code suivant.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des erreurs WCF](../../../docs/framework/wcf/wcf-error-handling.md)  
 [Spécification et gestion des erreurs dans les contrats et les services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
