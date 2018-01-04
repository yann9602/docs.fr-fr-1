---
title: "Suivi à l'aide d'un fichier texte"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56a82682-73c2-4b91-a206-4d8bb12c561b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f1d4b3f319d86dd463dabc8b71be7c76c7fef41f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="tracking-using-a-text-file"></a><span data-ttu-id="4f053-102">Suivi à l'aide d'un fichier texte</span><span class="sxs-lookup"><span data-stu-id="4f053-102">Tracking Using a Text File</span></span>
<span data-ttu-id="4f053-103">Cet exemple montre comment étendre le suivi dans [!INCLUDE[wf](../../../../includes/wf-md.md)] en créant un participant de suivi personnalisé.</span><span class="sxs-lookup"><span data-stu-id="4f053-103">This sample demonstrates how to extend tracking in [!INCLUDE[wf](../../../../includes/wf-md.md)] by creating a custom tracking participant.</span></span> <span data-ttu-id="4f053-104">Les participants de suivi sont des classes .NET Framework qui reçoivent des enregistrements de suivi du runtime lorsqu'ils sont émis.</span><span class="sxs-lookup"><span data-stu-id="4f053-104">Tracking participants are .NET Framework classes that receive tracking records from the runtime as they are emitted.</span></span> <span data-ttu-id="4f053-105">Vous pouvez créer un participant de suivi pour transporter les événements de suivi vers toute destination qui est requise pour votre scénario.</span><span class="sxs-lookup"><span data-stu-id="4f053-105">You can create a tracking participant to transport the tracking events to whichever destination is required for your scenario.</span></span> <span data-ttu-id="4f053-106">Par exemple, le participant de suivi ETW (Event Tracing for Windows, suivi d'événements pour Windows) est fourni dans le cadre du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4f053-106">For example, ETW (Event Tracing for Windows) Tracking Participant is provided as part of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="4f053-107">Dans cet exemple, le participant de suivi écrit les enregistrements au format XML dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="4f053-107">The tracking participant in this sample writes the records in XML format to a text file.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="4f053-108">Détails de l'exemple</span><span class="sxs-lookup"><span data-stu-id="4f053-108">Sample details</span></span>  
 <span data-ttu-id="4f053-109">Pour optimiser l'utilité et la fiabilité de votre participant de suivi, certaines étapes supplémentaires doivent être effectuées pour connecter correctement le participant de suivi au runtime.</span><span class="sxs-lookup"><span data-stu-id="4f053-109">To optimize the usefulness and robustness of your tracking participant, some additional steps must be completed to properly wire the tracking participant to the runtime.</span></span> <span data-ttu-id="4f053-110">Le tableau suivant décrit les classes utilisées dans cet exemple pour créer un participant de suivi qui soit conforme aux meilleures pratiques.</span><span class="sxs-lookup"><span data-stu-id="4f053-110">The following table describes the classes used in this sample to create a tracking participant that complies with best practices.</span></span>  
  
|<span data-ttu-id="4f053-111">Classe</span><span class="sxs-lookup"><span data-stu-id="4f053-111">Class</span></span>|<span data-ttu-id="4f053-112">Description</span><span class="sxs-lookup"><span data-stu-id="4f053-112">Description</span></span>|  
|-----------|-----------------|  
|`TextFileTrackingExtensionElement`|<span data-ttu-id="4f053-113">Un <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> est utilisé pour définir la section de configuration utilisée pour configurer le participant de suivi de fichier texte.</span><span class="sxs-lookup"><span data-stu-id="4f053-113">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> is used to define the configuration section used to configure the text file tracking participant.</span></span> <span data-ttu-id="4f053-114">Cela permet aux utilisateurs de spécifier la destination du fichier journal à l'aide de fichiers de configuration .NET Framework standard.</span><span class="sxs-lookup"><span data-stu-id="4f053-114">This allows users to specify the destination of the log file using standard .NET Framework configuration files.</span></span>|  
|`TextFileTrackingBehavior`|<span data-ttu-id="4f053-115">Les comportements dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] permettent aux utilisateurs d'injecter des extensions dans le runtime.</span><span class="sxs-lookup"><span data-stu-id="4f053-115">Behaviors in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] allow users to inject extensions into the runtime.</span></span> <span data-ttu-id="4f053-116">Ce comportement ajoute le participant de suivi au service lors du démarrage de ce dernier.</span><span class="sxs-lookup"><span data-stu-id="4f053-116">This behavior adds the tracking participant to the service when the service starts.</span></span>|  
|`TextFileTrackingParticipant`|<span data-ttu-id="4f053-117">Participant de suivi qui reçoit des participants de suivi au moment de l'exécution et les stocke à un fichier journal au format XML.</span><span class="sxs-lookup"><span data-stu-id="4f053-117">The tracking participant that receives tracking participants at runtime and stores them to a log file as XML.</span></span>|  
  
## <a name="behavior-extension-elements-configuration"></a><span data-ttu-id="4f053-118">Configuration des éléments d'extension de comportement</span><span class="sxs-lookup"><span data-stu-id="4f053-118">Behavior Extension Elements Configuration</span></span>  
 <span data-ttu-id="4f053-119">Une étape supplémentaire est requise pour utiliser l'élément d'extension de comportement décrite précédemment à l'aide de fichiers de configuration .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4f053-119">One more step is required to make use of the behavior extension element previously described using .NET Framework configuration files.</span></span> <span data-ttu-id="4f053-120">La configuration suivante doit être placée dans les fichiers de configuration où l'extension doit être utilisée.</span><span class="sxs-lookup"><span data-stu-id="4f053-120">The following configuration must be placed in configuration files where the extension is to be used.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
      <behaviorExtensions>  
        <add name="textFileTracking" type="Microsoft.Samples.TextFileTracking.TextFileTrackingExtensionElement, WFStockPriceApplication, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </behaviorExtensions>  
    </extensions>  
…  
  </system.serviceModel>  
```  
  
> [!NOTE]
>  <span data-ttu-id="4f053-121">Pour obtenir un exemple d'utilisation complet de configuration d'éléments d'extension de comportement, consultez le fichier Web.config disponible dans l'exemple.</span><span class="sxs-lookup"><span data-stu-id="4f053-121">See the Web.config file in the sample for a complete example usage of behavior extension elements configuration.</span></span>  
  
## <a name="custom-tracking-records"></a><span data-ttu-id="4f053-122">Enregistrements de suivi personnalisé</span><span class="sxs-lookup"><span data-stu-id="4f053-122">Custom Tracking Records</span></span>  
 <span data-ttu-id="4f053-123">Le fichier GetStockPrices.cs montre comment créer des enregistrements de suivi personnalisé à partir d'un <xref:System.Activities.CodeActivity>.</span><span class="sxs-lookup"><span data-stu-id="4f053-123">The GetStockPrices.cs file demonstrates how to create custom tracking records from within a <xref:System.Activities.CodeActivity>.</span></span> <span data-ttu-id="4f053-124">Recherchez cet enregistrement lorsque l'exemple est exécuté.</span><span class="sxs-lookup"><span data-stu-id="4f053-124">Look for this record when running the sample.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="4f053-125">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="4f053-125">To use this sample</span></span>  
  
1.  <span data-ttu-id="4f053-126">À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution WFStockPriceApplication.sln.</span><span class="sxs-lookup"><span data-stu-id="4f053-126">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the WFStockPriceApplication.sln solution file.</span></span>  
  
2.  <span data-ttu-id="4f053-127">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="4f053-127">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="4f053-128">Pour exécuter la solution, appuyez sur Ctrl+F5.</span><span class="sxs-lookup"><span data-stu-id="4f053-128">To run the solution, press CTRL+F5.</span></span>  
  
     <span data-ttu-id="4f053-129">La fenêtre du navigateur s'ouvre et affiche la liste des répertoires pour l'application.</span><span class="sxs-lookup"><span data-stu-id="4f053-129">The browser window opens and shows the directory listing for the application.</span></span>  
  
4.  <span data-ttu-id="4f053-130">Dans le navigateur, cliquez sur StockPriceService.xamlx.</span><span class="sxs-lookup"><span data-stu-id="4f053-130">In the browser, click StockPriceService.xamlx.</span></span>  
  
5.  <span data-ttu-id="4f053-131">Le navigateur affiche le **StockPriceService** page qui contient l’adresse wsdl du service local.</span><span class="sxs-lookup"><span data-stu-id="4f053-131">The browser displays the **StockPriceService** page, which contains the local service wsdl address.</span></span> <span data-ttu-id="4f053-132">Copiez cette adresse.</span><span class="sxs-lookup"><span data-stu-id="4f053-132">Copy this address.</span></span>  
  
     <span data-ttu-id="4f053-133">L'adresse WSDL du service local est, par exemple, http://localhost:53797/StockPriceService.xamlx?wsdl.</span><span class="sxs-lookup"><span data-stu-id="4f053-133">An example of the local service wsdl address is http://localhost:53797/StockPriceService.xamlx?wsdl.</span></span>  
  
6.  <span data-ttu-id="4f053-134">À l'aide de l'[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], accédez à votre dossier [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] (le dossier d'installation par défaut est %SystemDrive%\Program Files\Microsoft Visual Studio 10.0).</span><span class="sxs-lookup"><span data-stu-id="4f053-134">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], go to your [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] folder (the default installation folder is %SystemDrive%\Program Files\Microsoft Visual Studio 10.0).</span></span> <span data-ttu-id="4f053-135">Recherchez le sous-dossier Common7\IDE.</span><span class="sxs-lookup"><span data-stu-id="4f053-135">Then locate the Common7\IDE\ subfolder.</span></span>  
  
7.  <span data-ttu-id="4f053-136">Double-cliquez sur le fichier WcfTestClient.exe pour lancer le client test WCF.</span><span class="sxs-lookup"><span data-stu-id="4f053-136">Double-click the WcfTestClient.exe file to launch the WCF Test Client.</span></span>  
  
8.  <span data-ttu-id="4f053-137">Dans le Client Test WCF, sélectionnez **ajouter un Service en cours...**</span><span class="sxs-lookup"><span data-stu-id="4f053-137">In the WCF Test Client, select **Add Service…**</span></span> <span data-ttu-id="4f053-138">à partir de la **fichier** menu.</span><span class="sxs-lookup"><span data-stu-id="4f053-138">from the **File** menu.</span></span>  
  
9. <span data-ttu-id="4f053-139">Collez l'URL que vous venez de copier dans la zone de texte.</span><span class="sxs-lookup"><span data-stu-id="4f053-139">Paste the URL you just copied into the text box.</span></span>  
  
10. <span data-ttu-id="4f053-140">Cliquez sur **OK** pour fermer la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="4f053-140">Click **OK** to close the dialog.</span></span>  
  
11. <span data-ttu-id="4f053-141">Testez le service à l'aide du client test WCF.</span><span class="sxs-lookup"><span data-stu-id="4f053-141">Test the service using the WCF Test Client.</span></span>  
  
    1.  <span data-ttu-id="4f053-142">Dans le Client Test WCF, double-cliquez sur **GetStockPrice()** sous le **IStockPriceService** nœud.</span><span class="sxs-lookup"><span data-stu-id="4f053-142">In the WCF Test Client, double-click **GetStockPrice()** under the **IStockPriceService** node.</span></span>  
  
         <span data-ttu-id="4f053-143">Le **GetStockPrice()** méthode s’affiche dans le volet droit, avec un paramètre.</span><span class="sxs-lookup"><span data-stu-id="4f053-143">The **GetStockPrice()** method appears in the right pane, with one parameter.</span></span>  
  
    2.  <span data-ttu-id="4f053-144">Tapez Contoso comme valeur pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="4f053-144">Type in Contoso as the value for the parameter.</span></span>  
  
    3.  <span data-ttu-id="4f053-145">Cliquez sur **appeler**.</span><span class="sxs-lookup"><span data-stu-id="4f053-145">Click **Invoke**.</span></span>  
  
12. <span data-ttu-id="4f053-146">Consultez les événements suivis dans le fichier journal situé dans votre répertoire de données d'application dans %APPDATA%\trackingRecords.log.</span><span class="sxs-lookup"><span data-stu-id="4f053-146">See the tracked events in the log file located in your application data directory at %APPDATA%\trackingRecords.log.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4f053-147">%AppData% est une variable d’environnement qui se résout en %SystemDrive%\Users\\< nom d’utilisateur\>\AppData\Roaming dans [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], ou Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="4f053-147">The %APPDATA% is an environment variable that resolves to %SystemDrive%\Users\\<username\>\AppData\Roaming in [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], or Windows Server 2008.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4f053-148">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="4f053-148">The samples may already be installed on your computer.</span></span> <span data-ttu-id="4f053-149">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="4f053-149">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4f053-150">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4f053-150">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4f053-151">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="4f053-151">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\TextFileTracking`  
  
## <a name="see-also"></a><span data-ttu-id="4f053-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f053-152">See Also</span></span>  
 [<span data-ttu-id="4f053-153">Exemples d’analyse AppFabric</span><span class="sxs-lookup"><span data-stu-id="4f053-153">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
