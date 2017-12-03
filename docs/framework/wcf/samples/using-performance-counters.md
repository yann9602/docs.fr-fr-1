---
title: Using Performance Counters
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5963a1b2600066020562c1d17b0d2d2eb6eb67c8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="using-performance-counters"></a><span data-ttu-id="78a1b-102">Using Performance Counters</span><span class="sxs-lookup"><span data-stu-id="78a1b-102">Using Performance Counters</span></span>
<span data-ttu-id="78a1b-103">Cet exemple montre comment accéder aux compteurs de performance [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et comment créer des compteurs de performance définis par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="78a1b-103">This sample demonstrates how to access [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] performance counters and how to create user-defined performance counters.</span></span> <span data-ttu-id="78a1b-104">Cet exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="78a1b-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="78a1b-105">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="78a1b-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="78a1b-106">Dans cet exemple, le client appelle les quatre méthodes du service `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="78a1b-106">In this sample, the client calls the four methods of the `ICalculator` service.</span></span> <span data-ttu-id="78a1b-107">Le client continue jusqu'à ce qu'il soit interrompu par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="78a1b-107">The client continues to do this until it is interrupted by the user.</span></span> <span data-ttu-id="78a1b-108">Le service reste inchangé.</span><span class="sxs-lookup"><span data-stu-id="78a1b-108">The service remains unchanged.</span></span>  
  
 <span data-ttu-id="78a1b-109">Les compteurs de performance sont activés dans la section de diagnostic du fichier Web.config pour le service, comme le montre l'exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="78a1b-109">Performance counters are enabled in the diagnostics section of the Web.config file for the service, as shown in the following sample configuration.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />   
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="78a1b-110">Cette tâche peut également être effectuée à l’aide de la [l’outil Éditeur de Configuration (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="78a1b-110">This task can also be done using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="78a1b-111">Lorsque les compteurs de performance sont activés, la suite entière de compteurs de performance [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est activée pour le service.</span><span class="sxs-lookup"><span data-stu-id="78a1b-111">When performance counters are enabled, the entire suite of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] performance counters is enabled for the service.</span></span> <span data-ttu-id="78a1b-112">Le .NET Framework assure automatiquement la maintenance des données de performance à trois niveaux : `ServiceModelService`, `ServiceModelEndpoint` et `ServiceModelOperation`.</span><span class="sxs-lookup"><span data-stu-id="78a1b-112">The .NET Framework automatically maintains performance data at three levels: `ServiceModelService`, `ServiceModelEndpoint` and `ServiceModelOperation`.</span></span> <span data-ttu-id="78a1b-113">Chacun de ces niveaux comporte des compteurs de performance tels que « Appels », « Appels par seconde », et « Appels de sécurité non autorisés ».</span><span class="sxs-lookup"><span data-stu-id="78a1b-113">Each of these levels has performance counters such as "Calls", "Calls per Second", and "Security Calls Not Authorized".</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="78a1b-114">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="78a1b-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="78a1b-115">Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="78a1b-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="78a1b-116">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="78a1b-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="78a1b-117">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="78a1b-117">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-view-performance-data"></a><span data-ttu-id="78a1b-118">Pour afficher les données de performances</span><span class="sxs-lookup"><span data-stu-id="78a1b-118">To view performance data</span></span>  
  
1.  <span data-ttu-id="78a1b-119">Démarrez l’outil Analyseur de performances en cliquant sur **Démarrer**, **exécuter...** , entrez `perfmon` et cliquez sur **OK,** ou, dans le panneau de configuration, sélectionnez **outils d’administration** et double-cliquez sur **performances**.</span><span class="sxs-lookup"><span data-stu-id="78a1b-119">Start the Performance Monitor Tool by clicking **Start**, **Run…**, enter `perfmon` and click **OK,** or from Control Panel, select **Administrative Tools** and double-click **Performance**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="78a1b-120">Vous ne pouvez pas ajouter de compteurs tant que l'exemple de code est en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="78a1b-120">You cannot add counters until the sample code is running.</span></span>  
  
2.  <span data-ttu-id="78a1b-121">Supprimez les compteurs de performance répertoriés en les sélectionnant et en appuyant sur la touche Suppr.</span><span class="sxs-lookup"><span data-stu-id="78a1b-121">Remove the performance counters that are listed by selecting them and pressing the Delete key.</span></span>  
  
3.  <span data-ttu-id="78a1b-122">Ajouter [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] compteurs en cliquant sur le volet du graphique et en sélectionnant **ajouter des compteurs**.</span><span class="sxs-lookup"><span data-stu-id="78a1b-122">Add [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] counters by right-clicking the graph pane and selecting **Add Counters**.</span></span> <span data-ttu-id="78a1b-123">Dans le **ajouter des compteurs** boîte de dialogue, sélectionnez **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0 ou ServiceModelService 3.0.0.0** dans l’objet de Performance, faites glisser la zone de liste.</span><span class="sxs-lookup"><span data-stu-id="78a1b-123">In the **Add Counters** dialog box, select **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0, or ServiceModelService 3.0.0.0** in the Performance object drop down list box.</span></span> <span data-ttu-id="78a1b-124">Sélectionnez les compteurs que vous souhaitez afficher dans la liste.</span><span class="sxs-lookup"><span data-stu-id="78a1b-124">Select the counters you want to view from the list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="78a1b-125">Il n'y a pas de compteurs de performance [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour un service s'il n'y a pas de services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] en cours d'exécution sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="78a1b-125">There are no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] performance counters for a service if there are no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services running on the computer.</span></span>  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a><span data-ttu-id="78a1b-126">Pour utiliser l'Éditeur de configuration afin d'activer des compteurs</span><span class="sxs-lookup"><span data-stu-id="78a1b-126">To use the Configuration Editor to enable counters</span></span>  
  
1.  <span data-ttu-id="78a1b-127">Ouvrez une instance de SvcConfigEditor.exe.</span><span class="sxs-lookup"><span data-stu-id="78a1b-127">Open an instance of the SvcConfigEditor.exe.</span></span>  
  
2.  <span data-ttu-id="78a1b-128">Dans le menu fichier, cliquez sur **ouvrir** , puis **le fichier de configuration...** .</span><span class="sxs-lookup"><span data-stu-id="78a1b-128">On the File menu, click **Open** and then click **Config file…**.</span></span>  
  
3.  <span data-ttu-id="78a1b-129">Naviguez jusqu’au dossier de service de l’exemple d’application et ouvrez le fichier Web.config.</span><span class="sxs-lookup"><span data-stu-id="78a1b-129">Navigate to the sample application's service folder and open the Web.config file.</span></span>  
  
4.  <span data-ttu-id="78a1b-130">Cliquez sur **Diagnostics** sur l’arborescence de la Configuration.</span><span class="sxs-lookup"><span data-stu-id="78a1b-130">Click **Diagnostics** on the Configuration tree.</span></span>  
  
5.  <span data-ttu-id="78a1b-131">Activer/désactiver **compteur de Performance** dans les **Diagnostics** fenêtre 'All'.</span><span class="sxs-lookup"><span data-stu-id="78a1b-131">Toggle **Performance Counter** in the **Diagnostics** window to show 'All'.</span></span>  
  
6.  <span data-ttu-id="78a1b-132">Enregistrez le fichier de configuration et quittez l'éditeur.</span><span class="sxs-lookup"><span data-stu-id="78a1b-132">Save the configuration file and exit the editor.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="78a1b-133">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="78a1b-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="78a1b-134">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="78a1b-134">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="78a1b-135">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="78a1b-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="78a1b-136">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="78a1b-136">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a><span data-ttu-id="78a1b-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78a1b-137">See Also</span></span>  
 [<span data-ttu-id="78a1b-138">Exemples d’analyse AppFabric</span><span class="sxs-lookup"><span data-stu-id="78a1b-138">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
