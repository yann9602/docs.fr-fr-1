---
title: "Extraire des données WF à l'aide du suivi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e30c68f5-8c6a-495a-bd20-667a4364c68e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d6c269dc9c8b5a0050cfc3ffcefc3160b07c897
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="extract-wf-data-using-tracking"></a><span data-ttu-id="e3525-102">Extraire des données WF à l'aide du suivi</span><span class="sxs-lookup"><span data-stu-id="e3525-102">Extract WF Data using Tracking</span></span>
<span data-ttu-id="e3525-103">Cet exemple montre comment utiliser le suivi de workflow pour extraire des variables de workflow et des arguments d’activités.</span><span class="sxs-lookup"><span data-stu-id="e3525-103">This sample demonstrates how to use workflow tracking to extract workflow variables and arguments from activities.</span></span> <span data-ttu-id="e3525-104">Il montre également l'ajout d'annotations à des enregistrements de suivi et l'extraction de la charge utile de données dans des enregistrements de suivi personnalisés.</span><span class="sxs-lookup"><span data-stu-id="e3525-104">It also shows the addition of annotations to tracking records and the extraction of data payload within custom tracking records.</span></span> <span data-ttu-id="e3525-105">L'exemple utilise le participant de suivi Suivi d'événements pour Windows (ETW, Event Tracing for Windows) pour extraire des données du workflow.</span><span class="sxs-lookup"><span data-stu-id="e3525-105">The sample uses the Event Tracing for Windows (ETW) tracking participant to extract data from the workflow.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="e3525-106">Détails de l'exemple</span><span class="sxs-lookup"><span data-stu-id="e3525-106">Sample Details</span></span>  
 [!INCLUDE[wf](../../../../includes/wf-md.md)]<span data-ttu-id="e3525-107"> fournit le suivi pour avoir plus de visibilité dans l'exécution d'une instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="e3525-107"> provides tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="e3525-108">Le runtime de suivi émet des enregistrements de suivi de workflow lors de l'exécution du workflow.</span><span class="sxs-lookup"><span data-stu-id="e3525-108">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> <span data-ttu-id="e3525-109">Avec les enregistrements de suivi de workflow, les données dans l'instance de workflow peuvent être extraites du workflow.</span><span class="sxs-lookup"><span data-stu-id="e3525-109">Along with the workflow tracking records, data within the workflow instance can be extracted from the workflow.</span></span> <span data-ttu-id="e3525-110">La liste suivante détaille les types des données qui peuvent être extraites des enregistrements de suivi :</span><span class="sxs-lookup"><span data-stu-id="e3525-110">The following list details the types of data that can be extracted from tracking records:</span></span>  
  
1.  <span data-ttu-id="e3525-111">Variables de workflow dans une activité et enregistrements de suivi pendant l'exécution de l'activité.</span><span class="sxs-lookup"><span data-stu-id="e3525-111">Workflow variables within an activity and tracking records during activity execution.</span></span>  
  
     <span data-ttu-id="e3525-112">Pour extraire des variables de workflow, les variables à extraire sont spécifiées dans un profil.</span><span class="sxs-lookup"><span data-stu-id="e3525-112">To extract workflow variables, the variables to be extracted are specified in a profile.</span></span> <span data-ttu-id="e3525-113">Les variables à extraire peuvent uniquement être spécifiées avec `ActivityStateQueries`.</span><span class="sxs-lookup"><span data-stu-id="e3525-113">Variables to be extracted can only be specified with `ActivityStateQueries`.</span></span> <span data-ttu-id="e3525-114">L'exemple de code suivant illustre un modèle de suivi utilisé pour extraire la variable de workflow d'une activité.</span><span class="sxs-lookup"><span data-stu-id="e3525-114">The following code example demonstrates a tracking profile used to extract the workflow variable from an activity.</span></span>  
  
    ```xml  
    <activityStateQuery activityName="StockPriceService">  
         <states>  
              <state name="Closed"/>  
         </states>  
         <variables>  
              <variable name="symbol"/>  
         </variables>  
    </activityStateQuery>  
    ```  
  
2.  <span data-ttu-id="e3525-115">Arguments d'activité et enregistrements de suivi d'état d'activité.</span><span class="sxs-lookup"><span data-stu-id="e3525-115">Activity arguments and activity state tracking records.</span></span>  
  
     <span data-ttu-id="e3525-116">Les arguments définissent le flux de données à l'intérieur ou à l'extérieur d'une activité.</span><span class="sxs-lookup"><span data-stu-id="e3525-116">Arguments define the way data flows in or out of an activity.</span></span> <span data-ttu-id="e3525-117">Les arguments à extraire sont spécifiés à l'aide d'un <xref:System.Activities.Tracking.ActivityStateQuery>. L'exemple de code suivant est un modèle de suivi qui extrait l'argument `Value`.</span><span class="sxs-lookup"><span data-stu-id="e3525-117">Arguments to be extracted are specified using an <xref:System.Activities.Tracking.ActivityStateQuery>.The following code example is a tracking profile that extracts the `Value` argument.</span></span>  
  
    ```xml  
    <activityStateQuery activityName="GetStockPrice">  
         <states>  
              <state name="Closed"/>  
         </states>  
         <arguments>  
              <argument name="Value"/>  
         </arguments>  
    </activityStateQuery>  
    ```  
  
3.  <span data-ttu-id="e3525-118">Les annotations sont des paires clé/valeur qui peuvent être ajoutées à tout enregistrement de suivi émis.</span><span class="sxs-lookup"><span data-stu-id="e3525-118">Annotations are key/value pairs that can be added to any tracking record that is emitted.</span></span>  
  
     <span data-ttu-id="e3525-119">Les annotations servent de mécanisme de balises pour les enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="e3525-119">Annotations serve as a tagging mechanism for tracking records.</span></span> <span data-ttu-id="e3525-120">Les annotations sont ajoutées aux enregistrements de suivi via un modèle de suivi.</span><span class="sxs-lookup"><span data-stu-id="e3525-120">Annotations are added to tracking records through a tracking profile.</span></span> <span data-ttu-id="e3525-121">Les annotations peuvent être ajoutées à tout type de requête de suivi de workflow.</span><span class="sxs-lookup"><span data-stu-id="e3525-121">Annotations can be added to any type of a workflow tracking query.</span></span> <span data-ttu-id="e3525-122">L'exemple de code suivant est un modèle de suivi qui montre comment une annotation peut être ajoutée à un enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="e3525-122">The following code example is a tracking profile that shows how an annotation can be added to a tracking record.</span></span>  
  
    ```xml  
    <workflowInstanceQuery>  
         <states>  
              <state name="Started"/>  
         </states>  
         <annotations>  
              <annotation name="StockPriceWorkflow" value="Begin"/>  
         </annotations>  
    </workflowInstanceQuery>  
    ```  
  
4.  <span data-ttu-id="e3525-123">Les enregistrements de suivi personnalisés sont émis à partir d'activités définies par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e3525-123">Custom tracking records are emitted from user-defined activities.</span></span>  
  
     <span data-ttu-id="e3525-124">Les enregistrements de suivi personnalisés peuvent contenir des données de charge utile définies dans cette activité.</span><span class="sxs-lookup"><span data-stu-id="e3525-124">Custom tracking records can carry payload data defined within this activity.</span></span> <span data-ttu-id="e3525-125">L'abonnement aux enregistrements de suivi personnalisés dans un modèle de suivi permet l'extraction de la charge utile dans l'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="e3525-125">Subscribing for custom tracking records in a tracking profile allows the extraction of the payload within the tracking record.</span></span> <span data-ttu-id="e3525-126">Les enregistrements de suivi personnalisés peuvent être extraits avec un <xref:System.Activities.Tracking.TrackingQuery> personnalisé.</span><span class="sxs-lookup"><span data-stu-id="e3525-126">The custom tracking records can be extracted with custom a <xref:System.Activities.Tracking.TrackingQuery>.</span></span> <span data-ttu-id="e3525-127">L'exemple de code suivant est un modèle de suivi qui extrait un enregistrement de suivi personnalisé avec sa charge utile.</span><span class="sxs-lookup"><span data-stu-id="e3525-127">The following code example is a tracking profile that extracts a custom tracking record along with its payload.</span></span>  
  
    ```xml  
    <customTrackingQuery name="QuoteLookupEvent" activityName="GetStockPrice"/>  
    ```  
  
 <span data-ttu-id="e3525-128">L'exemple illustre l'extraction de variables, d'arguments et d'enregistrements personnalisés ainsi que l'ajout d'annotations à l'aide d'un profil spécifié dans un fichier Web.config. Le suivi est activé sur l'exemple de service de workflow en ajoutant un élément de comportement `<etwTracking>`.</span><span class="sxs-lookup"><span data-stu-id="e3525-128">The sample demonstrates the extraction of a variables, arguments, custom records and adding annotations using a profile specified in a Web.config. Tracking is enabled on the sample workflow service by adding an `<etwTracking>` behavior element.</span></span> <span data-ttu-id="e3525-129">L'exemple de code suivant active le suivi pour le modèle de suivi `ExtractWorkflowVariables`.</span><span class="sxs-lookup"><span data-stu-id="e3525-129">The following code example enables tracking for the `ExtractWorkflowVariables` tracking profile.</span></span>  
  
```xml  
<serviceBehaviors>  
     <behavior>  
               <etwTracking profileName="ExtractWorkflowVariables"/>  
     </behavior>  
</serviceBehaviors>  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="e3525-130">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="e3525-130">To use this sample</span></span>  
  
1.  <span data-ttu-id="e3525-131">À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution WFStockPriceApplication.sln.</span><span class="sxs-lookup"><span data-stu-id="e3525-131">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the WFStockPriceApplication.sln solution file.</span></span>  
  
2.  <span data-ttu-id="e3525-132">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="e3525-132">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="e3525-133">Pour exécuter la solution, appuyez sur F5.</span><span class="sxs-lookup"><span data-stu-id="e3525-133">To run the solution, press F5.</span></span>  
  
     <span data-ttu-id="e3525-134">La fenêtre du navigateur s'ouvre et affiche la liste des répertoires pour l'application.</span><span class="sxs-lookup"><span data-stu-id="e3525-134">The browser window opens and shows the directory listing for the application.</span></span>  
  
4.  <span data-ttu-id="e3525-135">Dans le navigateur, cliquez sur StockPriceService.xamlx.</span><span class="sxs-lookup"><span data-stu-id="e3525-135">In the browser, click StockPriceService.xamlx.</span></span>  
  
5.  <span data-ttu-id="e3525-136">Le navigateur affiche la page StockPriceService, laquelle contient l'adresse WSDL du service local.</span><span class="sxs-lookup"><span data-stu-id="e3525-136">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="e3525-137">Copiez cette adresse.</span><span class="sxs-lookup"><span data-stu-id="e3525-137">Copy this address.</span></span>  
  
     <span data-ttu-id="e3525-138">L'exemple suivant affiche une adresse WSDL du service local.</span><span class="sxs-lookup"><span data-stu-id="e3525-138">The following example shows a local service WSDL address.</span></span> `http://localhost:53797/StockPriceService.xamlx?wsdl`  
  
6.  <span data-ttu-id="e3525-139">Avant d'appeler le service, démarrez l'observateur d'événements et vérifiez que le journal des événements écoute les événements de suivi émis à partir du service de workflow.</span><span class="sxs-lookup"><span data-stu-id="e3525-139">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the workflow service.</span></span>  
  
7.  <span data-ttu-id="e3525-140">À partir de la **Démarrer** menu, sélectionnez **outils d’administration** , puis **Observateur d’événements**.</span><span class="sxs-lookup"><span data-stu-id="e3525-140">From the **Start** menu, select **Administrative Tools** and then **Event Viewer**.</span></span>  
  
8.  <span data-ttu-id="e3525-141">Dans l’arborescence de commandes dans l’Observateur d’événements, accédez à **Observateur d’événements**, **journaux des Applications et Services**, et **Microsoft**.</span><span class="sxs-lookup"><span data-stu-id="e3525-141">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, and **Microsoft**.</span></span> <span data-ttu-id="e3525-142">Avec le bouton droit **Microsoft** et sélectionnez **vue** , puis **afficher les journaux d’analyse et de débogage**.</span><span class="sxs-lookup"><span data-stu-id="e3525-142">Right-click **Microsoft** and select **View** and then **Show Analytic and Debug Logs**.</span></span>  
  
     <span data-ttu-id="e3525-143">Vérifiez que le **afficher les journaux d’analyse et de débogage** option est activée.</span><span class="sxs-lookup"><span data-stu-id="e3525-143">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>  
  
9. <span data-ttu-id="e3525-144">Dans l’arborescence de commandes dans l’Observateur d’événements, accédez à **Observateur d’événements**, **journaux des Applications et Services**, **Microsoft**, **Windows**,  **Serveur d’applications-Applications**.</span><span class="sxs-lookup"><span data-stu-id="e3525-144">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="e3525-145">Avec le bouton droit **analyse** et sélectionnez **activer le journal**.</span><span class="sxs-lookup"><span data-stu-id="e3525-145">Right-click **Analytic** and select **Enable Log**.</span></span>  
  
10. <span data-ttu-id="e3525-146">À l'aide de l'[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], ouvrez le client de test WCF.</span><span class="sxs-lookup"><span data-stu-id="e3525-146">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], open the WCF test client.</span></span>  
  
     <span data-ttu-id="e3525-147">Le client de test WCF (WcfTestClient.exe) se trouve dans le \< [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] dossier d’installation > \Common7\IDE\ dossier.</span><span class="sxs-lookup"><span data-stu-id="e3525-147">The WCF test client (WcfTestClient.exe) is located in the \<[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] installation folder>\Common7\IDE\ folder.</span></span>  
  
     <span data-ttu-id="e3525-148">Le dossier d'installation [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] par défaut est C:\Program Files\Microsoft Visual Studio 10.0.</span><span class="sxs-lookup"><span data-stu-id="e3525-148">The default [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] installation folder is C:\Program Files\Microsoft Visual Studio 10.0.</span></span>  
  
11. <span data-ttu-id="e3525-149">Dans le client test WCF, sélectionnez **ajouter un Service** à partir de la **fichier** menu.</span><span class="sxs-lookup"><span data-stu-id="e3525-149">In WCF test client, select **Add Service** from the **File** menu.</span></span>  
  
     <span data-ttu-id="e3525-150">Ajoutez l'adresse WSDL du service local que vous avez copiée précédemment dans la zone d'entrée.</span><span class="sxs-lookup"><span data-stu-id="e3525-150">Add the local service WSDL address you copied earlier in the input box.</span></span>  
  
12. <span data-ttu-id="e3525-151">Dans le client test WCF, double-cliquez sur `GetStockPrice`.</span><span class="sxs-lookup"><span data-stu-id="e3525-151">In WCF test client, double-click `GetStockPrice`.</span></span>  
  
     <span data-ttu-id="e3525-152">Vous ouvrez ainsi la méthode `GetStockPrice`.</span><span class="sxs-lookup"><span data-stu-id="e3525-152">This opens the `GetStockPrice` method.</span></span> <span data-ttu-id="e3525-153">La demande accepte un paramètre.</span><span class="sxs-lookup"><span data-stu-id="e3525-153">The request accepts one parameter.</span></span> <span data-ttu-id="e3525-154">Utilisez la valeur **Contoso**.</span><span class="sxs-lookup"><span data-stu-id="e3525-154">Use the value **Contoso**.</span></span>  
  
13. <span data-ttu-id="e3525-155">Cliquez sur **appeler**.</span><span class="sxs-lookup"><span data-stu-id="e3525-155">Click **Invoke**.</span></span>  
  
14. <span data-ttu-id="e3525-156">Revenez à l’Observateur d’événements et naviguez jusqu'à **Observateur d’événements**, **journaux des Applications et Services**, **Microsoft**, **Windows**,  **Serveur d’applications-Applications**.</span><span class="sxs-lookup"><span data-stu-id="e3525-156">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="e3525-157">Avec le bouton droit **analyse** et sélectionnez **Actualiser**.</span><span class="sxs-lookup"><span data-stu-id="e3525-157">Right-click **Analytic** and select **Refresh**.</span></span> <span data-ttu-id="e3525-158">Les événements de workflow sont dans la plage d'ID d’événements comprise entre 100 et 199.</span><span class="sxs-lookup"><span data-stu-id="e3525-158">The workflow events are in the event ID ranges 100-199.</span></span>  
  
     <span data-ttu-id="e3525-159">Les événements contiennent les annotations, variables, arguments et enregistrements de suivi personnalisés qui peuvent être affichés dans l'observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="e3525-159">The events contain the annotations, variables, arguments and custom tracking records that can be viewed in the event viewer.</span></span>  
  
## <a name="cleaning-up-in-the-event-viewer"></a><span data-ttu-id="e3525-160">Nettoyage dans l'observateur d'événements</span><span class="sxs-lookup"><span data-stu-id="e3525-160">Cleaning up in the Event Viewer</span></span>  
 <span data-ttu-id="e3525-161">Le canal analytique dans le journal des événements peut être nettoyé dans l'observateur d'événements en procédant comme suit.</span><span class="sxs-lookup"><span data-stu-id="e3525-161">The analytic channel in the event log can be cleaned up in the Event Viewer by doing the following.</span></span>  
  
#### <a name="to-clean-up-optional"></a><span data-ttu-id="e3525-162">Pour nettoyer (facultatif)</span><span class="sxs-lookup"><span data-stu-id="e3525-162">To clean up (Optional)</span></span>  
  
1.  <span data-ttu-id="e3525-163">Ouvrez l'observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="e3525-163">Open Event Viewer.</span></span>  
  
2.  <span data-ttu-id="e3525-164">Accédez à **Observateur d’événements**, **journaux des Applications et Services**, **Microsoft**, **Windows**, **Application Les Applications serveur**.</span><span class="sxs-lookup"><span data-stu-id="e3525-164">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="e3525-165">Avec le bouton droit **analyse** et sélectionnez **désactiver le journal**.</span><span class="sxs-lookup"><span data-stu-id="e3525-165">Right-click **Analytic** and select **Disable Log**.</span></span>  
  
3.  <span data-ttu-id="e3525-166">Accédez à **Observateur d’événements**, **journaux des Applications et Services**, **Microsoft**, **Windows**, **Application Les Applications serveur**.</span><span class="sxs-lookup"><span data-stu-id="e3525-166">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="e3525-167">Avec le bouton droit **analyse** et sélectionnez **effacer le journal**.</span><span class="sxs-lookup"><span data-stu-id="e3525-167">Right-click **Analytic** and select **Clear Log**.</span></span>  
  
     <span data-ttu-id="e3525-168">Choisissez le **effacer** option pour effacer les événements.</span><span class="sxs-lookup"><span data-stu-id="e3525-168">Choose the **Clear** option to clear the events.</span></span>  
  
## <a name="known-issue"></a><span data-ttu-id="e3525-169">Problème connu</span><span class="sxs-lookup"><span data-stu-id="e3525-169">Known Issue</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3525-170">Un problème connu de l'observateur d'événements est qu'il lui arrive de ne pas parvenir à décoder des événements ETW.</span><span class="sxs-lookup"><span data-stu-id="e3525-170">There is a known issue in the Event Viewer where it may fail to decode ETW events.</span></span> <span data-ttu-id="e3525-171">Un message d'erreur semblable au suivant s'affiche éventuellement.</span><span class="sxs-lookup"><span data-stu-id="e3525-171">You may see an error message that looks like the following.</span></span>  
>   
>  `The description for Event ID <id> from source Microsoft-Windows-Application Server-Applications cannot be found. Either the component that raises this event is not installed on your local computer or the installation is corrupted. You can install or repair the component on the local computer.`  
>   
>  <span data-ttu-id="e3525-172">Si vous rencontrez cette erreur, cliquez sur **Actualiser** dans le volet actions.</span><span class="sxs-lookup"><span data-stu-id="e3525-172">If you encounter this error, click **Refresh** in the actions pane.</span></span> <span data-ttu-id="e3525-173">Le décodage de l'événement doit maintenant s'effectuer correctement.</span><span class="sxs-lookup"><span data-stu-id="e3525-173">The event should now decode properly.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e3525-174">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e3525-174">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e3525-175">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="e3525-175">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e3525-176">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e3525-176">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e3525-177">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="e3525-177">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\ExtractWfData`  
  
## <a name="see-also"></a><span data-ttu-id="e3525-178">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3525-178">See Also</span></span>  
 [<span data-ttu-id="e3525-179">Exemples d’analyse AppFabric</span><span class="sxs-lookup"><span data-stu-id="e3525-179">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
