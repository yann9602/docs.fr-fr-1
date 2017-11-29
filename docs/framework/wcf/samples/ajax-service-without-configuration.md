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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 32879c2b618f3e22960a7828d29601f502a55585
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ajax-service-without-configuration"></a><span data-ttu-id="42cbf-102">AJAX Service Without Configuration</span><span class="sxs-lookup"><span data-stu-id="42cbf-102">AJAX Service Without Configuration</span></span>
<span data-ttu-id="42cbf-103">Cet exemple illustre comment utiliser [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pour créer un service de base ASP.NET AJAX (Asynchronous JavaScript and XML), c'est-à-dire un service auquel vous pouvez accéder en utilisant un code Javascript depuis un client de navigateur Web sans recourir à des paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="42cbf-103">This sample demonstrates how to use [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access by using JavaScript code from a Web browser client) without using any configuration settings.</span></span> <span data-ttu-id="42cbf-104">Le service utilise une syntaxe spéciale dans le fichier .svc pour activer automatiquement un point de terminaison AJAX.</span><span class="sxs-lookup"><span data-stu-id="42cbf-104">The service uses special syntax in the .svc file to automatically enable an AJAX endpoint.</span></span>  
  
 <span data-ttu-id="42cbf-105">La prise en charge d'AJAX dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est optimisée pour permettre son utilisation avec ASP.NET AJAX via le contrôle `ScriptManager`.</span><span class="sxs-lookup"><span data-stu-id="42cbf-105">AJAX support in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="42cbf-106">Pour obtenir un exemple d’utilisation de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] avec ASP.NET AJAX, consultez le [exemples Ajax](http://msdn.microsoft.com/en-us/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span><span class="sxs-lookup"><span data-stu-id="42cbf-106">For an example of using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with ASP.NET AJAX, see the [Ajax Samples](http://msdn.microsoft.com/en-us/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="42cbf-107">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="42cbf-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="42cbf-108">Cet exemple est basé sur le service AJAX Service utilisant HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="42cbf-108">This sample builds upon the AJAX Service Using HTTP POST.</span></span> <span data-ttu-id="42cbf-109">Comme décrit dans la [servie AJAX de base](../../../../docs/framework/wcf/samples/basic-ajax-service.md) exemple, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> est utilisé pour héberger le service.</span><span class="sxs-lookup"><span data-stu-id="42cbf-109">As described in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used to host the service.</span></span>  
  
```  
<%ServiceHost  
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CalculatorService  
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"  
%>  
```  
  
 <span data-ttu-id="42cbf-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ajoute automatiquement un <xref:System.ServiceModel.Description.WebScriptEndpoint> au service.</span><span class="sxs-lookup"><span data-stu-id="42cbf-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> automatically adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> to the service.</span></span> <span data-ttu-id="42cbf-111">Si aucune modification de configuration ne doit être apportées au point de terminaison, le \<système. ServiceModel > section peut être supprimée complètement du fichier Web.config pour le service.</span><span class="sxs-lookup"><span data-stu-id="42cbf-111">If no configuration changes need to be made to the endpoint, the \<system.ServiceModel> section can be completely removed from the Web.config file for the service.</span></span> <span data-ttu-id="42cbf-112">Le fichier Web.config contient des paramètres ASP.NET, qui sont utilisés par ConfigFreeClientPage.aspx.</span><span class="sxs-lookup"><span data-stu-id="42cbf-112">The Web.config file contains some ASP.NET settings, which are used by ConfigFreeClientPage.aspx.</span></span> <span data-ttu-id="42cbf-113">Si ce n'était pas le cas, l'intégralité du fichier Web.config pourrait être supprimée.</span><span class="sxs-lookup"><span data-stu-id="42cbf-113">If that were not the case, the entire Web.config file could be removed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="42cbf-114">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="42cbf-114">The samples may already be installed on your computer.</span></span> <span data-ttu-id="42cbf-115">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="42cbf-115">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="42cbf-116">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="42cbf-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="42cbf-117">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="42cbf-117">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="42cbf-118">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="42cbf-118">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="42cbf-119">Veillez à effectuer les instructions d’installation dans [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="42cbf-119">Ensure that you perform the setup instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="42cbf-120">Générez la solution ConfigFreeAjaxService.sln comme décrit dans [génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="42cbf-120">Build the solution ConfigFreeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="42cbf-121">Accédez à http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx (n'ouvrez pas le fichier ConfigFreeClientPage.aspx dans le navigateur à partir du répertoire de projet).</span><span class="sxs-lookup"><span data-stu-id="42cbf-121">Navigate to http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx (do not open ConfigFreeClientPage.aspx in the browser from within the project directory).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="42cbf-122">Avant d'exécuter cet exemple, assurez-vous que l'authentification anonyme et que l'authentification Windows ne sont pas toutes deux activées dans le dossier ServiceModelSamples des services IIS.</span><span class="sxs-lookup"><span data-stu-id="42cbf-122">When running this sample, please ensure that Anonymous Authentication and Windows Authentication are not enabled simultaneously for the ServiceModelSamples folder in IIS.</span></span> <span data-ttu-id="42cbf-123">Si tel est le cas, désactivez l'authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="42cbf-123">If that is the case, please disable Windows Authentication.</span></span> <span data-ttu-id="42cbf-124">Une fois que vous avez exécuté l'exemple, activez l'authentification Windows et réexécutez « iisreset ».</span><span class="sxs-lookup"><span data-stu-id="42cbf-124">Once you have run the sample, enable Windows Authentication and run "iisreset".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42cbf-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42cbf-125">See Also</span></span>  
 [<span data-ttu-id="42cbf-126">Service AJAX de base</span><span class="sxs-lookup"><span data-stu-id="42cbf-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
