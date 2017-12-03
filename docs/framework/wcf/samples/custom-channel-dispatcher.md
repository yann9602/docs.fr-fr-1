---
title: Custom Channel Dispatcher
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 813acf03-9661-4d57-a3c7-eeab497321c6
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 81512576e1d26b63cf65b3a0c9992c2d273d2779
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="custom-channel-dispatcher"></a>Custom Channel Dispatcher
Cet exemple montre comment générer la pile de canaux de façon personnalisée en implémentant <xref:System.ServiceModel.ServiceHostBase> directement et comment créer un répartiteur de canal personnalisé dans un environnement avec hôte Web. Le répartiteur de canal interagit avec <xref:System.ServiceModel.Channels.IChannelListener> pour accepter des canaux et récupère des messages de la pile de canaux. Cet exemple fournit également un exemple de base pour montrer comment construire une pile de canaux dans un environnement avec hôte Web à l'aide de <xref:System.ServiceModel.Activation.VirtualPathExtension>.  
  
## <a name="custom-servicehostbase"></a>Custom ServiceHostBase  
 Cet exemple implémente le type de base <xref:System.ServiceModel.ServiceHostBase> au lieu de <xref:System.ServiceModel.ServiceHost> pour montrer comment remplacer l'implémentation de pile [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] par une couche personnalisée de gestion des messages en plus de la pile de canaux. Vous devez substituer la méthode virtuelle <xref:System.ServiceModel.ServiceHostBase.InitializeRuntime%2A> pour générer des écouteurs de canal et le répartiteur de canal.  
  
 Pour implémenter un service hébergé sur le Web, obtenez l'extension de service <xref:System.ServiceModel.Activation.VirtualPathExtension> de la collection <xref:System.ServiceModel.ServiceHostBase.Extensions%2A> et ajoutez-la au <xref:System.ServiceModel.Channels.BindingParameterCollection> afin que la couche transport sache comment configurer l'écouteur de canal selon les paramètres de l'environnement d'hébergement, à savoir, les paramètres Internet Information Services (IIS) et ceux du service d'activation des processus Windows (WAS).  
  
## <a name="custom-channel-dispatcher"></a>Custom Channel Dispatcher  
 Le répartiteur de canal personnalisé étend le type <xref:System.ServiceModel.Dispatcher.ChannelDispatcherBase>. Ce type implémente la logique de programmation de la couche du canal. Dans cet exemple, seul <xref:System.ServiceModel.Channels.IReplyChannel> est pris en charge pour le modèle d'échange de messages demande/réponse, mais le répartiteur de canal personnalisé peut facilement être étendu à d'autres types de canaux.  
  
 Le répartiteur ouvre d'abord l'écouteur de canal, puis accepte le canal de réponse singleton. Avec le canal, il commence à envoyer des messages (demandes) dans une boucle infinie. Pour chaque demande, il crée un message de réponse qu'il renvoie au client.  
  
## <a name="creating-a-response-message"></a>Création d'un message de réponse  
 Le traitement des messages est implémenté dans le type `MyServiceManager`. Dans la méthode `HandleRequest`, l'en-tête `Action` du message est vérifié en premier pour voir si la demande est prise en charge. Une action SOAP prédéfinie « http://tempuri.org/HelloWorld/Hello » est définie pour assurer le filtrage des messages. Ce concept est similaire à celui du contrat de service dans l'implémentation [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de <xref:System.ServiceModel.ServiceHost>.  
  
 Pour le cas de l'action SOAP appropriée, l'exemple récupère les données de message demandées et génère une réponse correspondante à la demande similaire à celle du cas <xref:System.ServiceModel.ServiceHost>.  
  
 Vous avez géré le verbe HTTP-GET de manière spéciale en retournant un message HTML personnalisé dans ce cas, aussi pouvez-vous parcourir le service à partir d'un navigateur et vérifier qu'il est correctement compilé. Si l'action SOAP ne correspond pas, renvoyez un message d'erreur pour indiquer que la demande n'est pas prise en charge.  
  
 Le client de cet exemple est un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] normal qui n'effectue aucune supposition relativement au service. Le service est donc conçu spécialement pour correspondre à ce que vous obtenez d'une implémentation [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] normale de <xref:System.ServiceModel.ServiceHost>. Par conséquent, seul un contrat de service est obligatoire sur le client.  
  
## <a name="using-the-sample"></a>Utilisation de l'exemple  
 L'exécution de l'application cliente produit directement la sortie suivante.  
  
```Output  
Client is talking to a request/reply WCF service.   
Type what you want to say to the server: Howdy  
Server replied: You said: Howdy. Message id: 1  
Server replied: You said: Howdy. Message id: 2  
Server replied: You said: Howdy. Message id: 3  
Server replied: You said: Howdy. Message id: 4  
Server replied: You said: Howdy. Message id: 5  
```  
  
 Vous pouvez également parcourir le service à partir d'un navigateur afin qu'un message HTTP-GET soit traité sur le serveur. Vous obtenez un texte HTML correctement mis en forme.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\CustomChannelDispatcher`
