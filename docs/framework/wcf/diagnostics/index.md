---
title: "Administration et diagnostics | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "administration (WCF)"
  - "diagnostics (WCF)"
  - "WCF, administration"
  - "WCF, diagnostics"
  - "Windows Communication Foundation, administration"
  - "Windows Communication Foundation, diagnostics"
ms.assetid: 34c81c08-0e0f-4fbc-9ae8-91948640ee43
caps.latest.revision: 19
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 19
---
# Administration et diagnostics
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] fournit un jeu complet de fonctionnalités vous permettant de surveiller les différentes étapes du cycle de vie d'une application.Par exemple, vous pouvez utiliser la configuration pour installer les services et les clients lors du déploiement.[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inclut un jeu important de compteurs de performance pour vous aider à mesurer les performances de votre application.[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] expose également au moment de l'exécution les données d'inspection d'un service par l'intermédiaire d'un fournisseur WMI \(Windows Management Instrumentation\) de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].En cas de défaillance ou de fonctionnement incorrect de l'application, vous pouvez utiliser le journal des événements afin de vérifier si un événement significatif s'est produit.Vous pouvez également utiliser la journalisation des messages et le suivi pour afficher les événements qui se produisent sur l'ensemble de votre application.Ces fonctionnalités permettent aux développeurs et aux professionnels de l'informatique de dépanner une application [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] lorsque celle\-ci ne se comporte pas correctement.  
  
> [!NOTE]
>  Si vous recevez des erreurs sans informations détaillées spécifiques, vous devez activer l'attribut `includeExceptionDetailInFaults` de l'élément de configuration [\<serviceDebug\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md).Cette opération indique à [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] d'envoyer des informations d'exception aux clients, ce qui vous permet de détecter un grand nombre de problèmes courants sans nécessiter un diagnostic plus élaboré.Pour plus d'informations, consultez [Envoi et réception des erreurs](../../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
## Fonctionnalités de diagnostic fournies par WCF  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit les fonctionnalités de diagnostic suivantes :  
  
-   Le suivi de bout en bout fournit les données d'instrumentation permettant de dépanner une application sans utiliser de débogueur.[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génère des suivis pour les jalons de processus, ainsi que des messages d'erreur.Cela peut inclure l'ouverture d'une fabrication de canal ou l'envoi et la réception de messages par un hôte de service.Le suivi peut être activé pour une application en cours d'exécution afin de surveiller sa progression.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)], la rubrique [Suivi](../../../../docs/framework/wcf/diagnostics/tracing/index.md).Pour comprendre de quelle manière le suivi vous permet de déboguer votre application, consultez la rubrique « [Utilisation du suivi pour résoudre les problèmes posés par votre application](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md) ».  
  
-   La journalisation des messages vous permet de voir la manière dont les messages se présentent à la fois avant et après la transmission.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)], la rubrique [Enregistrement des messages](../../../../docs/framework/wcf/diagnostics/message-logging.md).  
  
-   En cas de problèmes majeurs, le suivi écrit les événements dans le journal.L'observateur d'événements vous permet ensuite d'examiner les anomalies.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)], la rubrique [Journalisation des événements](../../../../docs/framework/wcf/diagnostics/event-logging/index.md).  
  
-   Les compteurs de performance exposés via l'analyseur de performances vous permettent de surveiller l'état de votre application et de votre système.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)], la rubrique [Compteurs de performance](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md).  
  
-   L'espace de noms <xref:System.ServiceModel.Configuration> vous permet de charger des fichiers de configuration et de configurer un point de terminaison de service ou client.Vous pouvez utiliser le modèle objet pour modifier de nombreuses applications lorsque des mises à jour doivent être déployées sur un grand nombre d'ordinateurs.Vous pouvez également utiliser [Outil Éditeur de configuration \(SvcConfigEditor.exe\)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) pour modifier les paramètres de configuration à l'aide d'un Assistant GUI.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)], la rubrique [Configuration de votre application](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md).  
  
-   WMI vous permet d'identifier les services qui écoutent sur une machine, ainsi que les liaisons utilisées.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)], la rubrique [Utilisation de Windows Management Instrumentation pour les diagnostics](../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit également plusieurs interfaces GUI et outils de ligne de commande qui facilitent la création, le déploiement et la gestion des applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Outils de Windows Communication Foundation](../../../../docs/framework/wcf/tools.md).Par exemple, vous pouvez utiliser [Outil Éditeur de configuration \(SvcConfigEditor.exe\)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) pour créer et modifier des paramètres de configuration [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à l'aide d'un assistant, au lieu de modifier XML directement.Par ailleurs, l'[Service Trace Viewer Tool \(SvcTraceViewer.exe\)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) vous permet d'afficher, de regrouper et de filtrer des messages de suivi afin de diagnostiquer, réparer et vérifier les problèmes liés aux services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## Voir aussi  
 [Configuration de votre application](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)   
 [Déploiement de services](../../../../docs/framework/wcf/diagnostics/deploying-services.md)   
 [Référence des exceptions](../../../../docs/framework/wcf/diagnostics/exceptions-reference/index.md)   
 [Journalisation des événements](../../../../docs/framework/wcf/diagnostics/event-logging/index.md)   
 [Enregistrement des messages](../../../../docs/framework/wcf/diagnostics/message-logging.md)   
 [Outil Éditeur de configuration \(SvcConfigEditor.exe\)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)   
 [Service Trace Viewer Tool \(SvcTraceViewer.exe\)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)   
 [Outil d'inscription ServiceModel](../../../../docs/framework/wcf/diagnostics/servicemodel-registration-tool.md)   
 [Suivi](../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [Utilisation de Windows Management Instrumentation pour les diagnostics](../../../../docs/framework/wcf/diagnostics/wmi/index.md)   
 [Compteurs de performance](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)   
 [Outils de Windows Communication Foundation](../../../../docs/framework/wcf/tools.md)