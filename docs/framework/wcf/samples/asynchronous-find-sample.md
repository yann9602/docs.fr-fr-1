---
title: Exemple Asynchronous Find
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a713a25-c1f4-42e1-8c4a-93d64ca45a3b
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a793945906bb1a106916d59ff07ea813f38469d4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="asynchronous-find-sample"></a>Exemple Asynchronous Find
Cet exemple montre comment utiliser l'opération de recherche asynchrone à partir d'une application cliente.  
  
## <a name="sample-details"></a>Détails de l'exemple  
 L'avantage à suivre ce modèle de conception réside dans le fait que le client reçoit une notification asynchrone lorsque la demande de recherche a situé des points de terminaison. Pour en comprendre le fonctionnement, ouvrez le fichier Client.cs. Notez que l'objet <xref:System.ServiceModel.Discovery.DiscoveryClient> a deux délégués attachés à ses gestionnaires d'événements. Un délégué est appelé lorsqu'un événement <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> est déclenché et un autre est appelé chaque fois qu'un événement <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> est déclenché. L'exemple montre comment vous pouvez utiliser ce modèle dans votre application.  
  
> [!NOTE]
>  Cet exemple utilise des points de terminaison HTTP et pour l'exécuter, des listes de contrôle d'accès (ACL) d'URL appropriées doivent être ajoutées. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Configuration de HTTP et HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md). L'exécution de la commande suivante avec un privilège élevé doit ajouter les ACL appropriées. Vous pouvez substituer vos domaine et nom d’utilisateur aux arguments suivants si la commande ne fonctionne pas telle quelle. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  À l'aide de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ouvrez le fichier AsyncFind.sln.  
  
2.  Appuyez sur Ctrl+Maj+B pour générer la solution.  
  
3.  Ouvrez une invite de commandes [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], accédez au répertoire \WCF\Basic\Discovery\AsyncFind\CS\service\bin\Debug ou \WCF\Basic\Discovery\AsyncFind\VB\service\bin\Debug et exécutez Service.exe.  
  
4.  Une fois le service démarré, accédez au répertoire \WCF\Basic\Discovery\AsyncFind\CS\client\bin\Debug ou WCF\Basic\Discovery\AsyncFind\VB\client\bin\Debug et exécutez Client.exe.  
  
5.  Notez que le client est en mesure de trouver et d'appeler le service.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\AsyncFind`  
  
## <a name="see-also"></a>Voir aussi
