---
title: "F&#233;d&#233;ration et confiance | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fédération (WCF), et confiance"
ms.assetid: 4bdec4f2-f8a2-4512-bdcf-14ef54b5877a
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# F&#233;d&#233;ration et confiance
Cette rubrique couvre divers aspects relatifs aux applications fédérées, aux limites d'approbation et à la configuration, ainsi qu'à l'utilisation de jetons émis dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
## Services, services d'émission de jeton de sécurité et confiance  
 Les services qui exposent des points de terminaison fédérés s'attendent en général à ce que les clients s'authentifient à l'aide d'un jeton fourni par un émetteur spécifique.Il est important que le service soit configuré avec les informations d'identification correctes de l'émetteur ; dans le cas contraire, il ne sera pas en mesure de vérifier les signatures sur les jetons émis, et le client ne pourra pas communiquer avec le service.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] la configuration des informations d'identification de l'émetteur sur le service, consultez [Comment : configurer des informations d'identification sur un service FS \(Federation Service\)](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
 De la même façon, lorsque vous utilisez des clés symétriques, les clés sont chiffrées pour le service cible et vous devez donc configurer le service d'émission de jeton de sécurité avec les informations d'identification correctes du service cible ; dans le cas contraire, il ne sera pas en mesure de chiffrer la clé pour le service cible, et une nouvelle fois, le client ne pourra pas communiquer avec le service.  
  
 Les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilisent la valeur de la propriété <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> sur [SecurityBindingElement](../../../../docs/framework/wcf/diagnostics/wmi/securitybindingelement.md) pour autoriser l'inclinaison de l'horloge entre le client et le service.Dans la fédération, le paramètre `MaxClockSkew` s'applique aux inclinaisons de l'horloge entre à la fois le client et le service d'émission de jeton de sécurité à partir duquel le client a obtenu le jeton émis.Par conséquent, les services d'émission de jeton de sécurité n'ont pas besoin d'allouer d'inclinaison d'horloge lors de la définition des délais de validité et d'expiration du jeton émis.  
  
> [!NOTE]
>  L'importance de l'inclinaison de l'horloge augmente à mesure que la durée de vie du jeton émis raccourcit.Dans la plupart des cas, l'inclinaison de l'horloge n'est pas un problème significatif si la durée de vie du jeton est de 30 minutes ou plus.Des scénarios avec des durées de vie plus courtes ou dans lesquels le délai de validité exact du jeton est important doivent être conçus afin de prendre l'inclinaison de l'horloge en compte.  
  
## Points de terminaison fédérés et délais d'expiration  
 Lorsqu'un client communique avec un point de terminaison fédéré, il doit tout d'abord acquérir un jeton approprié d'un service d'émission de jeton de sécurité.Si le service d'émission de jeton de sécurité expose un point de terminaison fédéré, le client doit en premier lieu obtenir un jeton de l'émetteur pour ce point de terminaison.Chaque acquisition de jeton prend du temps, et ce temps est soumis au délai d'expiration total pour l'envoi du message réel au point de terminaison final.  
  
 Par exemple, le délai d'expiration sur le canal côté client a pour valeur 30 secondes.Deux émetteurs de jeton doivent être appelés pour récupérer des jetons avant d'envoyer le message au point de terminaison final, et chacun prend 15 secondes pour émettre un jeton.Dans ce cas, la tentative échoue et une exception <xref:System.TimeoutException> est levée.Vous devez donc définir <xref:System.ServiceModel.IContextChannel.OperationTimeout%2A> sur le canal client à une valeur suffisamment élevée pour inclure le temps pris pour récupérer tous les jetons émis.Si aucune valeur n'est spécifiée pour la propriété <xref:System.ServiceModel.IContextChannel.OperationTimeout%2A>, la propriété <xref:System.ServiceModel.Channels.Binding.OpenTimeout%2A> ou la propriété <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A> \(ou les deux\) doivent avoir une valeur suffisamment élevée pour inclure le temps pris pour récupérer tous les jetons émis.  
  
## Renouvellement et durée de vie des jetons  
 Les clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne vérifient pas le jeton émis lorsqu'ils effectuent une demande initiale à un service.Au lieu de cela, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] approuve le service d'émission de jeton de sécurité pour émettre un jeton avec des délais de validité et d'expiration appropriés.Si le jeton est mis en cache par le client et réutilisé, sa durée de vie est vérifiée sur les demandes suivantes, et le client le renouvelle automatiquement si nécessaire.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] la mise en cache des jetons, consultez [Comment : créer un client fédéré](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).  
  
 La spécification de durées de vie courtes, de l'ordre de 30 secondes ou moins pour les jetons émis ou les jetons de contexte de sécurité, peut provoquer l'expiration de la négociation ou la levée d'autres exceptions par les clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] lors de la demande des jetons émis, ou lors de la négociation ou du renouvellement des jetons de contexte de sécurité.  
  
## Jetons émis et InclusionMode  
 Qu'un jeton émis soit ou non sérialisé dans un message envoyé d'un client vers un point de terminaison fédéré, il est contrôlé en définissant la propriété <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.InclusionMode%2A> de la classe <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters>.Cette propriété peut prendre l'une des valeurs de l'énumération <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>, mais ce n'est pas utile dans la plupart des scénarios fédérés.Les valeurs `SecurityTokenInclusionMode.Never` et `SecurityTokenInclusionMode.AlwaysToInitiator` provoquent l'envoi par le client d'une référence au jeton émis par le service d'émission de jeton de sécurité à la partie de confiance.Sauf si la partie de confiance possède une copie du jeton émis, l'authentification échouera car la référence du jeton ne peut pas être résolue.[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] considère `SecurityTokenInclusionMode.Once` comme équivalent à `SecurityTokenInclusionMode.AlwaysToRecipient`.  
  
## Voir aussi  
 <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>   
 [Comment : créer un client fédéré](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)   
 [Comment : configurer des informations d'identification sur un service FS \(Federation Service\)](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)   
 [Comment : créer une liaison WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)