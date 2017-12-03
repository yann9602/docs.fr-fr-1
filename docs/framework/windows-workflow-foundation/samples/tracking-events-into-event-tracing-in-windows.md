---
title: "Événements de suivi dans Event Tracing for Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f812659b-0943-45ff-9430-4defa733182b
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 12dd8ee58b577df1ef7d54e8f820ff183cef6084
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="tracking-events-into-event-tracing-in-windows"></a><span data-ttu-id="c9a18-102">Événements de suivi dans Event Tracing for Windows</span><span class="sxs-lookup"><span data-stu-id="c9a18-102">Tracking Events into Event Tracing in Windows</span></span>
<span data-ttu-id="c9a18-103">Cet exemple montre comment activer le suivi [!INCLUDE[wf](../../../../includes/wf-md.md)] sur un service de workflow et émettre les événements de suivi dans le suivi d'événements pour Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="c9a18-103">This sample demonstrates how to enable [!INCLUDE[wf](../../../../includes/wf-md.md)] tracking on a workflow service and emit the tracking events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="c9a18-104">Pour émettre des enregistrements de suivi de workflow dans ETW, l'exemple utilise le participant de suivi ETW (<xref:System.Activities.Tracking.EtwTrackingParticipant>).</span><span class="sxs-lookup"><span data-stu-id="c9a18-104">To emit workflow tracking records into ETW, the sample uses the ETW tracking participant (<xref:System.Activities.Tracking.EtwTrackingParticipant>).</span></span>  
  
 <span data-ttu-id="c9a18-105">Le workflow dans l'exemple reçoit une demande, assigne la réciproque des données d'entrée à la variable d'entrée et retourne la réciproque au client.</span><span class="sxs-lookup"><span data-stu-id="c9a18-105">The workflow in the sample receives a request, assigns the reciprocal of the input data to the input variable and returns the reciprocal back to the client.</span></span> <span data-ttu-id="c9a18-106">Lorsque les données d'entrée sont égales à 0, une exception de division par zéro qui n'est pas gérée et provoque l'abandon du workflow se produit.</span><span class="sxs-lookup"><span data-stu-id="c9a18-106">When the input data is 0, a divide by zero exception occurs that is unhandled that causes the workflow to abort.</span></span> <span data-ttu-id="c9a18-107">Lorsque le suivi est activé, l'enregistrement de suivi des erreurs est émis dans ETW, ce qui peut aider à corriger l'erreur ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="c9a18-107">With tracking enabled, the error track record is emitted to ETW, which can help troubleshoot the error later.</span></span> <span data-ttu-id="c9a18-108">Le participant de suivi ETW est configuré avec un modèle de suivi pour s'abonner aux enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="c9a18-108">The ETW tracking participant is configured with a tracking profile to subscribe to tracking records.</span></span> <span data-ttu-id="c9a18-109">Le modèle de suivi est défini dans le fichier Web.config et fourni comme paramètre de configuration au participant de suivi ETW.</span><span class="sxs-lookup"><span data-stu-id="c9a18-109">The tracking profile is defined in the Web.config file and provided as a configuration parameter to the ETW tracking participant.</span></span> <span data-ttu-id="c9a18-110">Le participant de suivi ETW est configuré dans le fichier Web.config du service de workflow et appliqué au service comme comportement de service.</span><span class="sxs-lookup"><span data-stu-id="c9a18-110">The ETW tracking participant is configured in the Web.config file of the workflow service and is applied to the service as a service behavior.</span></span> <span data-ttu-id="c9a18-111">Dans cet exemple, vous consultez les événements de suivi dans le journal des événements à l'aide de l'observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="c9a18-111">In this sample, you view the tracking events in the event log using Event Viewer.</span></span>  
  
## <a name="workflow-tracking-details"></a><span data-ttu-id="c9a18-112">Détails de suivi de workflow</span><span class="sxs-lookup"><span data-stu-id="c9a18-112">Workflow Tracking Details</span></span>  
 [!INCLUDE[wf2](../../../../includes/wf2-md.md)]<span data-ttu-id="c9a18-113"> fournit une infrastructure de suivi pour suivre l'exécution d'une instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="c9a18-113"> provides a tracking infrastructure to track the execution of a workflow instance.</span></span> <span data-ttu-id="c9a18-114">Le runtime de suivi crée une instance de workflow pour émettre des événements associés au cycle de vie de workflow, événements des activités de workflow et événements personnalisés.</span><span class="sxs-lookup"><span data-stu-id="c9a18-114">The tracking runtime creates a workflow instance to emit events related to the workflow lifecycle, events from workflow activities and custom events.</span></span> <span data-ttu-id="c9a18-115">Le tableau suivant détaille les composants principaux de l'infrastructure de suivi.</span><span class="sxs-lookup"><span data-stu-id="c9a18-115">The following table details the primary components of the tracking infrastructure.</span></span>  
  
|<span data-ttu-id="c9a18-116">Composant</span><span class="sxs-lookup"><span data-stu-id="c9a18-116">Component</span></span>|<span data-ttu-id="c9a18-117">Description</span><span class="sxs-lookup"><span data-stu-id="c9a18-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c9a18-118">Runtime de suivi</span><span class="sxs-lookup"><span data-stu-id="c9a18-118">Tracking runtime</span></span>|<span data-ttu-id="c9a18-119">Fournit l'infrastructure permettant d'émettre des enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="c9a18-119">Provides the infrastructure to emit tracking records.</span></span>|  
|<span data-ttu-id="c9a18-120">Participants de suivi</span><span class="sxs-lookup"><span data-stu-id="c9a18-120">Tracking participants</span></span>|<span data-ttu-id="c9a18-121">Accède aux enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="c9a18-121">Accesses the tracking records.</span></span> [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]<span data-ttu-id="c9a18-122"> est fourni avec un participant de suivi qui écrit les enregistrements de suivi sous la forme d'événements Suivi d'événements pour Windows (ETW, Event Tracing for Windows).</span><span class="sxs-lookup"><span data-stu-id="c9a18-122"> ships with a tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span>|  
|<span data-ttu-id="c9a18-123">Modèle de suivi</span><span class="sxs-lookup"><span data-stu-id="c9a18-123">Tracking profile</span></span>|<span data-ttu-id="c9a18-124">Mécanisme de filtrage qui permet à un participant de suivi de s'abonner à un sous-ensemble des enregistrements de suivi émis à partir d'une instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="c9a18-124">A filtering mechanism that allows a tracking participant to subscribe for a subset of the tracking records emitted from a workflow instance.</span></span>|  
  
 <span data-ttu-id="c9a18-125">Le tableau suivant détaille les enregistrements de suivi que l'exécution de workflow émet.</span><span class="sxs-lookup"><span data-stu-id="c9a18-125">The following table details the tracking records that the workflow runtime emits.</span></span>  
  
|<span data-ttu-id="c9a18-126">Enregistrement de suivi</span><span class="sxs-lookup"><span data-stu-id="c9a18-126">Tracking record</span></span>|<span data-ttu-id="c9a18-127">Description</span><span class="sxs-lookup"><span data-stu-id="c9a18-127">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="c9a18-128">Enregistrements de suivi d'instance du workflow.</span><span class="sxs-lookup"><span data-stu-id="c9a18-128">Workflow instance tracking records.</span></span>|<span data-ttu-id="c9a18-129">Décrit le cycle de vie de l'instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="c9a18-129">Describes the lifecycle of the workflow instance.</span></span> <span data-ttu-id="c9a18-130">Par exemple, un enregistrement d'instance est émis lorsque le workflow démarre ou se termine.</span><span class="sxs-lookup"><span data-stu-id="c9a18-130">For example, an instance record is emitted when the workflow starts or completes.</span></span>|  
|<span data-ttu-id="c9a18-131">Enregistrements de suivi d'état d'activité.</span><span class="sxs-lookup"><span data-stu-id="c9a18-131">Activity state tracking records.</span></span>|<span data-ttu-id="c9a18-132">Détaille l'exécution de l'activité.</span><span class="sxs-lookup"><span data-stu-id="c9a18-132">Details activity execution.</span></span> <span data-ttu-id="c9a18-133">Ces enregistrements indiquent l'état d'une activité de workflow, par exemple lorsqu'une activité est planifiée, lorsque l'activité se termine ou lorsqu'une erreur est générée.</span><span class="sxs-lookup"><span data-stu-id="c9a18-133">These records indicate the state of a workflow activity such as when an activity is scheduled or when the activity completes or when a fault is thrown.</span></span>|  
|<span data-ttu-id="c9a18-134">Enregistrement de reprise de signet.</span><span class="sxs-lookup"><span data-stu-id="c9a18-134">Bookmark resumption record.</span></span>|<span data-ttu-id="c9a18-135">Émis chaque fois qu'un signet au sein d'une instance de workflow est repris.</span><span class="sxs-lookup"><span data-stu-id="c9a18-135">Emitted whenever a bookmark within a workflow instance is resumed.</span></span>|  
|<span data-ttu-id="c9a18-136">Enregistrements de suivi personnalisé.</span><span class="sxs-lookup"><span data-stu-id="c9a18-136">Custom tracking records.</span></span>|<span data-ttu-id="c9a18-137">Un auteur de workflow peut créer des enregistrements de suivi personnalisé et les émettre dans l'activité personnalisée.</span><span class="sxs-lookup"><span data-stu-id="c9a18-137">A workflow author can create custom tracking records and emit them within the custom activity.</span></span>|  
|<xref:System.Activities.Tracking.ActivityScheduledRecord>|<span data-ttu-id="c9a18-138">Cet enregistrement est émis lorsqu'une activité planifie une autre activité.</span><span class="sxs-lookup"><span data-stu-id="c9a18-138">This record is emitted when an activity schedules another activity.</span></span>|  
|<xref:System.Activities.Tracking.FaultPropagationRecord>|<span data-ttu-id="c9a18-139">Cet enregistrement est émis lorsqu'une erreur est propagée à partir d'une activité.</span><span class="sxs-lookup"><span data-stu-id="c9a18-139">This record is emitted when a fault is propagated from an activity.</span></span>|  
|<xref:System.Activities.Tracking.CancelRequestedRecord>|<span data-ttu-id="c9a18-140">Cet enregistrement est émis lorsqu'une activité est annulée par une autre activité.</span><span class="sxs-lookup"><span data-stu-id="c9a18-140">This record is emitted when an activity is canceled by another activity.</span></span>|  
  
 <span data-ttu-id="c9a18-141">Le participant de suivi s'abonne à un sous-ensemble des enregistrements de suivi émis à l'aide de modèles de suivi.</span><span class="sxs-lookup"><span data-stu-id="c9a18-141">The tracking participant subscribes for a subset of the emitted tracking records using tracking profiles.</span></span> <span data-ttu-id="c9a18-142">Un modèle de suivi contient des requêtes de suivi qui permettent de s'abonner à un type d'enregistrement de suivi particulier.</span><span class="sxs-lookup"><span data-stu-id="c9a18-142">A tracking profile contains tracking queries that allow subscribing for a particular tracking record type.</span></span> <span data-ttu-id="c9a18-143">Les modèles de suivi peuvent être spécifiés dans le code ou dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="c9a18-143">Tracking profiles can be specified in code or in configuration.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="c9a18-144">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="c9a18-144">To use this sample</span></span>  
  
1.  <span data-ttu-id="c9a18-145">À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution EtwTrackingParticipantSample.sln.</span><span class="sxs-lookup"><span data-stu-id="c9a18-145">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the EtwTrackingParticipantSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="c9a18-146">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="c9a18-146">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="c9a18-147">Pour exécuter la solution, appuyez sur F5.</span><span class="sxs-lookup"><span data-stu-id="c9a18-147">To run the solution, press F5.</span></span>  
  
     <span data-ttu-id="c9a18-148">Par défaut, le service écoute sur le port 53797 (http://localhost:53797/SampleWorkflowService.xamlx).</span><span class="sxs-lookup"><span data-stu-id="c9a18-148">By default, the service is listening on port 53797 (http://localhost:53797/SampleWorkflowService.xamlx).</span></span>  
  
4.  <span data-ttu-id="c9a18-149">À l'aide de l'[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], ouvrez le client de test WCF.</span><span class="sxs-lookup"><span data-stu-id="c9a18-149">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], open the WCF test client.</span></span>  
  
     <span data-ttu-id="c9a18-150">Le client de test WCF (WcfTestClient.exe) se trouve dans le \< [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] dossier d’installation > \Common7\IDE\ dossier.</span><span class="sxs-lookup"><span data-stu-id="c9a18-150">The WCF test client (WcfTestClient.exe) is located in the \<[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] installation folder>\Common7\IDE\ folder.</span></span>  
  
     <span data-ttu-id="c9a18-151">Le dossier d'installation [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] par défaut est C:\Program Files\Microsoft Visual Studio 10.0.</span><span class="sxs-lookup"><span data-stu-id="c9a18-151">The default [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] installation folder is C:\Program Files\Microsoft Visual Studio 10.0.</span></span>  
  
5.  <span data-ttu-id="c9a18-152">Dans le client test WCF, sélectionnez **ajouter un Service** à partir de la **fichier** menu.</span><span class="sxs-lookup"><span data-stu-id="c9a18-152">In WCF test client, select **Add Service** from the **File** menu.</span></span>  
  
     <span data-ttu-id="c9a18-153">Ajoutez l'adresse du point de terminaison dans la zone d'entrée.</span><span class="sxs-lookup"><span data-stu-id="c9a18-153">Add the endpoint address in the input box.</span></span> <span data-ttu-id="c9a18-154">La valeur par défaut est http://localhost:53797/SampleWorkflowService.xamlx.</span><span class="sxs-lookup"><span data-stu-id="c9a18-154">The default is http://localhost:53797/SampleWorkflowService.xamlx.</span></span>  
  
6.  <span data-ttu-id="c9a18-155">Ouvrez l'application Observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="c9a18-155">Open the Event Viewer application.</span></span>  
  
     <span data-ttu-id="c9a18-156">Avant d’appeler le service, démarrez l’Observateur d’événements à partir de la **Démarrer** menu, sélectionnez **exécuter** et tapez `eventvwr.exe`.</span><span class="sxs-lookup"><span data-stu-id="c9a18-156">Before invoking the service, start Event Viewer from the **Start** menu, select **Run** and type in `eventvwr.exe`.</span></span> <span data-ttu-id="c9a18-157">Vérifiez que le journal des événements écoute les événements de suivi émis à partir du service de workflow.</span><span class="sxs-lookup"><span data-stu-id="c9a18-157">Ensure that the event log is listening for tracking events emitted from the workflow service.</span></span>  
  
7.  <span data-ttu-id="c9a18-158">Dans l’arborescence de l’Observateur d’événements, accédez à **Observateur d’événements**, **journaux des Applications et Services**, et **Microsoft**.</span><span class="sxs-lookup"><span data-stu-id="c9a18-158">In the tree view of the Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, and **Microsoft**.</span></span> <span data-ttu-id="c9a18-159">Avec le bouton droit **Microsoft** et sélectionnez **vue** , puis **afficher les journaux d’analyse et de débogage** pour activer l’analyse et les journaux de débogage</span><span class="sxs-lookup"><span data-stu-id="c9a18-159">Right-click **Microsoft** and select **View** and then **Show Analytic and Debug Logs** to enable the analytic and debug logs</span></span>  
  
     <span data-ttu-id="c9a18-160">Vérifiez que le **afficher les journaux d’analyse et de débogage** option est activée.</span><span class="sxs-lookup"><span data-stu-id="c9a18-160">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>  
  
8.  <span data-ttu-id="c9a18-161">Dans l’arborescence de commandes dans l’Observateur d’événements, accédez à **Observateur d’événements**, **journaux des Applications et Services**, **Microsoft**, **Windows**,  **Serveur d’applications-Applications**.</span><span class="sxs-lookup"><span data-stu-id="c9a18-161">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="c9a18-162">Avec le bouton droit **analyse** et sélectionnez **activer le journal** pour activer la **analyse** journal.</span><span class="sxs-lookup"><span data-stu-id="c9a18-162">Right-click **Analytic** and select **Enable Log** to enable the **Analytic** log.</span></span>  
  
9. <span data-ttu-id="c9a18-163">Testez le service à l'aide du client test WCF en double-cliquant sur `GetData`.</span><span class="sxs-lookup"><span data-stu-id="c9a18-163">Test the service using the WCF test client by double-clicking `GetData`.</span></span>  
  
     <span data-ttu-id="c9a18-164">Vous ouvrez ainsi la méthode `GetData`.</span><span class="sxs-lookup"><span data-stu-id="c9a18-164">This opens the `GetData` method.</span></span> <span data-ttu-id="c9a18-165">La demande accepte un paramètre et vérifie que la valeur est égale à 0, qui est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="c9a18-165">The request accepts one parameter and ensures that the value is 0, which is the default.</span></span>  
  
     <span data-ttu-id="c9a18-166">Cliquez sur **appeler**.</span><span class="sxs-lookup"><span data-stu-id="c9a18-166">Click **Invoke**.</span></span>  
  
10. <span data-ttu-id="c9a18-167">Observez les événements émis à partir du workflow.</span><span class="sxs-lookup"><span data-stu-id="c9a18-167">Observe the events emitted from the workflow.</span></span>  
  
     <span data-ttu-id="c9a18-168">Revenez à l’Observateur d’événements et naviguez jusqu'à **Observateur d’événements**, **journaux des Applications et Services**, **Microsoft**, **Windows**,  **Serveur d’applications-Applications**.</span><span class="sxs-lookup"><span data-stu-id="c9a18-168">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="c9a18-169">Avec le bouton droit **analyse** et sélectionnez **Actualiser**.</span><span class="sxs-lookup"><span data-stu-id="c9a18-169">Right-click **Analytic** and select **Refresh**.</span></span>  
  
     <span data-ttu-id="c9a18-170">Les événements de workflow sont affichés dans l'observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="c9a18-170">The workflow events are displayed in the event viewer.</span></span> <span data-ttu-id="c9a18-171">Notez que les événements d'exécution du workflow sont affichés et que l'un d'eux est une exception non gérée qui correspond à l'erreur dans le workflow.</span><span class="sxs-lookup"><span data-stu-id="c9a18-171">Notice that workflow execution events are displayed and that one of them is an unhandled exception that corresponds to the error in workflow.</span></span> <span data-ttu-id="c9a18-172">Par ailleurs, un événement d'avertissement est émis à partir de l'activité de workflow, qui indique que l'activité génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="c9a18-172">Also, a warning event is emitted from the workflow activity, which indicates that the activity is throwing a fault.</span></span>  
  
11. <span data-ttu-id="c9a18-173">Répétez les étapes 9 et 10 avec une entrée de données autre que 0, afin qu'aucune erreur ne soit générée.</span><span class="sxs-lookup"><span data-stu-id="c9a18-173">Repeat steps 9 and 10 with an input of data other than 0, so that no error is thrown.</span></span>  
  
 <span data-ttu-id="c9a18-174">Les modèles de suivi vous permettent de vous abonner à des événements émis par l'exécution lorsque l'état d'une instance de workflow est modifié.</span><span class="sxs-lookup"><span data-stu-id="c9a18-174">Tracking profiles allow you to subscribe to events that are emitted by the runtime when the state of a workflow instance changes.</span></span> <span data-ttu-id="c9a18-175">Selon vos spécifications d'analyse, vous pouvez créer un profil très général, qui s'abonne à un petit jeu de modifications d'état de haut niveau d'un workflow.</span><span class="sxs-lookup"><span data-stu-id="c9a18-175">Depending on your monitoring requirements, you can create a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="c9a18-176">En revanche, vous pouvez créer un profil très précis dont la sortie est assez riche pour reconstruire l'exécution ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="c9a18-176">On the other hand, you can create a very precise profile whose output is rich enough to reconstruct the execution later.</span></span> <span data-ttu-id="c9a18-177">L'exemple illustre les événements émis à partir de l'exécution du workflow dans ETW à l'aide du `HealthMonitoring Tracking Profile`, qui émet un petit jeu d'événements.</span><span class="sxs-lookup"><span data-stu-id="c9a18-177">The sample demonstrates the events emitted from the workflow runtime to ETW using the `HealthMonitoring Tracking Profile`, which emits a small set of events.</span></span> <span data-ttu-id="c9a18-178">Un profil différent qui émet d'autres événements de suivi de workflow est également fourni dans le fichier Web.config nommé `Troubleshooting Tracking Profile`.</span><span class="sxs-lookup"><span data-stu-id="c9a18-178">A different profile that emits more workflow tracking events is also provided in the Web.config that is named `Troubleshooting Tracking Profile`.</span></span> <span data-ttu-id="c9a18-179">Lorsque le [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] est installé, un profil par défaut avec un nom vide est configuré dans le fichier Machine.config.</span><span class="sxs-lookup"><span data-stu-id="c9a18-179">When the [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] is installed, a default profile with an empty name is configured in the Machine.config file.</span></span> <span data-ttu-id="c9a18-180">Ce profil est utilisé par la configuration de comportement de suivi ETW lorsque aucun nom de profil n'est spécifié ou lorsqu'un nom de profil vide est spécifié.</span><span class="sxs-lookup"><span data-stu-id="c9a18-180">This profile is used by the ETW tracking behavior configuration when no profile name or an empty profile name is specified.</span></span>  
  
 <span data-ttu-id="c9a18-181">Le modèle de suivi de contrôle d'état émet des enregistrements d'instance de workflow et des enregistrements de propagation d'erreur de l'activité.</span><span class="sxs-lookup"><span data-stu-id="c9a18-181">The health monitoring tracking profile emits workflow instance records and activity fault propagation records.</span></span> <span data-ttu-id="c9a18-182">Ce profil est créé en ajoutant le modèle de suivi suivant à un fichier de configuration Web.config.</span><span class="sxs-lookup"><span data-stu-id="c9a18-182">This profile is created by adding the following tracking profile to a Web.config configuration file.</span></span>  
  
```xml  
<<tracking>  
      <profiles>  
        <trackingProfile name="HealthMonitoring Tracking Profile">  
          <workflow activityDefinitionId="*">  
            <workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="Started"/>  
                  <state name="Completed"/>  
                  <state name="Aborted"/>  
                  <state name="UnhandledException"/>  
                </states>  
            </workflowInstanceQuery>  
           </workflowInstanceQueries>  
            <faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
            </faultPropagationQueries>  
          </workflow>  
        </trackingProfile>  
       </profiles>  
</tracking>  
```  
  
 <span data-ttu-id="c9a18-183">Le profil peut être modifié en changeant la configuration `EtwTrackingParticipant` comme suit.</span><span class="sxs-lookup"><span data-stu-id="c9a18-183">The profile can be changed by changing the `EtwTrackingParticipant` configuration to the following.</span></span>  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <etwTracking profileName="HealthMonitoring Tracking Profile"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
#### <a name="to-clean-up-optional"></a><span data-ttu-id="c9a18-184">Pour nettoyer (facultatif)</span><span class="sxs-lookup"><span data-stu-id="c9a18-184">To clean up (Optional)</span></span>  
  
1.  <span data-ttu-id="c9a18-185">Ouvrez l'observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="c9a18-185">Open Event Viewer.</span></span>  
  
2.  <span data-ttu-id="c9a18-186">Accédez à **Observateur d’événements**, **journaux des Applications et Services**, **Microsoft**, **Windows**, **Application Les Applications serveur**.</span><span class="sxs-lookup"><span data-stu-id="c9a18-186">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="c9a18-187">Avec le bouton droit **analyse** et sélectionnez **désactiver le journal**.</span><span class="sxs-lookup"><span data-stu-id="c9a18-187">Right-click **Analytic** and select **Disable Log**.</span></span>  
  
3.  <span data-ttu-id="c9a18-188">Accédez à **Observateur d’événements**, **journaux des Applications et Services**, **Microsoft**, **Windows**, **Application Les Applications serveur**.</span><span class="sxs-lookup"><span data-stu-id="c9a18-188">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="c9a18-189">Avec le bouton droit **analyse** et sélectionnez **effacer le journal**.</span><span class="sxs-lookup"><span data-stu-id="c9a18-189">Right-click **Analytic** and select **Clear Log**.</span></span>  
  
4.  <span data-ttu-id="c9a18-190">Choisissez le **effacer** option pour effacer les événements.</span><span class="sxs-lookup"><span data-stu-id="c9a18-190">Choose the **Clear** option to clear the events.</span></span>  
  
## <a name="known-issue"></a><span data-ttu-id="c9a18-191">Problème connu</span><span class="sxs-lookup"><span data-stu-id="c9a18-191">Known Issue</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c9a18-192">Un problème connu de l'observateur d'événements est qu'il lui arrive de ne pas parvenir à décoder des événements ETW.</span><span class="sxs-lookup"><span data-stu-id="c9a18-192">There is a known issue in the Event Viewer where it may fail to decode ETW events.</span></span> <span data-ttu-id="c9a18-193">Un message d'erreur semblable au suivant s'affiche éventuellement.</span><span class="sxs-lookup"><span data-stu-id="c9a18-193">You may see an error message that looks like the following.</span></span>  
>   
>  <span data-ttu-id="c9a18-194">La description de l’ID d’événement \<id > à partir de la source Microsoft-Windows-Application Server-Applications est introuvable.</span><span class="sxs-lookup"><span data-stu-id="c9a18-194">The description for Event ID \<id> from source Microsoft-Windows-Application Server-Applications cannot be found.</span></span> <span data-ttu-id="c9a18-195">Le composant qui a déclenché cet événement n'est pas installé sur l'ordinateur local ou l'installation est endommagée.</span><span class="sxs-lookup"><span data-stu-id="c9a18-195">Either the component that raises this event is not installed on your local computer or the installation is corrupted.</span></span> <span data-ttu-id="c9a18-196">Vous pouvez installer ou réparer le composant sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="c9a18-196">You can install or repair the component on the local computer.</span></span>  
>   
>  <span data-ttu-id="c9a18-197">Si vous rencontrez cette erreur, cliquez sur Actualiser dans le volet Actions.</span><span class="sxs-lookup"><span data-stu-id="c9a18-197">If you encounter this error, click refresh in the actions pane.</span></span> <span data-ttu-id="c9a18-198">Le décodage de l'événement doit maintenant s'effectuer correctement.</span><span class="sxs-lookup"><span data-stu-id="c9a18-198">The event should now decode properly.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c9a18-199">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c9a18-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c9a18-200">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="c9a18-200">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c9a18-201">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c9a18-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c9a18-202">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="c9a18-202">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\EtwTracking`  
  
## <a name="see-also"></a><span data-ttu-id="c9a18-203">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c9a18-203">See Also</span></span>  
 [<span data-ttu-id="c9a18-204">Exemples d’analyse AppFabric</span><span class="sxs-lookup"><span data-stu-id="c9a18-204">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
