---
title: Exemple Announcements
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 954a75e4-9a97-41d6-94fc-43765d4205a9
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 05e2c45b66f92229877ac3ec867da9b71cd4156a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="announcements-sample"></a>Exemple Announcements
Cet exemple montre comment utiliser les fonctionnalités d’annonce de la découverte. Les annonces permettent aux services d'envoyer des messages d'annonce qui contiennent des métadonnées relatives au service. Par défaut, une annonce de type Hello est envoyée lorsque le service démarre et une annonce de type Bye est envoyée lorsque le service s'arrête. Ces annonces peuvent être envoyées en mode multidiffusion ou de point à point. Cet exemple se compose de deux projets : service et client.  
  
## <a name="service"></a>Service  
 Ce projet contient un service de calculatrice auto-hébergé. Dans la méthode `Main`, un hôte de service est créé et un point de terminaison de service lui est ajouté. Ensuite, un <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> est créé. Pour activer les annonces, un point de terminaison d'annonce doit être ajouté au <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>. Dans ce cas, un point de terminaison standard utilisant la multidiffusion UDP est ajouté comme point de terminaison d'annonce. Celui-ci diffuse les annonces sur une adresse UDP bien connue.  
  
```  
Uri baseAddress = new Uri("http://localhost:8000/" + Guid.NewGuid().ToString());  
  
// Create a ServiceHost for the CalculatorService type.  
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))  
{  
     serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new WSHttpBinding(), String.Empty);  
  
     ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();  
  
     // Announce the availability of the service over UDP multicast  
    serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());  
  
    // Make the service discoverable over UDP multicast.  
    serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);                  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    serviceHost.Open();  
    // ...  
}  
```  
  
## <a name="client"></a>Client  
 Dans ce projet, notez que le client héberge un <xref:System.ServiceModel.Discovery.AnnouncementService>. En outre, deux délégués sont inscrits avec les événements. Ces événements déterminent les actions du client lors de la réception d'annonces en ligne et hors connexion.  
  
```  
// Create an AnnouncementService instance  
AnnouncementService announcementService = new AnnouncementService();  
  
// Subscribe the announcement events  
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;  
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;  
```  
  
 Les méthodes `OnOnlineEvent` et `OnOfflineEvent` gèrent respectivement les messages d'annonce de type Hello et Bye.  
  
```  
static void OnOnlineEvent(object sender, AnnouncementEventArgs e)  
{  
    Console.WriteLine();              
    Console.WriteLine("Received an online announcement from {0}:", e.AnnouncementMessage.EndpointDiscoveryMetadata.Address);  
PrintEndpointDiscoveryMetadata(e.AnnouncementMessage.EndpointDiscoveryMetadata);  
}  
  
static void OnOfflineEvent(object sender, AnnouncementEventArgs e)  
{  
    Console.WriteLine();  
    Console.WriteLine("Received an offline announcement from {0}:", e.AnnouncementMessage.EndpointDiscoveryMetadata.Address);  
            PrintEndpointDiscoveryMetadata(e.AnnouncementMessage.EndpointDiscoveryMetadata);  
}  
```  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  Cet exemple utilise des points de terminaison HTTP et pour exécuter cet exemple, bon ACL d’URL doit être ajouté voir [configuration de HTTP et HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) pour plus d’informations. L'exécution de la commande suivante avec un privilège élevé doit ajouter les ACL appropriées. Vous pouvez substituer vos domaine et nom d’utilisateur aux arguments suivants si la commande ne fonctionne pas telle quelle. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  Générez la solution.  
  
3.  Exécutez l'application client.exe.  
  
4.  Exécutez l'application service.exe. Notez que le client reçoit une annonce en ligne.  
  
5.  Fermez l'application service.exe. Notez que le client reçoit une annonce hors connexion.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Announcements`  
  
## <a name="see-also"></a>Voir aussi
