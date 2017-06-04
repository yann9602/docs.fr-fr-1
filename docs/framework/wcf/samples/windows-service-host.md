---
title: "Windows Service Host | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Service Windows NT"
  - "NT Service Host (exemple) (Windows Communication Foundation)"
ms.assetid: 1b2f45c5-2bed-4979-b0ee-8f9efcfec028
caps.latest.revision: 40
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 40
---
# Windows Service Host
Cet exemple montre un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hébergé dans un service Windows managé.Les services Windows sont contrôlés à l'aide de l'applet Services du **Panneau de configuration** et peuvent être configurés pour démarrer automatiquement après un redémarrage du système.L'exemple se compose d'un programme client et d'un programme de service Windows.Le service est implémenté en tant que programme .exe et contient son propre code d'hébergement.Dans d'autres environnements d'hébergement, tels que WAS \(Windows Process Activation Services\) ou IIS \(Internet Information Services\), vous n'avez pas besoin d'écrire le code d'hébergement.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WindowsService`  
  
 Après avoir généré ce service, il doit être installé avec l'utilitaire Installutil.exe comme tout autre service Windows.Si vous voulez apporter des modifications au service, vous devez d'abord le désinstaller avec `installutil /u`.Les fichiers Setup.bat et Cleanup.bat inclus dans cet exemple sont les commandes pour installer et démarrer le service Windows, et pour fermer et désinstaller le service Windows.Le service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peut répondre aux clients uniquement si le service Windows est en cours d'exécution.Si vous arrêtez le service Windows en utilisant l'applet Services du **Panneau de configuration** et si vous exécutez le client, une exception <xref:System.ServiceModel.EndpointNotFoundException> est levée lorsqu'un client essaie d'accéder au service.Si vous redémarrez le service Windows et exécutez à nouveau le client, la communication réussit.  
  
 Le code de service inclut une classe Installer, une classe d'implémentation de service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui implémente le contrat ICalculator, et une classe de service Windows qui agit l'hôte d'exécution.La classe Installer, qui hérite de <xref:System.Configuration.Install.Installer>, permet à l'outil Installutil.exe d'installer le programme comme un service NT.La classe d'implémentation du service, `WcfCalculatorService`, est un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui implémente un contrat de service de base.Ce service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est hébergé dans une classe de service Windows appelée `WindowsCalculatorService`.Pour prétendre au titre de service Windows, la classe hérite de <xref:System.ServiceProcess.ServiceBase> et implémente les méthodes [OnStart\(String\<xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> et <xref:System.ServiceProcess.ServiceBase.OnStop>.Dans [OnStart\(String\<xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>, un objet <xref:System.ServiceModel.ServiceHost> est créé pour le type `WcfCalculatorService` et ouvert.Dans <xref:System.ServiceProcess.ServiceBase.OnStop>, le ServiceHost est fermé en appelant la méthode <xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> de l'objet <xref:System.ServiceModel.ServiceHost>.L'adresse de base de l'hôte est configurée à l'aide de l'élément [\<ajouter\>](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md), qui est un enfant de [\<baseAddresses\>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), qui est un enfant de l'élément [\<hôte\>](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), qui est un enfant de l'élément [\<service\>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md).  
  
 Le point de terminaison défini utilise l'adresse de base et un [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).L'exemple suivant illustre la configuration de l'adresse de base ainsi que le point de terminaison qui expose le CalculatorService.  
  
```  
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
  
 Lorsque vous exécutez l'exemple, les requêtes et réponses de l'opération s'affichent dans les fenêtres de console du service et du client.Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client.  
  
### Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez\-vous d'avoir effectué la procédure indiquée à la section [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l'édition C\# ou Visual Basic .NET de la solution, conformez\-vous aux instructions figurant dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Après avoir généré la solution, exécutez Setup.bat à partir d'une invite de commandes de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] de niveau élevé pour installer le service Windows à l'aide de l'outil Installutil.exe.Le service doit apparaître dans Services.  
  
4.  Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, conformez\-vous aux instructions figurant dans [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## Voir aussi  
 [Hébergement AppFabric et exemples de persistance](http://go.microsoft.com/fwlink/?LinkId=193961)