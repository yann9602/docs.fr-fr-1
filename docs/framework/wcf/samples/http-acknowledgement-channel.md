---
title: "HTTP Acknowledgement Channel | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 469f3056-5ef2-4753-8acf-b574d23d83cf
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# HTTP Acknowledgement Channel
HTTP Acknowledgement Channel est un exemple d'un canal superposé qui modifie le modèle de messagerie unidirectionnel pour permettre à un service d'accepter ou de refuser des messages entrants plutôt que d'envoyer automatiquement un accusé de réception.HTTP Acknowledgement Channel permet également au service de différer l'accusé de réception jusqu'à ce qu'il puisse garantir au niveau de l'entreprise que le message sera traité.  
  
## Démonstrations  
 <xref:System.ServiceModel.Channels.ReceiveContext>, exemple de canal superposé \(HTTP Acknowledgement Channel\).  
  
## Discussion  
 HTTP Acknowledgement Channel implémente <xref:System.ServiceModel.Channels.ReceiveContext> pour restructurer le modèle de messagerie requête\-réponse HTTP en modèle unidirectionnel avec accusé de réception différé.À l'aide de ce nouveau modèle, un service peut vérifier le traitement du message en envoyant un accusé de réception sous forme de code d'état HTTP OK \(200\) sans bloquer le client jusqu'à ce que le traitement du message soit terminé ou peut envoyer un message d'échec au client sous forme de code d'état HTTP Erreur interne du serveur \(500\).Par exemple, un service peut envoyer un accusé de réception après avoir écrit un message dans une file d'attente, puis continuer le traitement du message de façon asynchrone.Dans ce scénario, un client peut être assuré que ses messages ont été traités au moins une fois par le service, s'il a renvoyé chaque message jusqu'à obtention d'un accusé de réception en provenance du service.Notez que, si un service requiert un traitement asynchrone rapide des messages sur HTTP, sans garantie de leur traitement, <xref:System.ServiceModel.Channels.OneWayBindingElement> est un choix plus approprié.  
  
 <xref:System.ServiceModel.Channels.ReceiveContext> est utilisé pour maintenir le message en place pendant le temps nécessaire à déterminer s'il peut être traité au niveau du service.La capacité d'un service à traiter le message avec succès est indiquée en appelant Complete sur l'objet <xref:System.ServiceModel.Channels.ReceiveContext> qui envoie le code d'état HTTP OK et la capacité du service à traiter le message est indiquée en appelant la méthode `Abandon` de <xref:System.ServiceModel.Channels.ReceiveContext> sur l'objet <xref:System.ServiceModel.Channels.ReceiveContext>, qui envoie le code d'état HTTP Erreur interne du serveur.  
  
 Dans cet exemple, le client demande les informations de traitement en envoyant un ID d'employé.Du côté du service, si l'ID d'employé reçu est supérieur à 50, le service renvoie le code d'état HTTP 500 \(Erreur interne du serveur\) au client ; sinon il est supposé que le traitement peut être effectué avec succès et le code d'état HTTP 200 \(réussite\) est renvoyé au client.  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  Ouvrez [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] avec les privilèges d'administrateur.  
  
2.  Ouvrez la solution **HttpAckChannel**.  
  
3.  Démarrez une nouvelle instance du projet **Service** en cliquant avec le bouton droit sur le projet dans l'**Explorateur de solutions** et en sélectionnant **Débogage** et **Démarrer une nouvelle instance** dans le menu contextuel.  
  
4.  Démarrez une nouvelle instance du projet **Client** en cliquant avec le bouton droit sur le projet dans l'**Explorateur de solutions** et en sélectionnant **Débogage** et **Démarrer une nouvelle instance** dans le menu contextuel.  
  
5.  Une fois que le service a démarré, appuyez sur ENTRÉE dans la fenêtre du client pour que celui\-ci puisse envoyer un message au service.  
  
6.  Le premier message est traité au niveau du service et le code d'état HTTP OK est renvoyé au client.  
  
7.  Le deuxième message échoue et le code d'état HTTP Erreur interne du serveur est renvoyé au client, ce qui lève une exception <xref:System.ServiceModel.CommunicationException> sur le client.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpAckChannel`