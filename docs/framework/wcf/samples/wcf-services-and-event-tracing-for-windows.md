---
title: "WCF Services et suivi d'événements Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 809b48a27e5923db585d6125df0d2f55c96a4765
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="wcf-services-and-event-tracing-for-windows"></a><span data-ttu-id="65f32-102">WCF Services et suivi d'événements Windows</span><span class="sxs-lookup"><span data-stu-id="65f32-102">WCF Services and Event Tracing for Windows</span></span>
<span data-ttu-id="65f32-103">Cet exemple montre comment utiliser le traçage analytique dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pour émettre des événements dans le suivi d'événements pour Windows (ETW, Event Tracing for Windows).</span><span class="sxs-lookup"><span data-stu-id="65f32-103">This sample demonstrates how to use the analytic tracing in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to emit events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="65f32-104">Les traces analytiques sont des événements émis à des points clés dans la pile [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui permettent de résoudre des problèmes liés aux services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dans un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="65f32-104">The analytic traces are events emitted at key points in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] stack that allow troubleshooting of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services in production environment.</span></span>  
  
 <span data-ttu-id="65f32-105">La trace analytique des services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est un suivi qui peut être activé dans un environnement de production avec un impact minime sur les performances.</span><span class="sxs-lookup"><span data-stu-id="65f32-105">Analytic trace in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services is tracing that can be turned on in a production environment with minimal impact on performance.</span></span> <span data-ttu-id="65f32-106">Ces traces sont émises en tant qu'événements dans une session de suivi ETW.</span><span class="sxs-lookup"><span data-stu-id="65f32-106">These traces are emitted as events to an ETW session.</span></span>  
  
 <span data-ttu-id="65f32-107">Cet exemple inclut un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de base dans lequel des événements sont émis du service au journal des événements, lequel peut être consulté à l'aide de l'Observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="65f32-107">This sample includes a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service in which events are emitted from the service to the event log, which can be viewed using Event Viewer.</span></span> <span data-ttu-id="65f32-108">Il est également possible de démarrer une session de suivi ETW dédiée qui écoute les événements du service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="65f32-108">It is also possible to start a dedicated ETW session that listens for events from the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="65f32-109">L'exemple comprend un script permettant de créer une session de suivi ETW dédiée qui stocke des événements dans un fichier binaire pouvant être lu à l'aide de l'Observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="65f32-109">The sample includes a script to create a dedicated ETW session that stores events in a binary file that can be read using Event Viewer.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="65f32-110">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="65f32-110">To use this sample</span></span>  
  
1.  <span data-ttu-id="65f32-111">À l'aide de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ouvrez le fichier solution EtwAnalyticTraceSample.sln.</span><span class="sxs-lookup"><span data-stu-id="65f32-111">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the EtwAnalyticTraceSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="65f32-112">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="65f32-112">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="65f32-113">Pour exécuter la solution, appuyez sur Ctrl+F5.</span><span class="sxs-lookup"><span data-stu-id="65f32-113">To run the solution, press CTRL+F5.</span></span>  
  
     <span data-ttu-id="65f32-114">Dans le navigateur Web, cliquez sur **Calculator.svc**.</span><span class="sxs-lookup"><span data-stu-id="65f32-114">In the Web browser, click **Calculator.svc**.</span></span> <span data-ttu-id="65f32-115">L'URI du document WSDL du service doit s'afficher dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="65f32-115">The URI of the WSDL document for the service should appear in the browser.</span></span> <span data-ttu-id="65f32-116">Copiez cet URI.</span><span class="sxs-lookup"><span data-stu-id="65f32-116">Copy that URI.</span></span>  
  
     <span data-ttu-id="65f32-117">Par défaut, le service commence à écouter les requêtes sur le port 1378 (http://localhost:1378/Calculator.svc).</span><span class="sxs-lookup"><span data-stu-id="65f32-117">By default, the service starts listening for requests on port 1378 (http://localhost:1378/Calculator.svc).</span></span>  
  
4.  <span data-ttu-id="65f32-118">Exécutez le client test [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] (WcfTestClient.exe).</span><span class="sxs-lookup"><span data-stu-id="65f32-118">Run the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client (WcfTestClient.exe).</span></span>  
  
     <span data-ttu-id="65f32-119">Le [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client de test (WcfTestClient.exe) se trouve dans le \< [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Répertoire_installation_ > \Common7\IDE\ WcfTestClient.exe (valeur par défaut [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] est C:\Program Files\Microsoft Visual Studio 10.0).</span><span class="sxs-lookup"><span data-stu-id="65f32-119">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client (WcfTestClient.exe) is located in the \<[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Install Dir>\Common7\IDE\ WcfTestClient.exe (default [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] install dir is C:\Program Files\Microsoft Visual Studio 10.0).</span></span>  
  
5.  <span data-ttu-id="65f32-120">Dans le [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client de test, ajoutez le service en sélectionnant **fichier**, puis **ajouter un Service**.</span><span class="sxs-lookup"><span data-stu-id="65f32-120">Within the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client, add the service by selecting **File**, and then **Add Service**.</span></span>  
  
     <span data-ttu-id="65f32-121">Ajoutez l'adresse du point de terminaison dans la zone d'entrée.</span><span class="sxs-lookup"><span data-stu-id="65f32-121">Add the endpoint address in the input box.</span></span> <span data-ttu-id="65f32-122">La valeur par défaut est http://localhost:1378/Calculator.svc.</span><span class="sxs-lookup"><span data-stu-id="65f32-122">The default is http://localhost:1378/Calculator.svc.</span></span>  
  
6.  <span data-ttu-id="65f32-123">Ouvrez l'application Observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="65f32-123">Open the Event Viewer application.</span></span>  
  
     <span data-ttu-id="65f32-124">Avant d'appeler le service, démarrez l'Observateur d'événements et vérifiez que le journal des événements écoute les événements de suivi émis à partir du service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="65f32-124">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
7.  <span data-ttu-id="65f32-125">À partir de la **Démarrer** menu, sélectionnez **outils d’administration**, puis **Observateur d’événements**.</span><span class="sxs-lookup"><span data-stu-id="65f32-125">From the **Start** menu, select **Administrative Tools**, and then **Event Viewer**.</span></span>  <span data-ttu-id="65f32-126">Activer la **analyse** et **déboguer** journaux.</span><span class="sxs-lookup"><span data-stu-id="65f32-126">Enable the **Analytic** and **Debug** logs.</span></span>  
  
8.  <span data-ttu-id="65f32-127">Dans l’arborescence de commandes dans l’Observateur d’événements, accédez à **Observateur d’événements**, **journaux des Applications et Services**, **Microsoft**, **Windows**, puis **Serveur d’applications-Applications**.</span><span class="sxs-lookup"><span data-stu-id="65f32-127">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="65f32-128">Avec le bouton droit **serveur d’applications-Applications**, sélectionnez **vue**, puis **afficher les journaux d’analyse et de débogage**.</span><span class="sxs-lookup"><span data-stu-id="65f32-128">Right-click **Application Server-Applications**, select **View**, and then **Show Analytic and Debug Logs**.</span></span>  
  
     <span data-ttu-id="65f32-129">Vérifiez que le **afficher les journaux d’analyse et de débogage** option est activée.</span><span class="sxs-lookup"><span data-stu-id="65f32-129">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>  
  
9. <span data-ttu-id="65f32-130">Activer la **analyse** journal.</span><span class="sxs-lookup"><span data-stu-id="65f32-130">Enable the **Analytic** log.</span></span>  
  
     <span data-ttu-id="65f32-131">Dans l’arborescence de commandes dans l’Observateur d’événements, accédez à **Observateur d’événements**, **journaux des Applications et Services**, **Microsoft**, **Windows**, puis **Serveur d’applications-Applications**.</span><span class="sxs-lookup"><span data-stu-id="65f32-131">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="65f32-132">Avec le bouton droit **analyse** et sélectionnez **activer le journal**.</span><span class="sxs-lookup"><span data-stu-id="65f32-132">Right-click **Analytic** and select **Enable Log**.</span></span>  
  
#### <a name="to-test-the-service"></a><span data-ttu-id="65f32-133">Pour tester le service</span><span class="sxs-lookup"><span data-stu-id="65f32-133">To test the service</span></span>  
  
1.  <span data-ttu-id="65f32-134">Revenez au client test [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], double-cliquez sur `Divide` et conservez les valeurs par défaut, qui spécifient le dénominateur 0.</span><span class="sxs-lookup"><span data-stu-id="65f32-134">Switch back to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client and double-click `Divide` and keep the default values, which specify a denominator of 0.</span></span>  
  
     <span data-ttu-id="65f32-135">Si le dénominateur est 0, le service génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="65f32-135">If the denominator is 0, then the service throws a fault.</span></span>  
  
2.  <span data-ttu-id="65f32-136">Observez les événements émis par le service.</span><span class="sxs-lookup"><span data-stu-id="65f32-136">Observe the events emitted from the service.</span></span>  
  
     <span data-ttu-id="65f32-137">Revenez à l’Observateur d’événements et naviguez jusqu'à **Observateur d’événements**, **journaux des Applications et Services**, **Microsoft**, **Windows**, puis **Serveur d’applications-Applications**.</span><span class="sxs-lookup"><span data-stu-id="65f32-137">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="65f32-138">Avec le bouton droit **analyse** et sélectionnez **Actualiser**.</span><span class="sxs-lookup"><span data-stu-id="65f32-138">Right-click **Analytic** and select **Refresh**.</span></span>  
  
     <span data-ttu-id="65f32-139">Les événements du traçage analytique de WCF s'affichent dans l'Observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="65f32-139">The WCF analytic trace events are displayed in the event viewer.</span></span> <span data-ttu-id="65f32-140">Notez qu'en raison de l'erreur générée par le service, un événement de trace d'erreur est visible dans l'Observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="65f32-140">Notice that because a fault was thrown by the service an error trace event is displayed in the event viewer.</span></span>  
  
3.  <span data-ttu-id="65f32-141">Répétez les étapes 1 et 2, mais avec des entrées valides.</span><span class="sxs-lookup"><span data-stu-id="65f32-141">Repeat steps 1 and 2, but with valid inputs.</span></span> <span data-ttu-id="65f32-142">La valeur du paramètre `N2` peut être n'importe quel nombre différent de 0.</span><span class="sxs-lookup"><span data-stu-id="65f32-142">The value of the `N2` parameter can be any number other than 0.</span></span>  
  
     <span data-ttu-id="65f32-143">Actualisez le canal analytique pour constater que les événements WCF n'incluent aucun événement d'erreur.</span><span class="sxs-lookup"><span data-stu-id="65f32-143">Refresh the analytic channel to view the WCF events do not include any error events.</span></span>  
  
 <span data-ttu-id="65f32-144">L'exemple montre les événements de trace analytique émis par un service WCF.</span><span class="sxs-lookup"><span data-stu-id="65f32-144">The sample demonstrates the analytic trace events emitted from a WCF service.</span></span>  
  
#### <a name="to-cleanup-optional"></a><span data-ttu-id="65f32-145">Pour effectuer un nettoyage (facultatif)</span><span class="sxs-lookup"><span data-stu-id="65f32-145">To cleanup (Optional)</span></span>  
  
1.  <span data-ttu-id="65f32-146">Ouvrez l'observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="65f32-146">Open Event Viewer.</span></span>  
  
2.  <span data-ttu-id="65f32-147">Accédez à **Observateur d’événements**, **journaux des Applications et Services**, **Microsoft**, **Windows**, puis  **Serveur d’applications-Applications**.</span><span class="sxs-lookup"><span data-stu-id="65f32-147">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="65f32-148">Avec le bouton droit **analyse** et sélectionnez **désactiver le journal**.</span><span class="sxs-lookup"><span data-stu-id="65f32-148">Right-click **Analytic** and select **Disable Log**.</span></span>  
  
3.  <span data-ttu-id="65f32-149">Accédez à **Observateur d’événements**, **journaux des Applications et Services**, **Microsoft**, **Windows**, puis  **Serveur d’applications-Applications**.</span><span class="sxs-lookup"><span data-stu-id="65f32-149">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="65f32-150">Avec le bouton droit **analyse** et sélectionnez **effacer le journal**.</span><span class="sxs-lookup"><span data-stu-id="65f32-150">Right-click **Analytic** and select **Clear Log**.</span></span>  
  
4.  <span data-ttu-id="65f32-151">Choisissez le **effacer** option pour effacer les événements.</span><span class="sxs-lookup"><span data-stu-id="65f32-151">Choose the **Clear** option to clear the events.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="65f32-152">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="65f32-152">The samples may already be installed on your computer.</span></span> <span data-ttu-id="65f32-153">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="65f32-153">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="65f32-154">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="65f32-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="65f32-155">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="65f32-155">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a><span data-ttu-id="65f32-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="65f32-156">See Also</span></span>  
 [<span data-ttu-id="65f32-157">Exemples d’analyse AppFabric</span><span class="sxs-lookup"><span data-stu-id="65f32-157">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
