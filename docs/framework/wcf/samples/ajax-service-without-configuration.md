---
title: AJAX Service Without Configuration
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 82d9bb27ef20aa4e425e232a23c785af3b7e6e5a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ajax-service-without-configuration"></a>AJAX Service Without Configuration
Cet exemple illustre comment utiliser [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pour créer un service de base ASP.NET AJAX (Asynchronous JavaScript and XML), c'est-à-dire un service auquel vous pouvez accéder en utilisant un code Javascript depuis un client de navigateur Web sans recourir à des paramètres de configuration. Le service utilise une syntaxe spéciale dans le fichier .svc pour activer automatiquement un point de terminaison AJAX.  
  
 La prise en charge d'AJAX dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est optimisée pour permettre son utilisation avec ASP.NET AJAX via le contrôle `ScriptManager`. Pour obtenir un exemple d’utilisation de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] avec ASP.NET AJAX, consultez le [exemples Ajax](http://msdn.microsoft.com/en-us/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Cet exemple est basé sur le service AJAX Service utilisant HTTP POST. Comme décrit dans la [servie AJAX de base](../../../../docs/framework/wcf/samples/basic-ajax-service.md) exemple, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> est utilisé pour héberger le service.  
  
```  
<%ServiceHost  
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CalculatorService  
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"  
%>  
```  
  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ajoute automatiquement un <xref:System.ServiceModel.Description.WebScriptEndpoint> au service. Si aucune modification de configuration ne doit être apportées au point de terminaison, le \<système. ServiceModel > section peut être supprimée complètement du fichier Web.config pour le service. Le fichier Web.config contient des paramètres ASP.NET, qui sont utilisés par ConfigFreeClientPage.aspx. Si ce n'était pas le cas, l'intégralité du fichier Web.config pourrait être supprimée.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Veillez à effectuer les instructions d’installation dans [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Générez la solution ConfigFreeAjaxService.sln comme décrit dans [génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Accédez à http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx (n'ouvrez pas le fichier ConfigFreeClientPage.aspx dans le navigateur à partir du répertoire de projet).  
  
> [!NOTE]
>  Avant d'exécuter cet exemple, assurez-vous que l'authentification anonyme et que l'authentification Windows ne sont pas toutes deux activées dans le dossier ServiceModelSamples des services IIS. Si tel est le cas, désactivez l'authentification Windows. Une fois que vous avez exécuté l'exemple, activez l'authentification Windows et réexécutez « iisreset ».  
  
## <a name="see-also"></a>Voir aussi  
 [Service AJAX de base](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
