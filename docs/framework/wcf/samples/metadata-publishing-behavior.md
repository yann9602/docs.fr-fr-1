---
title: Metadata Publishing Behavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a92b41df3b2e9c556e61c08979290b12206f18aa
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="metadata-publishing-behavior"></a><span data-ttu-id="c6f6f-102">Metadata Publishing Behavior</span><span class="sxs-lookup"><span data-stu-id="c6f6f-102">Metadata Publishing Behavior</span></span>
<span data-ttu-id="c6f6f-103">Cet exemple montre comment contrôler les fonctionnalités de publication des métadonnées d’un service.</span><span class="sxs-lookup"><span data-stu-id="c6f6f-103">The Metadata Publishing Behavior sample demonstrates how to control the metadata publishing features of a service.</span></span> <span data-ttu-id="c6f6f-104">Pour empêcher la divulgation involontaire de métadonnées de service potentiellement sensibles, la publication de métadonnées est désactivée par défaut dans la configuration des services [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c6f6f-104">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services disables metadata publishing.</span></span> <span data-ttu-id="c6f6f-105">Ce comportement est sécurisé par défaut, mais il signifie également que vous ne pouvez pas utiliser d'outil d'importation de métadonnées (tel que Svcutil.exe) pour générer le code client requis pour appeler le service, à moins que le comportement de publication des métadonnées du service soit activé explicitement dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="c6f6f-105">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c6f6f-106">Pour plus de clarté, cet exemple montre comment créer un point de terminaison de publication de métadonnées non sécurisé.</span><span class="sxs-lookup"><span data-stu-id="c6f6f-106">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="c6f6f-107">De tels points de terminaison sont potentiellement disponibles aux consommateurs non authentifiés anonymes et il est nécessaire de se montrer vigilant et de s'assurer que la divulgation publique des métadonnées d'un service est appropriée avant de déployer de tels points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="c6f6f-107">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span> <span data-ttu-id="c6f6f-108">Consultez le [personnalisé sécuriser les métadonnées de point de terminaison](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) sample pour obtenir un exemple qui permet de sécuriser un point de terminaison de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="c6f6f-108">See the [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) sample for a sample that secures a metadata endpoint.</span></span>  
  
 <span data-ttu-id="c6f6f-109">L’exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md), qui implémente le `ICalculator` contrat de service.</span><span class="sxs-lookup"><span data-stu-id="c6f6f-109">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="c6f6f-110">Dans cet exemple, le client est une application console (.exe) et le service est hébergé par les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="c6f6f-110">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6f6f-111">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="c6f6f-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c6f6f-112">Pour qu'un service expose des métadonnées, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> doit être configuré sur le service.</span><span class="sxs-lookup"><span data-stu-id="c6f6f-112">For a service to expose metadata, the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> must be configured on the service.</span></span> <span data-ttu-id="c6f6f-113">Lorsque ce comportement est présent, vous pouvez publier des métadonnées en configurant un point de terminaison afin qu'il exposer le contrat <xref:System.ServiceModel.Description.IMetadataExchange> en tant qu'implémentation d'un protocole MEX (WS-MetadataExchange).</span><span class="sxs-lookup"><span data-stu-id="c6f6f-113">When this behavior is present, you can publish metadata by configuring an endpoint to expose the <xref:System.ServiceModel.Description.IMetadataExchange> contract as an implementation of a WS-MetadataExchange (MEX) protocol.</span></span> <span data-ttu-id="c6f6f-114">Par commodité, le nom de configuration abrégé « IMetadataExchange » a été donné à ce contrat.</span><span class="sxs-lookup"><span data-stu-id="c6f6f-114">As a convenience, this contract has been given the abbreviated configuration name of "IMetadataExchange".</span></span> <span data-ttu-id="c6f6f-115">Cet exemple utilise `mexHttpBinding`, qui est une liaison standard équivalente à `wsHttpBinding` dont le mode de sécurité a la valeur `None`.</span><span class="sxs-lookup"><span data-stu-id="c6f6f-115">This sample uses the `mexHttpBinding`, which is a convenience standard binding that is equivalent to the `wsHttpBinding` with the security mode set to `None`.</span></span> <span data-ttu-id="c6f6f-116">Une adresse relative de « mex » est utilisée dans le point de terminaison. Lorsqu'elle est résolue par rapport à l'adresse de base des services, l'adresse de point de terminaison est http://localhost/servicemodelsamples/service.svc/mex.</span><span class="sxs-lookup"><span data-stu-id="c6f6f-116">A relative address of "mex" is used in the endpoint, which when resolved against the services base address results in an endpoint address of http://localhost/servicemodelsamples/service.svc/mex.</span></span> <span data-ttu-id="c6f6f-117">La configuration de comportement se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="c6f6f-117">The following shows the behavior configuration:</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <!-- The serviceMetadata behavior publishes metadata through   
           the IMetadataExchange contract. When this behavior is   
           present, you can expose this contract through an endpoint   
           as shown below. Setting httpGetEnabled to true publishes   
           the service's WSDL at the <baseaddress>?wsdl, for example,  
           http://localhost/servicemodelsamples/service.svc?wsdl -->  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="c6f6f-118">Le point de terminaison MEX se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="c6f6f-118">The following shows the MEX endpoint.</span></span>  
  
```xml  
<!-- the MEX endpoint is exposed at   
     http://localhost/servicemodelsamples/service.svc/mex   
     To expose the IMetadataExchange contract, you   
     must enable the serviceMetadata behavior as demonstrated                           
     previously. -->  
<endpoint address="mex"  
          binding="mexHttpBinding"  
          contract="IMetadataExchange" />  
```  
  
 <span data-ttu-id="c6f6f-119">Cet exemple affecte <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> à la propriété `true` qui expose également les métadonnées du service à l'aide de HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="c6f6f-119">This sample sets the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, which also exposes the service's metadata using HTTP GET.</span></span> <span data-ttu-id="c6f6f-120">Pour activer un point de terminaison de métadonnées HTTP GET, le service doit avoir une adresse de base HTTP.</span><span class="sxs-lookup"><span data-stu-id="c6f6f-120">To enable an HTTP GET metadata endpoint, the service must have an HTTP base address.</span></span> <span data-ttu-id="c6f6f-121">La chaîne de requête `?wsdl` est utilisée sur l'adresse de base du service pour accéder aux métadonnées.</span><span class="sxs-lookup"><span data-stu-id="c6f6f-121">The query string `?wsdl` is used on the base address of the service to access the metadata.</span></span> <span data-ttu-id="c6f6f-122">Par exemple, pour consulter le WSDL du service dans un navigateur Web, utilisez l'adresse http://localhost/servicemodelsamples/service.svc?wsdl.</span><span class="sxs-lookup"><span data-stu-id="c6f6f-122">For example, to see the WSDL for the service in a Web browser you would use the address http://localhost/servicemodelsamples/service.svc?wsdl.</span></span> <span data-ttu-id="c6f6f-123">Vous pouvez également utiliser ce comportement pour exposer des métadonnées sur HTTPS en affectant <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> à `true`.</span><span class="sxs-lookup"><span data-stu-id="c6f6f-123">Alternatively, you can use this behavior to expose metadata over HTTPS by setting <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> to `true`.</span></span> <span data-ttu-id="c6f6f-124">Cela requiert une adresse de base HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c6f6f-124">This requires an HTTPS base address.</span></span>  
  
 <span data-ttu-id="c6f6f-125">Pour utiliser de point de terminaison MEX du service d’accès du [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="c6f6f-125">To access the service's MEX endpoint use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 <span data-ttu-id="c6f6f-126">Cette opération génère un client basé sur les métadonnées du service.</span><span class="sxs-lookup"><span data-stu-id="c6f6f-126">This generates a client based on the service's metadata.</span></span>  
  
 <span data-ttu-id="c6f6f-127">Pour accéder aux métadonnées du service à l'aide de HTTP GET, pointez votre navigateur sur http://localhost/servicemodelsamples/service.svc?wsdl.</span><span class="sxs-lookup"><span data-stu-id="c6f6f-127">To access the service's metadata using HTTP GET, point your browser to http://localhost/servicemodelsamples/service.svc?wsdl.</span></span>  
  
 <span data-ttu-id="c6f6f-128">Si vous supprimez ce comportement et tentez d'ouvrir le service, vous obtenez une exception.</span><span class="sxs-lookup"><span data-stu-id="c6f6f-128">If you remove this behavior and try to open the service you get an exception.</span></span> <span data-ttu-id="c6f6f-129">Cette erreur se produit car sans le comportement, le point de terminaison configuré avec le contrat `IMetadataExchange` n'a aucune implémentation.</span><span class="sxs-lookup"><span data-stu-id="c6f6f-129">This error occurs because without the behavior, the endpoint configured with the `IMetadataExchange` contract has no implementation.</span></span>  
  
 <span data-ttu-id="c6f6f-130">Si vous affectez `HttpGetEnabled` à `false`, la page d'aide CalculatorService s'affiche à la place des métadonnées du service.</span><span class="sxs-lookup"><span data-stu-id="c6f6f-130">If you set `HttpGetEnabled` to `false`, you see the CalculatorService help page instead of seeing the service's metadata.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c6f6f-131">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="c6f6f-131">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c6f6f-132">Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c6f6f-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c6f6f-133">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c6f6f-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="c6f6f-134">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c6f6f-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c6f6f-135">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c6f6f-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c6f6f-136">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="c6f6f-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c6f6f-137">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c6f6f-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c6f6f-138">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="c6f6f-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
  
## <a name="see-also"></a><span data-ttu-id="c6f6f-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6f6f-139">See Also</span></span>
