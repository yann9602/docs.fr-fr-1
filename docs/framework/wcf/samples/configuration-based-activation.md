---
title: "Activation basée sur la configuration"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21bb762e-c43e-4b0c-887b-5e434d665838
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cc39a282cbb12b014c0749b3eb807f3248fca16e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="configuration-based-activation"></a><span data-ttu-id="1a550-102">Activation basée sur la configuration</span><span class="sxs-lookup"><span data-stu-id="1a550-102">Configuration-Based Activation</span></span>
<span data-ttu-id="1a550-103">Cet exemple montre comment activer des services [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sans avoir à utiliser un fichier .svc.</span><span class="sxs-lookup"><span data-stu-id="1a550-103">This sample demonstrates how to activate [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services without requiring a .svc file.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1a550-104">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1a550-104">The samples may already be installed on your computer.</span></span> <span data-ttu-id="1a550-105">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="1a550-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1a550-106">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1a550-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1a550-107">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="1a550-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\ConfigBasedActivation`  
  
## <a name="sample-details"></a><span data-ttu-id="1a550-108">Détails de l'exemple</span><span class="sxs-lookup"><span data-stu-id="1a550-108">Sample Details</span></span>  
 <span data-ttu-id="1a550-109">Dans cet exemple, le client est le client de test [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et le service est hébergé dans IIS.</span><span class="sxs-lookup"><span data-stu-id="1a550-109">In this sample, the client is the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client and the service is hosted in IIS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1a550-110">Les instructions d'installation et de génération correspondant à cet exemple figurent en fin de rubrique.</span><span class="sxs-lookup"><span data-stu-id="1a550-110">The setup and build instructions for this sample are located at the end of this topic.</span></span>  
  
### <a name="activation-of-services-without-requiring-a-svc-file"></a><span data-ttu-id="1a550-111">Activation de services sans avoir à utiliser de fichier .svc</span><span class="sxs-lookup"><span data-stu-id="1a550-111">Activation of services without requiring a .svc file</span></span>  
 <span data-ttu-id="1a550-112">Dans [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], un fichier .svc était requis pour activer un service.</span><span class="sxs-lookup"><span data-stu-id="1a550-112">In [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], a .svc file was required for activating a service.</span></span> <span data-ttu-id="1a550-113">Cela générait une charge de gestion supplémentaire, en raison du déploiement et de la maintenance nécessaires d'un fichier supplémentaire avec l'application.</span><span class="sxs-lookup"><span data-stu-id="1a550-113">This caused additional management overhead, because an additional file was required to be deployed and maintained along with the application.</span></span> <span data-ttu-id="1a550-114">Avec le lancement de [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], les composants d'activation peuvent être configurés à l'aide du fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="1a550-114">With the release of [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], the activation components can be configured using the application configuration file.</span></span>  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]<span data-ttu-id="1a550-115"> introduit un nouvel élément de configuration (<xref:System.ServiceModel.Configuration.ServiceActivationElement>), dans le <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> du fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="1a550-115"> introduces a new configuration element (<xref:System.ServiceModel.Configuration.ServiceActivationElement>), in the <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> of the application configuration file.</span></span> <span data-ttu-id="1a550-116">La collection <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> accepte une collection de services à activer, comme le montre l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="1a550-116">The <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> collection accepts a collection of services to activate, as shown in the following code example.</span></span>  
  
```xml  
<serviceActivations>  
   <add relativeAddress="Calculator.svc" service="Microsoft.ServiceModel.Samples.CalculatorService" />  
  
<serviceActivations>  
```  
  
 <span data-ttu-id="1a550-117">L'observation à formuler est que la configuration semble très similaire à celle de fichiers .svc.</span><span class="sxs-lookup"><span data-stu-id="1a550-117">The observation to make is the configuration looks very similar to the configuration of .svc files.</span></span> <span data-ttu-id="1a550-118">Un attribut supplémentaire, `relativeAddress`, qui fournit l'adresse du service, a été introduit.</span><span class="sxs-lookup"><span data-stu-id="1a550-118">An additional attribute that is introduced is the `relativeAddress` that provides the address of the service.</span></span> <span data-ttu-id="1a550-119">L'adresse relative constitue également le chemin d'accès virtuel du service.</span><span class="sxs-lookup"><span data-stu-id="1a550-119">The relative address is also the virtual path for the service.</span></span> <span data-ttu-id="1a550-120">L'hôte récupère le fichier Web.config du fichier à partir de l'emplacement `virtualPath`, s'il existe ; sinon, l'hôte effectue une recherche récursive dans son dossier parent.</span><span class="sxs-lookup"><span data-stu-id="1a550-120">The host retrieves the Web.config file of the file from the `virtualPath` location, if present; otherwise the host searches its parent folder recursively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1a550-121">Pour fonctionner, cet exemple requiert un hébergement dans IIS.</span><span class="sxs-lookup"><span data-stu-id="1a550-121">This sample requires hosting in IIS to function.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="1a550-122">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="1a550-122">To use this sample</span></span>  
  
1.  <span data-ttu-id="1a550-123">À l'aide de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ouvrez le fichier Service.csproj.</span><span class="sxs-lookup"><span data-stu-id="1a550-123">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the Service.csproj file.</span></span>  
  
2.  <span data-ttu-id="1a550-124">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="1a550-124">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="1a550-125">Testez le service en exécutant WCFTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="1a550-125">Test the service by running WCFTestClient.exe.</span></span>  
  
4.  <span data-ttu-id="1a550-126">À l'aide de l'[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], naviguez jusqu'au dossier %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE.</span><span class="sxs-lookup"><span data-stu-id="1a550-126">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], navigate to the %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE folder.</span></span>  
  
5.  <span data-ttu-id="1a550-127">Exécutez WcfTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="1a550-127">Run WcfTestClient.exe.</span></span>  
  
6.  <span data-ttu-id="1a550-128">Définissez l'adresse MEX du service.</span><span class="sxs-lookup"><span data-stu-id="1a550-128">Set the MEX address of the service.</span></span>  
  
7.  <span data-ttu-id="1a550-129">Appuyez sur CTRL+MAJ+A pour définir l'adresse du service.</span><span class="sxs-lookup"><span data-stu-id="1a550-129">Press CTRL+SHIFT+A to set the service address.</span></span>  
  
8.  <span data-ttu-id="1a550-130">Définissez l'adresse http://localhost/ServiceModelSamples/Calculator.svc.</span><span class="sxs-lookup"><span data-stu-id="1a550-130">Set the address to http://localhost/ServiceModelSamples/Calculator.svc.</span></span>  
  
9. <span data-ttu-id="1a550-131">Effectuez l'opération `Add`.</span><span class="sxs-lookup"><span data-stu-id="1a550-131">Perform the `Add` operation.</span></span> <span data-ttu-id="1a550-132">Affectez au paramètre `n1` la valeur 10 et au paramètre `n2` la valeur 15.</span><span class="sxs-lookup"><span data-stu-id="1a550-132">Set value on the `n1` parameter to 10 and set value on the `n2` parameter to 15.</span></span>  
  
10. <span data-ttu-id="1a550-133">Appuyez sur **appeler**.</span><span class="sxs-lookup"><span data-stu-id="1a550-133">Press **Invoke**.</span></span>  
  
     <span data-ttu-id="1a550-134">Le résultat attendu est 25.</span><span class="sxs-lookup"><span data-stu-id="1a550-134">The expected result is 25.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1a550-135">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="1a550-135">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="1a550-136">Vérifiez que vous avez effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1a550-136">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="1a550-137">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1a550-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="1a550-138">Une fois la solution générée, exécutez Setup.bat pour installer l'application ServiceModelSamples dans IIS.</span><span class="sxs-lookup"><span data-stu-id="1a550-138">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS.</span></span> <span data-ttu-id="1a550-139">Le répertoire ServiceModelSamples doit maintenant apparaître en tant qu'application IIS.</span><span class="sxs-lookup"><span data-stu-id="1a550-139">The ServiceModelSamples directory should now appear as an IIS Application.</span></span>  
  
4.  <span data-ttu-id="1a550-140">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1a550-140">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a550-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a550-141">See Also</span></span>  
 [<span data-ttu-id="1a550-142">Hébergement de AppFabric et exemples de persistance</span><span class="sxs-lookup"><span data-stu-id="1a550-142">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
