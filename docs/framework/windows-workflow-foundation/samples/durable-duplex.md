---
title: "Durable Duplex | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4e76d1a1-f3d8-4a0f-8746-4a322cdff6eb
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Durable Duplex
Cet exemple montre comment installer et configurer un échange de messages duplex durable à l'aide des activités de messagerie dans [!INCLUDE[wf](../../../../includes/wf-md.md)].Un échange de messages duplex durable est un échange de messages bidirectionnel qui a lieu sur une longue période de temps.La durée de vie de l'échange de messages peut être plus longue que la durée de vie du canal de communication et la durée de vie en mémoire des instances de service.  
  
## Détails de l'exemple  
 Dans cet exemple, deux services [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] implémentés à l'aide de [!INCLUDE[wf2](../../../../includes/wf2-md.md)] sont configurés pour avoir un échange de messages duplex durable.L'échange de messages duplex durable est composé de deux messages unidirectionnels envoyés sur MSMQ et mis en corrélation à l'aide de l'échange de contextes .NET décrit dans [.NET Context Exchange](http://go.microsoft.com/fwlink/?LinkID=166059) \(en anglais\).Les messages sont envoyés à l'aide des activités de messagerie <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.Send>.L'échange de contextes .NET est utilisé pour spécifier l'adresse de rappel sur les messages envoyés.Les deux services sont hébergés à l'aide des services d'activation des processus Windows \(WAS, Windows Process Activation Services\) et sont configurés pour activer la persistance des instances de service.  
  
 Le premier service \(Service1.xamlx\) envoie une demande au service d'envoi \(Service2.xamlx\) pour qu'il effectue un travail.Une fois le travail terminé, Service2.xamlx renvoie une notification à Service1.xamlx pour indiquer que le travail a été effectué.Une application console de workflow configure les files d'attente sur lesquelles les services effectuent une écoute et envoie le message de démarrage initial pour activer Service1.xamlx.Une fois que Service1.xamlx reçoit de Service2.xamlx la notification indiquant que le travail demandé a été effectué, il enregistre le résultat dans un fichier XML.En attendant le message de rappel, Service1.xamlx rend l'état de son instance persistant à l'aide du <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> par défaut.Service2.xamlx rend l'état de son instance persistant dans le cadre de l'exécution du travail demandé par Service1.xamlx.  
  
 Pour configurer les services afin d'utiliser l'échange de contextes .NET sur MSMQ, les deux services sont configurés pour utiliser une liaison personnalisée composée de <xref:System.ServiceModel.Channels.ContextBindingElement> et de <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>.Une adresse de rappel, spécifiée avec <xref:System.ServiceModel.Channels.ContextBindingElement>, est incluse dans un en\-tête de contexte de rappel avec tous les messages envoyés à l'aide d'une liaison personnalisée.L'exemple de code suivant définit la liaison personnalisée.  
  
```xml  
<configuration>  
     <system.serviceModel>  
          …  
          <bindings>  
               <customBinding>  
                    <binding name="netMsmqContextBinding">  
                         <context clientCallbackAddress="net.msmq://localhost/private/DurableDuplex/Service1.xamlx"/>  
                         <msmqTransport exactlyOnce="False">  
                              <msmqTransportSecurity msmqAuthenticationMode="None" msmqProtectionLevel="None"/>  
                         </msmqTransport>  
                    </binding>  
               </customBinding>  
          </bindings>  
          …  
     </system.serviceModel>  
</configuration>  
  
```  
  
> [!NOTE]
>  La liaison utilisée par cet exemple n'est pas sécurisée.Lors du déploiement de votre application, vous devez configurer votre liaison en fonction des spécifications de sécurité de votre application.  
  
> [!NOTE]
>  Les files d'attente utilisées dans cet exemple ne sont pas transactionnelles.Pour obtenir un exemple qui montre comment configurer des échanges de messages [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à l'aide de files d'attente de transaction, consultez l'exemple [MSMQ Activation](../../../../docs/framework/wcf/samples/msmq-activation.md).  
  
 L'envoi du message de Service1.xamlx à Service2.xamlx s'effectue à l'aide d'un point de terminaison client configuré avec l'adresse de Service2.xamlx et la liaison personnalisée définie précédemment.Le rappel de Service2.xamlx à Service1.xamlx est envoyé à l'aide d'un point de terminaison client sans adresse explicitement configurée car l'adresse provient du contexte de rappel envoyé par Service1.xamlx.L'exemple de code suivant définit les points de terminaison clients.  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
     <system.serviceModel>  
          …  
          <client>  
               <endpoint address="net.msmq://localhost/private/DurableDuplex/Service2.xamlx" binding="customBinding" bindingConfiguration="netMsmqContextBinding" contract="IDoWork"/>  
               <endpoint binding="customBinding" bindingConfiguration="netMsmqContextBinding" contract="INotify"/>  
          </client>  
          …  
     </system.serviceModel>  
</configuration>  
  
```  
  
 L'exemple de code suivant expose les points de terminaison à l'aide de cette liaison personnalisée en modifiant le mappage de protocole par défaut pour les adresses de base net.msmq afin d'utiliser cette liaison personnalisée.  
  
```  
<configuration>  
     <system.serviceModel>  
          <protocolMapping>  
               <add scheme="net.msmq" binding="customBinding" bindingConfiguration="netMsmqContextBinding"/>  
          </protocolMapping>  
          …  
     </system.serviceModel>  
</configuration>  
  
```  
  
 L'exemple de code suivant active la persistance pour les deux services en ajoutant le comportement <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> aux deux services et en spécifiant la chaîne de connexion pour la base de données de persistance.  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
    <system.serviceModel>  
          …  
          <behaviors>  
               <serviceBehaviors>  
                    <behavior>  
                         <serviceDebug includeExceptionDetailInFaults="True"/>  
                         <serviceMetadata httpGetEnabled="True"/>  
                         <sqlWorkflowInstanceStore connectionString="Data Source=.\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True"/>  
                    </behavior>  
               </serviceBehaviors>  
          </behaviors>  
     </system.serviceModel>  
</configuration>  
  
```  
  
## Configuration requise  
 Cet exemple requiert les composants suivants.  
  
1.  Services Internet \(IIS\)  
  
2.  Services Internet \(IIS\) \-\> Compatibilité avec la gestion IIS 6 \-\> Compatibilité avec la métabase IIS et la configuration IIS 6.  
  
3.  Services World Wide Web \-\> Fonctionnalités de développement d'applications \-\> ASP.NET.  
  
4.  Serveur de mise en file d'attente Microsoft \(MSMQ\).  
  
#### Pour utiliser cet exemple  
  
1.  Configurez la base de données de persistance et le répertoire de résultats.  
  
    1.  Ouvrez une invite de commandes [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
    2.  Accédez au dossier de cet exemple et exécutez Setup.cmd.  
  
2.  Configurez l'application virtuelle.  
  
    1.  À partir d'une invite de commandes [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], inscrivez ASP.NET en exécutant la commande suivante.  
  
        ```  
        aspnet_regiis -i  
        ```  
  
    2.  Exécutez [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] avec des autorisations d'administrateur en cliquant avec le bouton droit sur [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] et en sélectionnant **Exécuter en tant qu'administrateur**.  
  
    3.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier DurableDuplex.sln.  
  
3.  Configurez les files d'attente de service.  
  
    1.  Pour exécuter le client DurableDuplex, appuyez sur F5.  
  
    2.  Ouvrez la console **Gestion de l'ordinateur** en exécutant `Compmgmt.msc` à partir d'une invite de commandes.  
  
    3.  Développez **Services et applications**, **Message Queuing**,**Files d'attente privées**.  
  
    4.  Cliquez avec le bouton droit sur les files d'attente durableduplex\/service1.xamlx et durableduplex\/service2.xamlx, puis sélectionnez **Propriétés**.  
  
    5.  Sélectionnez l'onglet **Sécurité**, puis accordez les autorisations **Recevoir un message**, **Lire le message** et **Envoyer un message** pour les deux files d'attente.  
  
    6.  Ouvrez le Gestionnaire des services Internet \(IIS\).  
  
    7.  Accédez à **Serveur**, **Sites**, **Site Web par défaut**, **Privé**, **Durable Duplex**, puis sélectionnez **Options avancées**.  
  
    8.  Remplacez la valeur de **Protocoles activés** par **http,net.msmq**.  
  
4.  Exécutez l'exemple.  
  
    1.  Accédez à http:\/\/localhost\/private\/durableduplex\/service1.xamlx et http:\/\/localhost\/private\/durableduplex\/service2.xamlx pour vérifier que les deux services sont en cours d'exécution.  
  
    2.  Appuyez sur F5 pour exécuter DurableDuplexClient.  
  
         Lorsque l'échange de messages duplex durable se termine, un fichier result.xml, qui contient le résultat de l'échange de messages, est enregistré dans le dossier C:\\Inbox.  
  
#### Pour effectuer un nettoyage \(facultatif\)  
  
1.  Exécutez Cleanup.cmd.  
  
    1.  Ouvrez une invite de commandes [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
    2.  Accédez au dossier de cet exemple et exécutez Cleanup.cmd.  
  
2.  Supprimez l'application virtuelle pour les services.  
  
    1.  Ouvrez le Gestionnaire des services Internet \(IIS\) en exécutant `Inetmgr.exe` à partir d'une invite de commandes.  
  
    2.  Accédez au site Web par défaut et supprimez le répertoire virtuel **private**.  
  
3.  Supprimez les files d'attente configurées pour cet exemple.  
  
    1.  Ouvrez la console Gestion de l'ordinateur en exécutant `Compmgmt.msc` à partir d'une invite de commandes.  
  
    2.  Développez **Services et applications**, **Message Queuing**, **Files d'attente privées**.  
  
    3.  Supprimez les files d'attente durableduplex\/service1.xamlx et durableduplex\/service2.xamlx.  
  
4.  Supprimez le répertoire C:\\Inbox.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Services\DurableDuplex`  
  
## Voir aussi