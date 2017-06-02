---
title: "AJAX Service Without Configuration | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
caps.latest.revision: 23
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 23
---
# AJAX Service Without Configuration
Cet exemple illustre comment utiliser [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pour créer un service de base ASP.NET AJAX \(Asynchronous JavaScript and XML\), c'est\-à\-dire un service auquel vous pouvez accéder en utilisant un code Javascript depuis un client de navigateur Web sans recourir à des paramètres de configuration.  Le service utilise une syntaxe spéciale dans le fichier .svc pour activer automatiquement un point de terminaison AJAX.  
  
 La prise en charge d'AJAX dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est optimisée pour permettre son utilisation avec ASP.NET AJAX via le contrôle `ScriptManager`.  Pour obtenir un exemple d'utilisation de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] avec ASP.NET AJAX, consultez [Ajax Samples](http://msdn.microsoft.com/fr-fr/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Cet exemple est basé sur le service AJAX Service utilisant HTTP POST.  Comme décrit dans l'exemple [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md), <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> est utilisé pour héberger le service.  
  
```  
<%ServiceHost  
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CalculatorService  
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"  
%>  
  
```  
  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ajoute automatiquement un <xref:System.ServiceModel.Description.WebScriptEndpoint> au service.  Si aucune modification de configuration ne doit être apportée au point de terminaison, la section \<system.ServiceModel\> peut être supprimée complètement du fichier Web.config pour le service.  Le fichier Web.config contient des paramètres ASP.NET, qui sont utilisés par ConfigFreeClientPage.aspx.  Si ce n'était pas le cas, l'intégralité du fichier Web.config pourrait être supprimée.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.  Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, accédez à la page des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].  Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez\-vous d'avoir suivi les instructions d'installation de la section [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Générez la solution ConfigFreeAjaxService.sln tel qu'indiqué dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Accédez à http:\/\/localhost\/ServiceModelSamples\/ConfigFreeClientPage.aspx \(n'ouvrez pas le fichier ConfigFreeClientPage.aspx dans le navigateur à partir du répertoire de projet\).  
  
> [!NOTE]
>  Avant d'exécuter cet exemple, assurez\-vous que l'authentification anonyme et que l'authentification Windows ne sont pas toutes deux activées dans le dossier ServiceModelSamples des services IIS.  Si tel est le cas, désactivez l'authentification Windows.  Une fois que vous avez exécuté l'exemple, activez l'authentification Windows et réexécutez « iisreset ».  
  
## Voir aussi  
 [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md)