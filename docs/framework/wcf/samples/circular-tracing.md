---
title: Circular Tracing
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
caps.latest.revision: "21"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0b86867793424d6d0b42a18d6a2fbd6175bc1a47
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="circular-tracing"></a>Circular Tracing
Cet exemple montre l'implémentation d'un écouteur de suivis mis en mémoire tampon circulaire. L'un des scénarios courants pour les services de production consiste à disposer de services disponibles pendant de longues périodes et à activer la journalisation du suivi à un faible niveau. Ces services consomment beaucoup d'espace disque. Lors du dépannage d'un service, les données les plus récentes du journal de suivi s'avèrent pertinentes pour la résolution d'un problème. Cet exemple présente l'implémentation d'un écouteur de suivis mis en mémoire tampon circulaire dans lequel seules les suivis les plus récents sont conservés sur le disque jusqu'à un nombre de donnés configurable. Cet exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md) et inclut un écouteur de suivi personnalisé.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Cet exemple part du principe que vous êtes familiarisé avec les [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) exemple et avoir lu la documentation fournie pour le [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) exemple.  
  
## <a name="circular-buffer-trace-listener"></a>Écouteur de suivis mis en mémoire tampon circulaire  
 Le concept sous-jacent de l'implémentation de l'écouteur de suivis mis en mémoire tampon circulaire consiste à disposer de deux fichiers pouvant stocker chacun jusqu'à la moitié du nombre total de données du journal de suivi souhaitées. L'écouteur crée un fichier et écrit dans celui-ci jusqu'à ce qu'il atteigne la limite fixée à la moitié de la taille des données, stade à partir duquel il bascule sur un deuxième fichier. Lorsque l'écouteur atteint la limite pour deuxième fichier il écrase le premier fichier avec de nouveaux suivis.  
  
 Cet écouteur dérive le `XmlWriteTraceListener` et autorise les journaux à afficher avec le [outil Service Trace Viewer (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Si vous souhaitez consulter les journaux, vous pouvez recombiner les deux fichiers journaux facilement en les ouvrant en même temps dans l'outil Service Trace Viewer. Cet outil trie automatiquement les suivis afin qu'ils apparaissent dans l'ordre correct.  
  
## <a name="configuration"></a>Configuration  
 Un service peut être configuré pour utiliser l'écouteur de suivis mis en mémoire tampon circulaire en ajoutant le code suivant pour un écouteur et des éléments sources. La taille de fichier maximale est spécifiée à l'aide de l'attribut `maxFileSizeKB` dans la configuration de l'écouteur de suivis circulaire. Cela est illustré dans le code suivant :  
  
```xml  
<system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel" switchValue="Information,ActivityTracing" propagateActivity="true">  
      <listeners>  
        <add name="CircularTraceListener" />  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="CircularTraceListener" type="Microsoft. Samples.ServiceModel.CircularTraceListener,CircularTraceListener"   
         initializeData="c:\logs\CircularTracing-service.svclog" maxFileSizeKB="100" />  
  </sharedListeners>  
  <trace autoflush="true" />  
</system.diagnostics>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Vérifiez que vous avez effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples d’analyse AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
