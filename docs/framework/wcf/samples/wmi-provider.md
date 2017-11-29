---
title: WMI Provider
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
caps.latest.revision: "35"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7a0a64516bea4204eb782013e718c2fa26c6024b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="wmi-provider"></a><span data-ttu-id="c3375-102">WMI Provider</span><span class="sxs-lookup"><span data-stu-id="c3375-102">WMI Provider</span></span>
<span data-ttu-id="c3375-103">Cet exemple montre comment rassembler pendant l'exécution des données des services [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] en utilisant le fournisseur WMI (Windows Management Instrumentation) généré dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c3375-103">This sample demonstrates how to gather data from [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services at runtime by using the Windows Management Instrumentation (WMI) provider that is built into [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="c3375-104">Cet exemple montre également comment ajouter un objet WMI défini par l'utilisateur à un service.</span><span class="sxs-lookup"><span data-stu-id="c3375-104">Also, this sample demonstrates how to add a user-defined WMI object to a service.</span></span> <span data-ttu-id="c3375-105">L’exemple active le fournisseur WMI pour les [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md) et montre comment collecter des données à partir de la `ICalculator` service lors de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="c3375-105">The sample activates the WMI provider for the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and demonstrates how to gather data from the `ICalculator` service at runtime.</span></span>  
  
 <span data-ttu-id="c3375-106">WMI est l'implémentation de Microsoft de la norme WBEM (Web-Based Enterprise Management).</span><span class="sxs-lookup"><span data-stu-id="c3375-106">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="c3375-107">Pour plus d’informations sur le SDK WMI, consultez [Windows Management Instrumentation](https://msdn.microsoft.com/library/aa394582.aspx).</span><span class="sxs-lookup"><span data-stu-id="c3375-107">For more information about the WMI SDK, see [Windows Management Instrumentation](https://msdn.microsoft.com/library/aa394582.aspx).</span></span> <span data-ttu-id="c3375-108">WBEM est une norme d'industrie qui détermine comment les applications exposent l'instrumentation de gestion aux outils de gestion externes.</span><span class="sxs-lookup"><span data-stu-id="c3375-108">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c3375-109"> implémente un fournisseur WMI, un composant qui expose l'instrumentation au moment de l'exécution par l'intermédiaire d'une interface WBEM compatible.</span><span class="sxs-lookup"><span data-stu-id="c3375-109"> implements a WMI provider, a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="c3375-110">Les outils de gestion peuvent se connecter aux services au moment de l'exécution par l'intermédiaire de l'interface.</span><span class="sxs-lookup"><span data-stu-id="c3375-110">Management tools can connect to the services through the interface at runtime.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c3375-111"> expose des attributs de services tels que les adresses, les liaisons, les comportements et les écouteurs.</span><span class="sxs-lookup"><span data-stu-id="c3375-111"> exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="c3375-112">Le fournisseur WMI intégré est activé dans le fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="c3375-112">The built-in WMI provider is activated in the configuration file of the application.</span></span> <span data-ttu-id="c3375-113">Cette opération est effectuée via le `wmiProviderEnabled` attribut de la [ \<diagnostics >](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) dans les [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, comme indiqué dans l’exemple suivant configuration :</span><span class="sxs-lookup"><span data-stu-id="c3375-113">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration:</span></span>  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="c3375-114">Cette entrée de configuration expose une interface WMI.</span><span class="sxs-lookup"><span data-stu-id="c3375-114">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="c3375-115">Les applications de gestion peuvent maintenant se connecter par le biais de cette interface et accéder à l'instrumentation de gestion de l'application.</span><span class="sxs-lookup"><span data-stu-id="c3375-115">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="custom-wmi-object"></a><span data-ttu-id="c3375-116">Objet  WMI personnalisé.</span><span class="sxs-lookup"><span data-stu-id="c3375-116">Custom WMI Object</span></span>  
 <span data-ttu-id="c3375-117">L'ajout d'objets WMI à un service permet de révéler des informations définies par l'utilisateur en même temps que les informations du fournisseur WMI intégré.</span><span class="sxs-lookup"><span data-stu-id="c3375-117">Adding WMI objects to a service makes it possible to reveal user-defined information along with the built-in WMI provider information.</span></span> <span data-ttu-id="c3375-118">Cela s'effectue en publiant le schéma du service dans WMI en utilisant l'application Installutil.exe.</span><span class="sxs-lookup"><span data-stu-id="c3375-118">This is accomplished by publishing the schema of the service to WMI by using the Installutil.exe application.</span></span> <span data-ttu-id="c3375-119">Des instructions plus détaillées sont disponibles dans les instructions d'installation à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="c3375-119">Instructions to accomplish this, along with more details can be found in the setup instructions at the end of the topic.</span></span>  
  
## <a name="accessing-wmi-information"></a><span data-ttu-id="c3375-120">Accès aux informations WMI</span><span class="sxs-lookup"><span data-stu-id="c3375-120">Accessing WMI Information</span></span>  
 <span data-ttu-id="c3375-121">Les données WMI sont accessibles de plusieurs façons différentes.</span><span class="sxs-lookup"><span data-stu-id="c3375-121">WMI data can be accessed many different ways.</span></span> <span data-ttu-id="c3375-122">Microsoft fournit des API WMI pour les scripts, les applications [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], les applications C++ et le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] (http://msdn.microsoft.com/library/default.asp?url=/library/wmisdk/wmi/using_wmi.asp).</span><span class="sxs-lookup"><span data-stu-id="c3375-122">Microsoft provides WMI APIs for scripts, [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] applications, C++ applications, and the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] (http://msdn.microsoft.com/library/default.asp?url=/library/wmisdk/wmi/using_wmi.asp).</span></span>  
  
 <span data-ttu-id="c3375-123">Cet exemple utilise deux scripts Java : un pour énumérer des services qui s'exécutent sur l'ordinateur avec certaines de leurs propriétés et le second pour consulter les données WMI définies par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c3375-123">This sample uses two Java scripts: one to enumerate services running on the computer along with some of their properties and the second to view user-defined WMI data.</span></span> <span data-ttu-id="c3375-124">Le script ouvre une connexion au fournisseur WMI, analyse les données et affiche les données rassemblées.</span><span class="sxs-lookup"><span data-stu-id="c3375-124">The script opens a connection to the WMI provider, parses data, and displays the data gathered.</span></span>  
  
 <span data-ttu-id="c3375-125">Démarrez l'exemple pour créer une instance en cours d'exécution d'un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c3375-125">Start the sample to create a running instance of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="c3375-126">Pendant que le service s'exécute, exécutez chaque script Java en utilisant la commande suivante dans l'invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="c3375-126">While the service is running, run each Java script by using the following command at the command prompt:</span></span>  
  
```  
cscript EnumerateServices.js  
```  
  
 <span data-ttu-id="c3375-127">Le script accède à l'instrumentation contenue dans le service et produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="c3375-127">The script accesses the instrumentation contained in the service and produces the following output:</span></span>  
  
```  
Microsoft (R) Windows Script Host Version 5.6  
Copyright © Microsoft Corporation 1996-2001. All rights reserved.  
  
1 service(s) found.  
|-PID:           5776  
|-DistinguishedName:  CalculatorService@http://localhost/ServiceModelSamples/service.svc  
|-Endpoints:     1 endpoints  
  |-CalculatorService.ICalculator@http://localhost/ServiceModelSamples/service.svc  
    |-Address:                        http://localhost/ServiceModelSamples/service.svc  
    |-CounterInstanceName:  
    |-AddressHeaders:                 0  
    |-ContractType:                   Contract.Name='ICalculator'  
    |-BindingElements:                4 bindings  
      |-BindingElements[0]  
        |-Type:                       TransactionFlowBindingElement  
      |-BindingElements[1]  
        |-Type:                       SymmetricSecurityBindingElement  
      |-BindingElements[2]  
        |-Type:                       TextMessageEncodingBindingElement  
        |-MaxReadPoolSize:            64  
        |-MaxWritePoolSize:           16  
      |-BindingElements[3]  
        |-Type:                       HttpTransportBindingElement  
        |-ManualAddressing:           false  
        |-MaxBufferSize:              65536  
        |-AllowCookies:               false  
        |-AuthenticationScheme:       Anonymous  
        |-BypassProxyOnLocal:         false  
        |-HostNameComparisonMode:     StrongWildcard  
        |-ProxyAddress:               null  
        |-ProxyAuthenticationScheme:  Anonymous  
        |-Realm:  
        |-TransferMode:               Buffered  
        |-UseDefaultWebProxy:         true  
|-Behaviors:     5 behaviors  
      |-Behavior[0]  
      |-Type:                       ServiceBehaviorAttribute  
        |-AddressFilterMode:               Exact  
        |-AutomaticSessionShutdown:        true  
        |-ConcurrencyMode:                 Single  
        |-IncludeExceptionDetailInFaults:  false  
        |-InstanceContextMode:             PerSession  
        |-TransactionIsolationLevel:       Unspecified  
        |-TransactionTimeout:              null  
        |-ValidateMustUnderstand:          true  
      |-Behavior[1]  
      |-Type:                       AspNetCompatibilityRequirementsAttribute  
      |-Behavior[2]  
      |-Type:                       ServiceDebugBehavior  
      |-Behavior[3]  
      |-Type:                       ServiceAuthorizationBehavior  
      |-Behavior[4]  
      |-Type:                       Behavior  
```  
  
 <span data-ttu-id="c3375-128">Ensuite, exécutez le deuxième script Java pour afficher les données WMI définies par l'utilisateur :</span><span class="sxs-lookup"><span data-stu-id="c3375-128">Next, run the second Java Script to display the user-defined WMI data:</span></span>  
  
```  
cscript EnumerateCustomObjects.js  
```  
  
 <span data-ttu-id="c3375-129">Le script accède à l'instrumentation définie par l'utilisateur contenue dans les services et produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="c3375-129">The script accesses the user-defined instrumentation contained in the services and produces the following output:</span></span>  
  
```  
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 <span data-ttu-id="c3375-130">La sortie montre qu'un service unique s'exécute sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c3375-130">The output shows that there is a single service running on the computer.</span></span> <span data-ttu-id="c3375-131">Le service expose un point de terminaison qui implémente le contrat `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="c3375-131">The service exposes one endpoint that implements the `ICalculator` contract.</span></span> <span data-ttu-id="c3375-132">Les paramètres du comportement et de la liaison qui sont implémentés par le point de terminaison sont répertoriés comme la somme des éléments individuels de la pile de messagerie.</span><span class="sxs-lookup"><span data-stu-id="c3375-132">The settings of the behavior and binding that are implemented by the endpoint are listed as the sum of individual elements of the messaging stack.</span></span>  
  
 <span data-ttu-id="c3375-133">WMI ne se limite pas à exposer l'instrumentation de gestion WMI de l'infrastructure [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c3375-133">WMI is not limited to exposing the management instrumentation of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastructure.</span></span> <span data-ttu-id="c3375-134">L'application peut exposer ses propres éléments de données spécifiques au domaine à travers le même mécanisme.</span><span class="sxs-lookup"><span data-stu-id="c3375-134">The application can expose its own domain-specific data items through the same mechanism.</span></span> <span data-ttu-id="c3375-135">WMI est un mécanisme unifié pour l'inspection et le contrôle d'un service Web.</span><span class="sxs-lookup"><span data-stu-id="c3375-135">WMI is a unified mechanism for inspection and control of a Web service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c3375-136">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="c3375-136">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c3375-137">Vérifiez que vous avez exécuté le [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c3375-137">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c3375-138">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c3375-138">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="c3375-139">Publiez le schéma de services dans WMI en exécutant InstallUtil.exe (l'emplacement par défaut pour Installutil.exe est « %WINDIR%\Microsoft.NET\Framework\v4.0.30319 ») sur le fichier service.dll dans le répertoire d'hébergement.</span><span class="sxs-lookup"><span data-stu-id="c3375-139">Publish the services schema to WMI by running the InstallUtil.exe (the default locations for InstallUtil.exe is "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") on the service.dll file in the hosting directory.</span></span> <span data-ttu-id="c3375-140">Cette étape doit seulement être exécutée lorsque des modifications ont été apportées au fichier service.dll.</span><span class="sxs-lookup"><span data-stu-id="c3375-140">This step only needs to be executed when changes have been made to the service.dll file.</span></span> <span data-ttu-id="c3375-141">Pour plus d'informations, consultez Fourniture d'informations de gestion via l'instrumentation d'applications à l'adresse http://msdn.microsoft.com/fr-fr/library/ms186147.aspx dans la section « Comment : publier le schéma dans WMI pour une application instrumentée ».</span><span class="sxs-lookup"><span data-stu-id="c3375-141">For more information, see Providing Management Information by Instrumenting Applications at: http://msdn2.microsoft.com/library/ms186147.aspx in the "How To: Publish the Scheme to WMI for an Instrumented Application" section.</span></span>  
  
4.  <span data-ttu-id="c3375-142">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c3375-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c3375-143">Si vous avez installé [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] après avoir installé ASP.NET, vous devrez peut-être exécuter "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x pour donner l'autorisation au compte ASPNET de publier des objets WMI.</span><span class="sxs-lookup"><span data-stu-id="c3375-143">If you installed [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] after installing ASP.NET, you may need to run "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x to give the ASPNET account permission to publish WMI objects.</span></span>  
  
5.  <span data-ttu-id="c3375-144">Consultez les données de l'exemple révélées par WMI en utilisant la commande `cscript EnumerateServices.js` ou `cscript EnumerateCustomObjects.js`.</span><span class="sxs-lookup"><span data-stu-id="c3375-144">View data from the sample surfaced through WMI by using the commands: `cscript EnumerateServices.js` or `cscript EnumerateCustomObjects.js`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c3375-145">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c3375-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c3375-146">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="c3375-146">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c3375-147">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c3375-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c3375-148">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="c3375-148">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a><span data-ttu-id="c3375-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3375-149">See Also</span></span>  
 [<span data-ttu-id="c3375-150">Exemples d’analyse AppFabric</span><span class="sxs-lookup"><span data-stu-id="c3375-150">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
