---
title: "Transfert des messages par diffusion en continu | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 72a47a51-e5e7-4b76-b24a-299d51e0ae5a
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# Transfert des messages par diffusion en continu
Les transports [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] prennent en charge deux modes de transfert pour les messages :  
  
-   Les transferts mis en mémoire tampon conservent la totalité des messages en mémoire tampon tant que leur transfert n'est pas terminé.Un message mis en mémoire tampon doit être entièrement remis pour que son destinataire puisse le lire.  
  
-   Les transferts en flux continu exposent les messages sous forme de flux.Le destinataire commence à traiter les messages avant que ceux\-ci ne soient complètement remis.  
  
-   Les transferts en flux continu permettent d'améliorer l'évolutivité d'un service car ils évitent d'avoir à recourir à de grandes mémoires tampon.Utilisez ce mode de transfert pour améliorer l'évolutivité en fonction de la taille des messages à transférer.Préférez le transfert en flux continu pour les messages de grande taille.  
  
 Par défaut, les transports HTTP, TCP\/IP et les transports de canal nommé utilisent les transferts mis en mémoire tampon.Cette rubrique contient des instructions permettant de faire basculer ces transports d'un mode de transfert mis en mémoire tampon à un mode de transfert en flux continu et présente les conséquences d'une telle modification.  
  
## Activation des transferts en flux continu  
 L'activation de l'un ou l'autre de ces modes s'effectue au niveau de l'élément de liaison du transport.La propriété <xref:System.ServiceModel.TransferMode> de l'élément de liaison peut avoir la valeur `Buffered`, `Streamed`, `StreamedRequest` ou `StreamedResponse`.L'affectation de `Streamed` au mode de transfert permet d'assurer la communication en mode de diffusion en continu dans les deux sens.L'affectation au mode de transfert de la valeur `StreamedRequest` ou `StreamedResponse` permet d'assurer des communications en flux continu dans le sens spécifié uniquement.  
  
 Les liaisons <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.NetTcpBinding> et <xref:System.ServiceModel.NetNamedPipeBinding> exposent la propriété <xref:System.ServiceModel.TransferMode>.Pour les autres transports, vous devez créer une liaison personnalisée pour pouvoir définir le mode de transfert.  
  
 Le choix de l'un ou l'autre des modes de transfert \(mis en mémoire tampon ou flux continu\) revient en local au point de terminaison.Pour les transports HTTP, le mode de transfert n'est pas propagé à la totalité de la connexion ni aux serveurs ni autres intermédiaires.La description de l'interface de service ne reflète pas le mode de transfert défini.Après création d'une classe client pour le service, vous devez modifier son fichier de configuration pour pouvoir passer du mode de transfert en flux continu au mode de transfert mis en mémoire tampon.Pour les transports TCP et les transports de canal nommé, le mode de transfert est propagé sous forme d'assertion de stratégie.  
  
 Pour obtenir des exemples de code, consultez [Comment : activer la diffusion en continu](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md).  
  
## Activation de la diffusion en continu asynchrone  
 Pour activer la diffusion en continu asynchrone, ajoutez le comportement de point de terminaison <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> à l'hôte de service et affectez à sa propriété <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> la valeur `true`.  
  
 Cette version de WCF ajoute aussi la diffusion en continu asynchrone du côté expéditeur.Cela améliore l'extensibilité du service dans les scénarios où des messages sont diffusés en continu à plusieurs clients, dont certains sont lents dans la lecture ; probablement en raison de la congestion du réseau ou ne lisent pas du tout.Dans ces scénarios, WCF ne bloque plus les threads individuels sur le service par client.Cela garantit que le service peut gérer beaucoup plus de clients fournissant ainsi l'extensibilité du service.  
  
## Restrictions relatives aux transferts en flux continu  
 L'utilisation du mode de transfert en flux continu provoque l'application de restrictions supplémentaires de la part de l'exécution.  
  
 Le contrat des opérations intervenant sur un transport en flux continu peut contenir au maximum un paramètre d'entrée ou de sortie.Ce paramètre incarne l'intégralité du corps des messages et doit être un <xref:System.ServiceModel.Channels.Message>, un type dérivé de <xref:System.IO.Stream> ou une implémentation de <xref:System.Xml.Serialization.IXmlSerializable>.Disposer d'une valeur de retour pour une opération équivaut à disposer d'un paramètre de sortie.  
  
 Certaines fonctionnalités [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], telles que la messagerie fiable, les transactions et la sécurité de niveau message SOAP s'appuient sur les messages en mémoire tampon pour leurs transmissions.L'utilisation de ces fonctionnalités peut réduire, voire annuler les gains en termes de performances obtenus grâce au flux continu.Pour sécuriser le transport en flux continu, utilisez la sécurité de niveau transport uniquement ou la sécurité de niveau transport et le sécurité de niveau message avec authentification uniquement.  
  
 Les en\-têtes SOAP sont toujours mis en mémoire tampon, même lorsque le mode de transfert a la valeur flux continu.La taille des en\-têtes de message ne doit pas dépasser la taille du quota de transport `MaxBufferSize`.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] ce paramètre, consultez [Quotas de transport](../../../../docs/framework/wcf/feature-details/transport-quotas.md).  
  
## Différences entre les transferts mis en mémoire tampon et les transferts en flux continu  
 Modifier le mode de transfert de mis en mémoire tampon à flux continu modifie également la forme du canal natif des transports TCP et des transports de canal nommé.Pour les transferts mis en mémoire tampon, la forme du canal natif est <xref:System.ServiceModel.Channels.IDuplexSessionChannel>.Pour les transferts en flux continu, les canaux natifs correspondent à <xref:System.ServiceModel.Channels.IRequestChannel> et à <xref:System.ServiceModel.Channels.IReplyChannel>.Modifier le mode de transfert d'une application existante utilisant directement ces transports \(c'est\-à\-dire sans passer par un contrat de service\) nécessite de modifier la forme de canal escomptée des fabrications et écouteurs de canal.  
  
## Voir aussi  
 [Comment : activer la diffusion en continu](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)