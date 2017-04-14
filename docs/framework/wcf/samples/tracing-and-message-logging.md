---
title: "Tracing and Message Logging | Microsoft Docs"
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
  - "suivi et journalisation"
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
caps.latest.revision: 53
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 53
---
# Tracing and Message Logging
Cet exemple illustre comment activer l'enregistrement des suivis et des messages.Les journaux de suivis et de messages ainsi obtenus peuvent être affichés à l'aide de l'outil [Service Trace Viewer Tool \(SvcTraceViewer.exe\)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).Cet exemple est basé sur [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent en fin de rubrique.  
  
## Suivi  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] utilise le mécanisme de suivi défini dans l'espace de noms <xref:System.Diagnostics>.Dans ce modèle de suivi, les données de suivi sont générées par les sources de suivi implémentées par les applications.Chacune de ces sources est identifiée à l'aide d'un nom.Les consommateurs de suivis créent des écouteurs pour les sources de suivi à partir desquelles ils souhaitent récupérer des informations.Pour recevoir des données de suivi d'une source, vous devez créer un écouteur pour cette source.Dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], l'une des solutions pour ce faire consiste à ajouter le code suivant au fichier de configuration du service ou du client en définissant la source de suivi du modèle de service `switchValue` :  
  
```  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-service.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>  
```  
  
 Pour plus d'informations sur les sources de suivi, consultez la section Source de suivi dans la rubrique [Configuration du suivi](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).  
  
## Suivi et propagation d'activité  
 L'activation de `ActivityTracing` et l'affectation de la valeur `true` à `propagateActivity`  dans les sources de suivi `system.ServiceModel` du client et du service permettent de mettre en relation les suivis des unités logiques de traitement \(activités\), les suivis des activités propres à chaque point de terminaison \(via le transfert des activités\) et les suivis des activités impliquant plusieurs points de terminaison \(via la propagation des ID d'activité\).  
  
 Ces trois mécanismes \(activités, transfert et propagation\) peuvent vous permettre de localiser plus facilement la cause première d'une erreur, notamment en utilisant l'outil Service Trace Viewer.Pour plus d'informations, consultez [Utilisation de Service Trace Viewer pour afficher les suivis corrélés et résoudre les problèmes](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
 Il est possible d'étendre le suivi fourni par le ServiceModel en créant des suivis d'activité définis par l'utilisateur.Les suivis d'activité définis par l'utilisateur permettent :  
  
-   De regrouper les suivis dans des unités logiques de travail.  
  
-   De mettre en relation les activités à l'aide du transfert et de la propagation.  
  
-   D'atténuer les pertes en termes de performances du suivi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] \(par exemple, de diminuer l'espace disque occupé par le stockage des journaux\).  
  
 Pour plus d'informations sur les suivis d'activité définis par l'utilisateur, consultez l'exemple [Extending Tracing](../../../../docs/framework/wcf/samples/extending-tracing.md).  
  
## Enregistrement des messages  
 L'enregistrement des messages peut être activé à la fois sur le client et le service de toute application [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].Pour activer l'enregistrement des messages, vous devez ajouter le code suivant au client ou au service :  
  
```  
<configuration>  
  <system.serviceModel>  
    <diagnostics>  
      <!-- Enable Message Logging here. -->  
      <!-- log all messages received or sent at the transport or service model levels >  
      <messageLogging logEntireMessage="true"  
                      maxMessagesToLog="300"  
                      logMessagesAtServiceLevel="true"  
                      logMalformedMessages="true"  
                      logMessagesAtTransportLevel="true" />  
    </diagnostics>  
  </system.serviceModel>  
</configuration>  
```  
  
 Lorsqu'un message est enregistré, le type de suivi généré pour ce message n'est pas le même si ce message est suivi au niveau du client ou du serveur.Par exemple, le suivi du message « Add » est assuré dans la catégorie « TransportWrite », au niveau du client alors que son suivi est assuré dans la catégorie « TransportRead », au niveau du service.  
  
 Configurez l'écouteur de suivi en ajoutant le code suivant à la section <xref:System.Diagnostics> du fichier App.config du client ou du fichier Web.config du service :  
  
```  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-client.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
  </system.diagnostics>  
```  
  
 Les messages sont enregistrés au format XML dans le fichier de configuration stocké dans le répertoire cible spécifié.  
  
> [!NOTE]
>  Les fichiers de suivi ne peuvent pas être créés si un répertoire de journal n'est pas créé auparavant.Assurez\-vous que le répertoire C:\\logs\\ existe ou définissez un autre répertoire d'enregistrement dans la configuration de l'écouteur.Consultez les instructions initiales de configuration figurant en fin de rubrique pour plus d'informations.  
  
 Pour plus d'informations sur l'enregistrement des messages, consultez la rubrique [Configuration de la journalisation des messages](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md).  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez\-vous d'avoir effectué la procédure figurant à la section [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Avant d'exécuter l'exemple Tracing and Message Logging, créez le répertoire C:\\logs\\ dans lequel le service stockera les fichiers .svclog.Le nom de ce répertoire est défini dans le fichier de configuration sous la forme d'un chemin d'accès indiquant où les suivis et les messages doivent être enregistrés. Ce chemin peut être modifié.Accordez à l'utilisateur des droits d'accès en écriture de service réseau au répertoire des journaux.  
  
3.  Pour générer l'édition C\#, C\+\+ ou Visual Basic .NET de la solution, conformez\-vous aux instructions figurant dans la rubrique [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, conformez\-vous aux instructions figurant dans [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## Voir aussi  
 [Suivi](../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [Exemples d'analyse AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)