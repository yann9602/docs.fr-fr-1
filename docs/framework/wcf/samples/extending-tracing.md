---
title: "Extending Tracing | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
caps.latest.revision: 28
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 28
---
# Extending Tracing
Cet exemple montre comment étendre la fonctionnalité de suivi [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] en écrivant les suivis de l'activité définie par l'utilisateur dans le code du client et du service.Cela permet à l'utilisateur de créer des activités de suivi et de regrouper les suivis dans des unités de travail logiques.Il est également possible de mettre en corrélation des activités à travers des transferts \(au sein du même point de terminaison\) et la propagation \(sur plusieurs points de terminaison\).Dans cet exemple, le suivi est activé à la fois pour le client et pour le service.Pour plus d'informations sur l'activation du suivi dans les fichiers de configuration du client et du service, consultez [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).  
  
 Cet exemple est basé sur [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## Suivi et propagation d'activité  
 Le suivi d'activité défini par l'utilisateur permet à l'utilisateur de créer ses propres activités de suivi pour regrouper les suivis dans les unités de travail logiques, mettre en corrélation des activités par transfert et propagation et amoindrir les coûts de performance du suivi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] \(le coût en espace disque d'un fichier journal, par exemple\).  
  
### Ajout de sources personnalisées  
 Les suivis définis par l'utilisateur peuvent être ajoutés à la fois au code du client et du service.L'ajout de sources de suivi aux fichiers de configuration du client ou du service permet l'enregistrement et l'affichage de ces suivis personnalisés dans l'[Service Trace Viewer Tool \(SvcTraceViewer.exe\)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).Le code suivant montre comment ajouter une source de suivi définie par l'utilisateur nommée `ServerCalculatorTraceSource` au fichier de configuration.  
  
```  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
        <source name="ServerCalculatorTraceSource" switchValue="Information,ActivityTracing">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
       <add initializeData="C:\logs\ServerTraces.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" traceOutputOptions="Callstack">  
            <filter type="" />  
        </add>  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>....  
....  
```  
  
### Mise en corrélation des activités  
 Pour mettre directement en corrélation des activités sur plusieurs points de terminaison, l'attribut `propagateActivity` doit avoir la valeur `true` dans la source du suivi `System.ServiceModel`.En outre, le suivi d'activité ServiceModel doit être désactivé pour propager des suivis sans traverser des activités [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].C'est ce qu'illustre l'exemple de code suivant.  
  
> [!NOTE]
>  La désactivation du suivi d'activité ServiceModel n'équivaut pas à désactiver le niveau de suivi, dénoté par la propriété `switchValue`.  
  
```  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### Réduction des coûts de performance  
 Le fait de désactiver `ActivityTracing` dans la source de suivi `System.ServiceModel` génère un fichier de suivi qui contient uniquement les suivis d'activité définis par l'utilisateur, sans inclure les suivis d'activité ServiceModel.Ainsi, le fichier journal est beaucoup moins volumineux.Toutefois, la possibilité de mettre en corrélation les suivis de traitement [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est perdue.  
  
##### Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez\-vous d'avoir effectué la procédure figurant à la section [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l'édition C\# ou Visual Basic .NET de la solution, conformez\-vous aux instructions figurant dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, conformez\-vous aux instructions figurant dans [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## Voir aussi  
 [Exemples d'analyse AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)