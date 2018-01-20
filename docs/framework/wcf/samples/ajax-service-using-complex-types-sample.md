---
title: AJAX Service Using Complex Types, exemple
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4c83da8aba2e1a88665f4443d98dbebbd5b1962b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="ajax-service-using-complex-types-sample"></a><span data-ttu-id="bd001-102">AJAX Service Using Complex Types, exemple</span><span class="sxs-lookup"><span data-stu-id="bd001-102">AJAX Service Using Complex Types Sample</span></span>
<span data-ttu-id="bd001-103">Cet exemple montre comment utiliser [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pour créer un service AJAX (ASP.NET Asynchronous JavaScript and XML) qui créent des instances de types complexes et les envoient entre le service et le client au format JSON (JavaScript Object Notation).</span><span class="sxs-lookup"><span data-stu-id="bd001-103">This sample demonstrates how to use [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to create an ASP.NET Asynchronous JavaScript and XML (AJAX) service that creates instances of complex types and sends them between service and client as JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="bd001-104">Vous pouvez accéder à un service AJAX en utilisant le code JavaScript à partir d'un client de navigateur Web.</span><span class="sxs-lookup"><span data-stu-id="bd001-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="bd001-105">Cet exemple est basé le [servie AJAX de base](../../../../docs/framework/wcf/samples/basic-ajax-service.md) exemple.</span><span class="sxs-lookup"><span data-stu-id="bd001-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="bd001-106">La prise en charge d'AJAX dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est optimisée pour permettre son utilisation avec ASP.NET AJAX via le contrôle <xref:System.Web.UI.ScriptManager>.</span><span class="sxs-lookup"><span data-stu-id="bd001-106">AJAX support in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is optimized for use with ASP.NET AJAX through the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="bd001-107">Pour obtenir un exemple d’utilisation de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] avec ASP.NET AJAX, consultez le [exemples AJAX](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span><span class="sxs-lookup"><span data-stu-id="bd001-107">For an example of using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with ASP.NET AJAX, see the [AJAX Samples](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd001-108">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="bd001-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="bd001-109">Le service dans l'exemple suivant est un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sans code spécifique à AJAX.</span><span class="sxs-lookup"><span data-stu-id="bd001-109">The service in the following sample is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service with no AJAX-specific code.</span></span> <span data-ttu-id="bd001-110">L'attribut <xref:System.ServiceModel.Web.WebGetAttribute> n'étant pas appliqué, le verbe HTTP par défaut ("POST") est utilisé.</span><span class="sxs-lookup"><span data-stu-id="bd001-110">Because the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="bd001-111">Le service a une opération appelée `DoMath` qui retourne un type complexe appelé `MathResult`.</span><span class="sxs-lookup"><span data-stu-id="bd001-111">The service has one operation, `DoMath`, which returns a complex type named `MathResult`.</span></span> <span data-ttu-id="bd001-112">Le type complexe est un type de contrat de données standard qui ne contient pas non plus de code spécifique à AJAX.</span><span class="sxs-lookup"><span data-stu-id="bd001-112">The complex type is a standard data contract type, which also contains no AJAX-specific code.</span></span>  
  
```  
[DataContract]  
    public class MathResult  
    {  
        [DataMember]  
        public double sum;  
        [DataMember]  
        public double difference;  
        [DataMember]  
        public double product;  
        [DataMember]  
        public double quotient;  
    }  
```  
  
 <span data-ttu-id="bd001-113">Créez un point de terminaison AJAX sur le service à l'aide de <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, comme dans l'exemple de servie AJAX de base.</span><span class="sxs-lookup"><span data-stu-id="bd001-113">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>  
  
 <span data-ttu-id="bd001-114">La page Web client ComplexTypeClientPage.aspx contient du code ASP.NET et JavaScript pour appeler le service lorsque l’utilisateur clique sur le **effectuer le calcul** bouton sur la page.</span><span class="sxs-lookup"><span data-stu-id="bd001-114">The client Web page ComplexTypeClientPage.aspx contains ASP.NET and JavaScript code to invoke the service when the user clicks the **Perform calculation** button on the page.</span></span> <span data-ttu-id="bd001-115">Le code pour appeler le service construit un corps JSON et l’envoie à l’aide de HTTP POST, similaire à la [AJAX Service utilisant HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) exemple.</span><span class="sxs-lookup"><span data-stu-id="bd001-115">The code to invoke the service constructs a JSON body and sends it using HTTP POST, similar to the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) sample.</span></span>  
  
 <span data-ttu-id="bd001-116">Une fois l'appel de service réussi, vous pouvez accéder aux membres de données individuels (`sum`, `difference`, `product` et `quotient`) sur l'objet JavaScript résultant.</span><span class="sxs-lookup"><span data-stu-id="bd001-116">After the service call succeeds, you can access the individual data members (`sum`, `difference`, `product` and `quotient`) on the resulting JavaScript object.</span></span>  
  
```  
function onSuccess(mathResult){  
     document.getElementById("sum").value = mathResult.sum;  
     document.getElementById("difference").value = mathResult.difference;  
     document.getElementById("product").value = mathResult.product;  
     document.getElementById("quotient").value = mathResult.quotient;  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bd001-117">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="bd001-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="bd001-118">Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bd001-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="bd001-119">Générez la solution ComplexTypeAjaxService.sln comme décrit dans [génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bd001-119">Build the solution ComplexTypeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="bd001-120">Naviguez jusqu'à http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx (n'ouvrez pas ComplexTypeClientPage.aspx dans le navigateur depuis le répertoire du projet).</span><span class="sxs-lookup"><span data-stu-id="bd001-120">Navigate to http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx (do not open ComplexTypeClientPage.aspx in the browser from the project directory).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bd001-121">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="bd001-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="bd001-122">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="bd001-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bd001-123">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="bd001-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bd001-124">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="bd001-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`  
  
## <a name="see-also"></a><span data-ttu-id="bd001-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd001-125">See Also</span></span>  
 [<span data-ttu-id="bd001-126">Service AJAX de base</span><span class="sxs-lookup"><span data-stu-id="bd001-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
