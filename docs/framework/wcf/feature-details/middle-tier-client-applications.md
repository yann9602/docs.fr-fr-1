---
title: "Applications clientes de niveau intermédiaire"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f9714a64-d0ae-4a98-bca0-5d370fdbd631
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b73641fcbc881e57465f722d3a0f647938a5e12e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="middle-tier-client-applications"></a>Applications clientes de niveau intermédiaire
Cette rubrique traite des différents problèmes spécifiques aux applications clientes de niveau intermédiaire qui utilisent [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
## <a name="increasing-middle-tier-client-performance"></a>Augmenter les performances du client de niveau intermédiaire  
 Comparée aux technologies de communications précédentes, telles que les services Web qui utilisent [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], la création d'une instance cliente [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peut être plus complexe en raison du grand nombre de fonctionnalités [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Par exemple, lorsqu'un objet <xref:System.ServiceModel.ChannelFactory%601> est ouvert, il peut établir une session sécurisée avec le service, procédure qui augmente le temps de démarrage pour l'instance cliente. En général, ces fonctionnalités supplémentaires affectent peu les applications clientes étant donné que le client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] effectue plusieurs appels, puis se ferme.  
  
 Cependant, les applications clientes de niveau intermédiaire peuvent créer rapidement de nombreux objets clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et, en conséquence, nécessitent des spécifications d'initialisation plus nombreuses. Il existe deux approches principales pour accroître les performances des applications de niveau intermédiaire lors d'un appel des services :  
  
-   Mettre en cache l'objet client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et le réutiliser pour les appels suivants le cas échéant.  
  
-   Créer un objet <xref:System.ServiceModel.ChannelFactory%601> puis l'utiliser pour créer des nouveaux objets de canal de client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour chaque appel.  
  
 Les problèmes à prendre en compte lors de l'utilisation de ces approches sont les suivants :  
  
-   Si le service maintient un état spécifique au client en utilisant une session, vous ne pouvez pas réutiliser le client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de niveau intermédiaire avec des demandes au niveau de plusieurs clients parce que l'état du service est lié à celui du client de niveau intermédiaire.  
  
-   Si le service doit exécuter l'authentification sur la base de chaque client, vous devez créer un client pour chaque requête entrante sur le niveau intermédiaire au lieu de réutiliser le client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de niveau intermédiaire (ou l'objet de canal de client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]) parce que les informations d'identification du client du niveau intermédiaire ne peuvent pas être modifiées après la création du client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] (ou de <xref:System.ServiceModel.ChannelFactory%601>).  
  
-   Si les canaux et les clients créés par les canaux sont thread-safe, ils peuvent ne pas prendre en charge l'écriture simultanée de plusieurs messages sur la transmission. Si vous envoyez des messages volumineux, notamment pour la diffusion en continu, l'opération d'envoi peut bloquer l'exécution d'une autre opération d'envoi. Cette situation entraîne deux types de problèmes : un manque d'accès concurrentiel et le risque d'interblocage si le flux de contrôle retourne au service par l'intermédiaire du canal (autrement dit, le client partagé appelle un service dont le chemin d'accès au code entraîne un rappel au client partagé). Cela est vrai indépendamment du type de client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] que vous réutilisez.  
  
-   Vous devez traiter les canaux défaillants, que vous partagiez ou non le canal. Toutefois, lorsque les canaux sont réutilisés, un canal défaillant peut faire échouer plusieurs opérations de demande ou d'envoi en attente.  
  
 Pour obtenir un exemple qui illustre les meilleures pratiques pour la réutilisation d’un client pour plusieurs requêtes, consultez [une liaison de données dans un Client ASP.NET](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md).  
  
 De plus, vous pouvez augmenter les performances de démarrage pour les clients qui utilisent des types de données sérialisables à l'aide de <xref:System.Xml.Serialization.XmlSerializer> pour générer et compiler le code de sérialisation pour ces types de données au moment de l'exécution qui peuvent ralentir les performances de démarrage. Le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) peut améliorer les performances de démarrage de ces applications en générant le code de sérialisation nécessaires à partir des assemblys compilés pour l’application. Pour plus d’informations, consultez [Comment : améliorer le démarrage du temps des Applications clientes WCF à l’aide de XmlSerializer](../../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Accès aux services à l’aide d’un client WCF](../../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md)
