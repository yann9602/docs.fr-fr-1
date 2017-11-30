---
title: SQLStoreExtensibility
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5da1b5a3-f144-41ba-b9c4-02818b28b15d
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 111e7aa4164d9fc811ebe3f5efb196df77d1ded0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sqlstoreextensibility"></a><span data-ttu-id="2c7f7-102">SQLStoreExtensibility</span><span class="sxs-lookup"><span data-stu-id="2c7f7-102">SQLStoreExtensibility</span></span>
<span data-ttu-id="2c7f7-103">Cet exemple illustre l'utilisation et la configuration de propriétés promues dans le magasin d'instances de workflow SQL.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-103">This sample demonstrates the use and configuration of promoted properties in the SQL workflow instance store.</span></span> <span data-ttu-id="2c7f7-104">Le magasin d'instances de workflow SQL est une implémentation basée sur SQL d'un magasin d'instances.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-104">The SQL workflow instance store is a SQL-based implementation of an instance store.</span></span> <span data-ttu-id="2c7f7-105">Il permet à une instance d'enregistrer et de charger son état vers et à partir d'une base de données SQL Server ou SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-105">It allows an instance to save its state and load its state to and from a SQL Server or SQL Server Express database.</span></span> <span data-ttu-id="2c7f7-106">La fonctionnalité d'extensibilité de magasin permet à l'utilisateur de définir des propriétés qui sont stockées dans le magasin d'instances.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-106">The store extensibility feature allows the user to define properties that are stored in the instance store.</span></span> <span data-ttu-id="2c7f7-107">Ces propriétés sont affichées dans une vue de propriétés promues qui permet à l'utilisateur de les rechercher.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-107">These properties are displayed in a promoted properties view that allows the user to query for them.</span></span>  
  
 <span data-ttu-id="2c7f7-108">Cet exemple est composé d'un workflow qui implémente un service de comptage.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-108">This sample consists of a workflow that implements a counting service.</span></span> <span data-ttu-id="2c7f7-109">Une fois que la méthode de démarrage du service est appelée, le service compte de 0 à 29.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-109">Once the service's start method is invoked, the service counts from 0 to 29.</span></span> <span data-ttu-id="2c7f7-110">Le compteur est incrémenté une fois toutes les 2 secondes.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-110">The counter is incremented once every 2 seconds.</span></span> <span data-ttu-id="2c7f7-111">Après chaque compte, le workflow rend son état persistant.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-111">After each count, the workflow persists.</span></span> <span data-ttu-id="2c7f7-112">La valeur actuelle du compteur est stockée dans le magasin d'instances sous la forme d'une propriété promue.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-112">The current counter value is stored in the instance store as a promoted property.</span></span>  
  
 <span data-ttu-id="2c7f7-113">Le workflow de comptage est auto-hébergé par un hôte de service de workflow.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-113">The Counting Workflow is self-hosted by a Workflow Service Host.</span></span> <span data-ttu-id="2c7f7-114">La méthode `Main` du programme effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="2c7f7-114">The program's `Main` method performs the following actions:</span></span>  
  
-   <span data-ttu-id="2c7f7-115">Crée une instance de l'hôte du service du workflow qui héberge le workflow de comptage et définit les points de terminaison sous lesquels le workflow de comptage peut être atteint.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-115">Creates an instance of the Workflow Service Host that hosts the Counting Workflow and defines the endpoints under which the Counting Workflow can be reached.</span></span>  
  
-   <span data-ttu-id="2c7f7-116">Définit un comportement de magasin d'instances de workflow SQL, lequel est utilisé pour configurer le magasin d'instances de workflow SQL.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-116">Defines a SQL workflow instance store behavior, which is used to configure the SQL workflow instance store.</span></span> <span data-ttu-id="2c7f7-117">Le magasin a pour instruction de traiter `CountStatus` comme une propriété promue.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-117">The store is instructed to treat `CountStatus` as a promoted property.</span></span>  
  
-   <span data-ttu-id="2c7f7-118">Crée un client qui appelle la méthode de démarrage du workflow de comptage.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-118">Creates a client that calls the start method of the counting workflow.</span></span>  
  
 <span data-ttu-id="2c7f7-119">Une fois le programme démarré, le compteur commence automatiquement le comptage.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-119">Once the program is started, the counter automatically starts counting.</span></span> <span data-ttu-id="2c7f7-120">Notez que le chargement de l'instance et la configuration du magasin d'instances de workflow SQL peut prendre quelques secondes.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-120">Note that it might take a few seconds to load the instance and configure the SQL workflow instance store.</span></span>  
  
 <span data-ttu-id="2c7f7-121">Pour promouvoir la valeur du compteur en tant que propriété personnalisée, les étapes suivantes doivent être effectuées :</span><span class="sxs-lookup"><span data-stu-id="2c7f7-121">To promote the counter value as a custom property, the following steps must be taken:</span></span>  
  
1.  <span data-ttu-id="2c7f7-122">La classe `CounterStatus` définit une extension d'instance de type <xref:System.Activities.Persistence.PersistenceParticipant>, qui est utilisée par les activités pour fournir les variables d'état.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-122">The class `CounterStatus` defines an instance extension of type <xref:System.Activities.Persistence.PersistenceParticipant>, which is used by activities to supply the state variables.</span></span> <span data-ttu-id="2c7f7-123">`Count` est défini comme une valeur en écriture seule.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-123">`Count` is defined as a write-only value.</span></span> <span data-ttu-id="2c7f7-124">Lorsqu'une instance de workflow atteint un point de persistance, l'extension d'instance enregistre la propriété `Count` dans la collecte de données de persistance.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-124">When a workflow instance comes to a persistence point, the instance extension saves the `Count` property into the persistence data collection.</span></span>  
  
2.  <span data-ttu-id="2c7f7-125">Lors de la création du magasin d'instances, une nouvelle propriété, `CountStatus`, est définie via la méthode `store.Promote()`.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-125">When creating the instance store, a new property, `CountStatus`, is defined through the `store.Promote()` method.</span></span>  
  
3.  <span data-ttu-id="2c7f7-126">L'activité `SaveCounter` du workflow affecte la valeur actuelle du compteur au champ d'état `Count`.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-126">The workflow's `SaveCounter` activity assigns the current counter value to the `Count` status field.</span></span>  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="2c7f7-127">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="2c7f7-127">To use this sample</span></span>  
  
1.  <span data-ttu-id="2c7f7-128">Créez la base de données du magasin d'instances.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-128">Create the instance store database.</span></span>  
  
    1.  <span data-ttu-id="2c7f7-129">Ouvrez une invite de commandes [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2c7f7-129">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
    2.  <span data-ttu-id="2c7f7-130">Accédez au répertoire de l'exemple (\WF\Basic\Persistence\SqlStoreExtensibility\CS) et exécutez CreateInstanceStore.cmd dans l'invite de commandes [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2c7f7-130">Navigate to the sample directory (\WF\Basic\Persistence\SqlStoreExtensibility\CS) and run CreateInstanceStore.cmd in the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
        > [!WARNING]
        >  <span data-ttu-id="2c7f7-131">Le script CreateInstanceStore.cmd tente de créer la base de données sur l'instance par défaut de SQL Server 2008 Express.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-131">The CreateInstanceStore.cmd script attempts to create the database on the default instance of SQL Server 2008 Express.</span></span> <span data-ttu-id="2c7f7-132">Si vous voulez installer la base de données sur une instance différente, modifiez le script en conséquence.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-132">If you want to install the database on a different instance, modify the script to do so.</span></span>  
  
2.  <span data-ttu-id="2c7f7-133">Ouvrez [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] et chargez la solution SqlStoreExtensibility.sln, puis générez-la en appuyant sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-133">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and load the SqlStoreExtensibility.sln solution and build it by pressing CTRL+SHIFT+B.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="2c7f7-134">Si vous avez installé la base de données sur une instance autre que l'instance par défaut de SQL Server, mettez à jour la chaîne de connexion dans le code avant de générer la solution.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-134">If you installed the database on a non-default instance of SQL Server, update the connection string in the code prior to building the solution.</span></span>  
  
3.  <span data-ttu-id="2c7f7-135">Exécuter l’exemple avec des privilèges d’administrateur, accédez au répertoire bin du projet (\WF\Basic\Persistence\SqlStoreExtensibility\bin\Debug) dans [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], droit sur SqlStoreExtensibility.exe, puis sélectionnez **d’identification Administrateur**.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-135">Run the sample with administrator privileges by navigating to the project’s bin directory (\WF\Basic\Persistence\SqlStoreExtensibility\bin\Debug) in [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], right-clicking SqlStoreExtensibility.exe and selecting **Run as Administrator**.</span></span>  
  
### <a name="to-verify-the-sample-is-working-correctly"></a><span data-ttu-id="2c7f7-136">Pour vérifier que l'exemple fonctionne correctement</span><span class="sxs-lookup"><span data-stu-id="2c7f7-136">To verify the sample is working correctly</span></span>  
  
1.  <span data-ttu-id="2c7f7-137">SQL Server Management Studio permet d’afficher le contenu de la table des instances en sélectionnant **bases de données**, **InstanceStore**, puis  **System.ServiceModel.Activities.DurableInstancing.InstanceTable** dans l’Explorateur d’objets, cliquez sur **System.ServiceModel.Activities.DurableInstancing.InstanceTable** et sélectionnez  **Sélectionner les 1000 lignes**.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-137">Use SQL Server Management Studio to view the contents of the instance table by selecting **Databases**, **InstanceStore**, and then **System.ServiceModel.Activities.DurableInstancing.InstanceTable** in the Object Explorer, right-click **System.ServiceModel.Activities.DurableInstancing.InstanceTable** and select **Select Top 1000 Rows**.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="2c7f7-138">SQL Server Management Studio, consultez [présentation de SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=165645)</span><span class="sxs-lookup"><span data-stu-id="2c7f7-138"> SQL Server Management Studio, see [Introducing SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=165645)</span></span>  
  
2.  <span data-ttu-id="2c7f7-139">Observez les instances de workflow répertoriées.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-139">Observe the workflow instances listed.</span></span>  
  
3.  <span data-ttu-id="2c7f7-140">Dans une invite de commandes [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], exécutez le script QueryInstanceStore.cmd situé dans le répertoire de l'exemple (\WF\Basic\Persistence\SqlStoreExtensibility).</span><span class="sxs-lookup"><span data-stu-id="2c7f7-140">In a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, run the QueryInstanceStore.cmd script located in the sample directory (\WF\Basic\Persistence\SqlStoreExtensibility).</span></span>  
  
4.  <span data-ttu-id="2c7f7-141">Observez la valeur du compteur affichée sous **CountStatus**.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-141">Observe the counter value displayed under **CountStatus**.</span></span>  
  
5.  <span data-ttu-id="2c7f7-142">Exécutez le script plusieurs fois pour voir les **CountStats** modification de valeur.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-142">Run the script a few times to see the **CountStats** value change.</span></span>  
  
6.  <span data-ttu-id="2c7f7-143">Appuyez sur ENTRÉE pour mettre fin à l'application de workflow.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-143">Press ENTER to terminate the workflow application.</span></span>  
  
### <a name="to-uninstall-the-sample"></a><span data-ttu-id="2c7f7-144">Pour désinstaller l'exemple</span><span class="sxs-lookup"><span data-stu-id="2c7f7-144">To uninstall the sample</span></span>  
  
1.  <span data-ttu-id="2c7f7-145">Supprimez la base de données du magasin d'instances en exécutant le script RemoveInstanceStore.cmd situé dans le répertoire de l'exemple (\WF\Basic\Persistence\SqlStoreExtensibility).</span><span class="sxs-lookup"><span data-stu-id="2c7f7-145">Remove the instance store database by running the RemoveInstanceStore.cmd script located in the sample directory (\WF\Basic\Persistence\SqlStoreExtensibility).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2c7f7-146">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-146">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2c7f7-147">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-147">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2c7f7-148">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2c7f7-148">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2c7f7-149">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="2c7f7-149">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\SQLStoreExtensibility`  
  
## <a name="see-also"></a><span data-ttu-id="2c7f7-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2c7f7-150">See Also</span></span>  
 [<span data-ttu-id="2c7f7-151">Persistance du workflow</span><span class="sxs-lookup"><span data-stu-id="2c7f7-151">Workflow Persistence</span></span>](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)  
 [<span data-ttu-id="2c7f7-152">Services de workflow</span><span class="sxs-lookup"><span data-stu-id="2c7f7-152">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="2c7f7-153">Hébergement de AppFabric et exemples de persistance</span><span class="sxs-lookup"><span data-stu-id="2c7f7-153">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
