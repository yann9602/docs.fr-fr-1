---
title: Windows Service Host
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- NT Service
- NT Service Host Sample [Windows Communication Foundation]
ms.assetid: 1b2f45c5-2bed-4979-b0ee-8f9efcfec028
caps.latest.revision: "40"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e3dd2b4880ea61f5c3236a3e15ba1c939dbc2952
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="windows-service-host"></a>Windows Service Host
Cet exemple montre un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hébergé dans un service Windows managé. Services Windows sont contrôlés à l’aide de l’applet Services **le panneau de configuration** et peut être configuré pour démarrer automatiquement après un redémarrage du système. L'exemple se compose d'un programme client et d'un programme de service Windows. Le service est implémenté en tant que programme .exe et contient son propre code d'hébergement. Dans d'autres environnements d'hébergement, tels que WAS (Windows Process Activation Services) ou IIS (Internet Information Services), vous n'avez pas besoin d'écrire le code d'hébergement.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WindowsService`  
  
 Après avoir généré ce service, il doit être installé avec l'utilitaire Installutil.exe comme tout autre service Windows. Si vous voulez apporter des modifications au service, vous devez d'abord le désinstaller avec `installutil /u`. Les fichiers Setup.bat et Cleanup.bat inclus dans cet exemple sont les commandes pour installer et démarrer le service Windows, et pour fermer et désinstaller le service Windows. Le service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peut répondre aux clients uniquement si le service Windows est en cours d'exécution. Si vous arrêtez le Service Windows à l’aide de l’applet Services du **le panneau de configuration** et exécutez le client, un <xref:System.ServiceModel.EndpointNotFoundException> exception se produit lorsqu’un client tente d’accéder au service. Si vous redémarrez le service Windows et exécutez à nouveau le client, la communication réussit.  
  
 Le code de service inclut une classe Installer, une classe d'implémentation de service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui implémente le contrat ICalculator, et une classe de service Windows qui agit l'hôte d'exécution. La classe Installer, qui hérite de <xref:System.Configuration.Install.Installer>, permet à l'outil Installutil.exe d'installer le programme comme un service NT. La classe d'implémentation du service, `WcfCalculatorService`, est un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui implémente un contrat de service de base. Ce service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est hébergé dans une classe de service Windows appelée `WindowsCalculatorService`. Pour prétendre au titre de service Windows, la classe hérite de <xref:System.ServiceProcess.ServiceBase> et implémente les méthodes <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> et <xref:System.ServiceProcess.ServiceBase.OnStop>. Dans <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>, un objet <xref:System.ServiceModel.ServiceHost> est créé pour le type `WcfCalculatorService` et ouvert. Dans <xref:System.ServiceProcess.ServiceBase.OnStop>, le ServiceHost est fermé en appelant la méthode <xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> de l'objet <xref:System.ServiceModel.ServiceHost>. Adresse de base de l’ordinateur hôte est configuré à l’aide de la [ \<Ajouter >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md) élément, qui est un enfant de [ \<baseAddresses >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), qui est un enfant de la [ \<hôte >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) élément, qui est un enfant de la [ \<service >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) élément.  
  
 Le point de terminaison est définie utilise l’adresse de base et un [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). L'exemple suivant illustre la configuration de l'adresse de base ainsi que le point de terminaison qui expose le CalculatorService.  
  
```xml  
<services>  
  <service name="Microsoft.ServiceModel.Samples.WcfCalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    <host>  
      <baseAddresses>  
        <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
      </baseAddresses>  
    </host>  
    <!-- This endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service.  -->  
    <endpoint address=""  
              binding="wsHttpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    ...  
  </service>  
</services>  
```  
  
 Lorsque vous exécutez l'exemple, les requêtes et réponses de l'opération s'affichent dans les fenêtres de console du service et du client. Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Après avoir généré la solution, exécutez Setup.bat à partir d'une invite de commandes de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] de niveau élevé pour installer le service Windows à l'aide de l'outil Installutil.exe. Le service doit apparaître dans Services.  
  
4.  Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Hébergement de AppFabric et exemples de persistance](http://go.microsoft.com/fwlink/?LinkId=193961)
