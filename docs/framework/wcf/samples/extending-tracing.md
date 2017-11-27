---
title: Extending Tracing
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
caps.latest.revision: "28"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 235b1a8454d573264f0bbe3cd5f9809d88d08209
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="extending-tracing"></a><span data-ttu-id="2522a-102">Extending Tracing</span><span class="sxs-lookup"><span data-stu-id="2522a-102">Extending Tracing</span></span>
<span data-ttu-id="2522a-103">Cet exemple montre comment étendre la fonctionnalité de suivi [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] en écrivant les suivis de l'activité définie par l'utilisateur dans le code du client et du service.</span><span class="sxs-lookup"><span data-stu-id="2522a-103">This sample demonstrates how to extend the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] tracing feature by writing user-defined activity traces in client and service code.</span></span> <span data-ttu-id="2522a-104">Cela permet à l'utilisateur de créer des activités de suivi et de regrouper les suivis dans des unités de travail logiques.</span><span class="sxs-lookup"><span data-stu-id="2522a-104">This allows the user to create trace activities and group traces into logical units of work.</span></span> <span data-ttu-id="2522a-105">Il est également possible de mettre en corrélation des activités à travers des transferts (au sein du même point de terminaison) et la propagation (sur plusieurs points de terminaison).</span><span class="sxs-lookup"><span data-stu-id="2522a-105">It is also possible to correlate activities through transfers (within the same endpoint) and propagation (across endpoints).</span></span> <span data-ttu-id="2522a-106">Dans cet exemple, le suivi est activé à la fois pour le client et pour le service.</span><span class="sxs-lookup"><span data-stu-id="2522a-106">In this sample, tracing is enabled for both the client and the service.</span></span> <span data-ttu-id="2522a-107">Pour plus d’informations sur la façon d’activer le suivi dans les fichiers de configuration client et le service, consultez [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="2522a-107">For more information about how to enable tracing in client and service configuration files, see [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="2522a-108">Cet exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="2522a-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2522a-109">La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.</span><span class="sxs-lookup"><span data-stu-id="2522a-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2522a-110">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2522a-110">The samples may already be installed on your computer.</span></span> <span data-ttu-id="2522a-111">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="2522a-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2522a-112">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2522a-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2522a-113">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="2522a-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a><span data-ttu-id="2522a-114">Suivi et propagation d'activité</span><span class="sxs-lookup"><span data-stu-id="2522a-114">Tracing and Activity Propagation</span></span>  
 <span data-ttu-id="2522a-115">Le suivi d'activité défini par l'utilisateur permet à l'utilisateur de créer ses propres activités de suivi pour regrouper les suivis dans les unités de travail logiques, mettre en corrélation des activités par transfert et propagation et amoindrir les coûts de performance du suivi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] (le coût en espace disque d'un fichier journal, par exemple).</span><span class="sxs-lookup"><span data-stu-id="2522a-115">User-defined activity tracing allows the user to create their own trace activities to group traces into logical units of work, correlate activities through transfers and propagation, and lessen the performance cost of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tracing (for example, the disk space cost of a log file).</span></span>  
  
### <a name="adding-custom-sources"></a><span data-ttu-id="2522a-116">Ajout de sources personnalisées</span><span class="sxs-lookup"><span data-stu-id="2522a-116">Adding Custom Sources</span></span>  
 <span data-ttu-id="2522a-117">Les suivis définis par l'utilisateur peuvent être ajoutés à la fois au code du client et du service.</span><span class="sxs-lookup"><span data-stu-id="2522a-117">User-defined traces can be added to both client and service code.</span></span> <span data-ttu-id="2522a-118">Ajout de sources de suivi pour les fichiers de configuration client ou un service permettant à ces traces personnalisées à être enregistré et affiché dans le [outil Service Trace Viewer (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="2522a-118">Adding trace sources to the client or service configuration files allow for these custom traces to be recorded and displayed in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="2522a-119">Le code suivant montre comment ajouter une source de suivi définie par l'utilisateur nommée `ServerCalculatorTraceSource` au fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="2522a-119">The following code shows how to add a user-defined trace source named `ServerCalculatorTraceSource` to the configuration file.</span></span>  
  
```xml  
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
  
### <a name="correlating-activities"></a><span data-ttu-id="2522a-120">Mise en corrélation des activités</span><span class="sxs-lookup"><span data-stu-id="2522a-120">Correlating Activities</span></span>  
 <span data-ttu-id="2522a-121">Pour mettre directement en corrélation des activités sur plusieurs points de terminaison, l'attribut `propagateActivity` doit avoir la valeur `true` dans la source du suivi `System.ServiceModel`.</span><span class="sxs-lookup"><span data-stu-id="2522a-121">To correlate activities directly across endpoints, the `propagateActivity` attribute must be set to `true` in the `System.ServiceModel` trace source.</span></span> <span data-ttu-id="2522a-122">En outre, le suivi d'activité ServiceModel doit être désactivé pour propager des suivis sans traverser des activités [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2522a-122">Also, to propagate traces without going through [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] activities, ServiceModel Activity Tracing must be turned off.</span></span> <span data-ttu-id="2522a-123">C'est ce qu'illustre l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="2522a-123">This can be seen in the following code example.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2522a-124">La désactivation du suivi d'activité ServiceModel n'équivaut pas à désactiver le niveau de suivi, dénoté par la propriété `switchValue`.</span><span class="sxs-lookup"><span data-stu-id="2522a-124">Turning off ServiceModel Activity Tracing is not the same as having the trace level, denoted by the `switchValue` property, set to off.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessening-performance-cost"></a><span data-ttu-id="2522a-125">Réduction des coûts de performance</span><span class="sxs-lookup"><span data-stu-id="2522a-125">Lessening Performance Cost</span></span>  
 <span data-ttu-id="2522a-126">Le fait de désactiver `ActivityTracing` dans la source de suivi `System.ServiceModel` génère un fichier de suivi qui contient uniquement les suivis d'activité définis par l'utilisateur, sans inclure les suivis d'activité ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="2522a-126">Setting `ActivityTracing` to off in the `System.ServiceModel` trace source generates a trace file that contains only user-defined activity traces, without any of the ServiceModel activity traces included.</span></span> <span data-ttu-id="2522a-127">Ainsi, le fichier journal est beaucoup moins volumineux.</span><span class="sxs-lookup"><span data-stu-id="2522a-127">This results in a log file of much smaller size.</span></span> <span data-ttu-id="2522a-128">Toutefois, la possibilité de mettre en corrélation les suivis de traitement [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est perdue.</span><span class="sxs-lookup"><span data-stu-id="2522a-128">However, the opportunity to correlate [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] processing traces is lost.</span></span>  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2522a-129">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="2522a-129">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="2522a-130">Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2522a-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="2522a-131">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2522a-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="2522a-132">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2522a-132">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2522a-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2522a-133">See Also</span></span>  
 [<span data-ttu-id="2522a-134">Exemples d’analyse AppFabric</span><span class="sxs-lookup"><span data-stu-id="2522a-134">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
