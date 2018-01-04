---
title: AJAX Service Using HTTP POST
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c2447f641748cdcc3419fda2a6ae8f02d68ed98e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ajax-service-using-http-post"></a><span data-ttu-id="ebae2-102">AJAX Service Using HTTP POST</span><span class="sxs-lookup"><span data-stu-id="ebae2-102">AJAX Service Using HTTP POST</span></span>
<span data-ttu-id="ebae2-103">Cet exemple montre comment utiliser [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pour créer un [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] service AJAX (JavaScript et XML asynchrones) qui utilise HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="ebae2-103">This sample demonstrates how to use [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to create an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Asynchronous JavaScript and XML (AJAX) service that uses HTTP POST.</span></span> <span data-ttu-id="ebae2-104">Un service AJAX est un service auquel vous pouvez accéder à l'aide du code Javascript de base d'un client de navigateur Web.</span><span class="sxs-lookup"><span data-stu-id="ebae2-104">An AJAX service is one that you can access by using basic JavaScript code from a Web browser client.</span></span> <span data-ttu-id="ebae2-105">Cet exemple est basé le [servie AJAX de base](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample ; la seule différence entre les deux exemples est l’utilisation de HTTP POST au lieu de HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="ebae2-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample; the only difference between the two samples is the use of HTTP POST instead of HTTP GET.</span></span>  
  
 <span data-ttu-id="ebae2-106">La prise en charge d'AJAX dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] est optimisée pour permettre son utilisation avec ASP.NET AJAX via le contrôle `ScriptManager`.</span><span class="sxs-lookup"><span data-stu-id="ebae2-106">AJAX support in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="ebae2-107">Pour obtenir un exemple d’utilisation de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] avec ASP.NET AJAX, consultez le [exemples Ajax](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="ebae2-107">For an example of using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with ASP.NET AJAX, see the [Ajax Samples](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ebae2-108">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="ebae2-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ebae2-109">Le service dans l'exemple suivant est un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sans code spécifique à AJAX.</span><span class="sxs-lookup"><span data-stu-id="ebae2-109">The service in the following sample is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service with no AJAX-specific code.</span></span>  
  
 <span data-ttu-id="ebae2-110">Si le <xref:System.ServiceModel.Web.WebInvokeAttribute> attribut est appliqué à une opération, ou le <xref:System.ServiceModel.Web.WebGetAttribute> attribut n’est pas appliqué, le verbe HTTP de valeur par défaut (« POST ») est utilisé.</span><span class="sxs-lookup"><span data-stu-id="ebae2-110">If the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute is applied on an operation, or the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="ebae2-111">Les demandes POST sont plus difficiles à générer que les demandes GET, mais elles ne sont pas mises en cache ; utilisez des demandes POST pour toutes les opérations où la mise en cache n'est pas appropriée.</span><span class="sxs-lookup"><span data-stu-id="ebae2-111">POST requests are harder to construct than GET requests, but they are not cached; use POST requests for all operations where caching is not appropriate.</span></span>  
  
```  
[ServiceContract(Namespace = "PostAjaxService")]  
    public interface ICalculator  
    {        [WebInvoke]  
        double Add(double n1, double n2);  
        //Other operations omitted…  
    }  
```  
  
 <span data-ttu-id="ebae2-112">Créez un point de terminaison AJAX sur le service à l'aide de <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, comme dans l'exemple de servie AJAX de base.</span><span class="sxs-lookup"><span data-stu-id="ebae2-112">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>  
  
 <span data-ttu-id="ebae2-113">Contrairement aux demandes GET, vous ne pouvez pas appeler des services POST depuis le navigateur.</span><span class="sxs-lookup"><span data-stu-id="ebae2-113">Unlike GET requests, you cannot invoke POST services from the browser.</span></span> <span data-ttu-id="ebae2-114">Par exemple, le fait de naviguer jusqu’à http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 génère une erreur, car le service POST s’attend à ce que les paramètres `n1` et `n2` soient envoyés dans le corps du message (au format JSON) et non dans l’URL.</span><span class="sxs-lookup"><span data-stu-id="ebae2-114">For example, navigating to http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 results in an error, because the POST service expects the `n1` and `n2` parameters to be sent in the message body—in the JSON format—and not in the URL.</span></span>  
  
 <span data-ttu-id="ebae2-115">La page web PostAjaxClientPage.aspx du client contient le code ASP.NET pour appeler le service toutes les fois que l’utilisateur clique sur l’un des boutons d’opération de la page.</span><span class="sxs-lookup"><span data-stu-id="ebae2-115">The client Web page PostAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="ebae2-116">Le service répond de la même façon que dans les [servie AJAX de base](../../../../docs/framework/wcf/samples/basic-ajax-service.md) exemple, avec la demande GET.</span><span class="sxs-lookup"><span data-stu-id="ebae2-116">The service responds in the same way as in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, with the GET request.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ebae2-117">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ebae2-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ebae2-118">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="ebae2-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ebae2-119">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ebae2-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ebae2-120">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="ebae2-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ebae2-121">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="ebae2-121">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ebae2-122">Veillez à effectuer les instructions d’installation [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ebae2-122">Ensure that you perform the setup instructions [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ebae2-123">Générez la solution PostAjaxService.sln comme décrit dans [génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ebae2-123">Build the solution PostAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="ebae2-124">Naviguez jusqu'à http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx (n'ouvrez pas PostAjaxClientPage.aspx dans le navigateur depuis le répertoire du projet).</span><span class="sxs-lookup"><span data-stu-id="ebae2-124">Navigate to http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx (do not open PostAjaxClientPage.aspx in the browser from the project directory).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebae2-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ebae2-125">See Also</span></span>
