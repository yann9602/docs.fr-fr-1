---
title: Utilisation de WorkflowIdentity et du versioning
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8451735-8046-478f-912b-40870a6c0c3a
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 033392276fb233bc1baa6c2af372a844e06a7d62
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="using-workflowidentity-and-versioning"></a><span data-ttu-id="5e114-102">Utilisation de WorkflowIdentity et du versioning</span><span class="sxs-lookup"><span data-stu-id="5e114-102">Using WorkflowIdentity and Versioning</span></span>
<span data-ttu-id="5e114-103"><xref:System.Activities.WorkflowIdentity> permet aux développeurs d'applications de workflow d'associer un nom et un <xref:System.Version> à une définition de workflow, et d'associer ces informations à une instance persistante de workflow.</span><span class="sxs-lookup"><span data-stu-id="5e114-103"><xref:System.Activities.WorkflowIdentity> provides a way for workflow application developers to associate a name and a <xref:System.Version> with a workflow definition, and for this information to be associated with a persisted workflow instance.</span></span> <span data-ttu-id="5e114-104">Ces informations d'identité peuvent être utilisées par les développeurs d'applications de workflow pour activer des scénarios tels que l'exécution côte à côte de plusieurs versions d'une définition de workflow, et fournir la base d'autres fonctionnalités telles que la mise à jour dynamique.</span><span class="sxs-lookup"><span data-stu-id="5e114-104">This identity information can be used by workflow application developers to enable scenarios such as side-by-side execution of multiple versions of a workflow definition, and provides the cornerstone for other functionality such as dynamic update.</span></span> <span data-ttu-id="5e114-105">Cette rubrique fournit une vue d'ensemble de l'utilisation de <xref:System.Activities.WorkflowIdentity> avec l'hébergement <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="5e114-105">This topic provides as overview of using <xref:System.Activities.WorkflowIdentity> with <xref:System.Activities.WorkflowApplication> hosting.</span></span> <span data-ttu-id="5e114-106">Pour plus d’informations sur l’exécution côte à côte de définitions de workflow dans un service de workflow, consultez [le contrôle de version côte à côte dans WorkflowServiceHost](../../../docs/framework/wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).</span><span class="sxs-lookup"><span data-stu-id="5e114-106">For information on side-by-side execution of workflow definitions in a workflow service, see [Side by Side Versioning in WorkflowServiceHost](../../../docs/framework/wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).</span></span> <span data-ttu-id="5e114-107">Pour plus d’informations sur la mise à jour dynamique, consultez [mise à jour dynamique](../../../docs/framework/windows-workflow-foundation/dynamic-update.md).</span><span class="sxs-lookup"><span data-stu-id="5e114-107">For information on dynamic update, see [Dynamic Update](../../../docs/framework/windows-workflow-foundation/dynamic-update.md).</span></span>  
  
## <a name="in-this-topic"></a><span data-ttu-id="5e114-108">Dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="5e114-108">In this topic</span></span>  
  
-   [<span data-ttu-id="5e114-109">Utilisation de WorkflowIdentity</span><span class="sxs-lookup"><span data-stu-id="5e114-109">Using WorkflowIdentity</span></span>](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UsingWorkflowIdentity)  
  
    -   [<span data-ttu-id="5e114-110">Exécution côte à côte à l’aide de WorkflowIdentity</span><span class="sxs-lookup"><span data-stu-id="5e114-110">Side-by-side Execution using WorkflowIdentity</span></span>](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#SxS)  
  
-   [<span data-ttu-id="5e114-111">La mise à niveau des bases de données de persistance 4 .NET Framework pour prendre en charge le Versioning de Workflow</span><span class="sxs-lookup"><span data-stu-id="5e114-111">Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning</span></span>](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)  
  
    -   [<span data-ttu-id="5e114-112">Pour mettre à niveau le schéma de base de données</span><span class="sxs-lookup"><span data-stu-id="5e114-112">To upgrade the database schema</span></span>](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#ToUpgrade)  
  
##  <span data-ttu-id="5e114-113"><a name="UsingWorkflowIdentity"></a>Utilisation de WorkflowIdentity</span><span class="sxs-lookup"><span data-stu-id="5e114-113"><a name="UsingWorkflowIdentity"></a> Using WorkflowIdentity</span></span>  
 <span data-ttu-id="5e114-114">Pour utiliser <xref:System.Activities.WorkflowIdentity>, créez une instance, configurez-la et associez-la à une instance <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="5e114-114">To use <xref:System.Activities.WorkflowIdentity>, create an instance, configure it, and associate it with a <xref:System.Activities.WorkflowApplication> instance.</span></span> <span data-ttu-id="5e114-115">Une instance <xref:System.Activities.WorkflowIdentity> contient trois informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="5e114-115">A <xref:System.Activities.WorkflowIdentity> instance contains three identifying pieces of information.</span></span> <span data-ttu-id="5e114-116"><xref:System.Activities.WorkflowIdentity.Name%2A> et <xref:System.Activities.WorkflowIdentity.Version%2A> contiennent un nom et un <xref:System.Version> et sont obligatoire, et <xref:System.Activities.WorkflowIdentity.Package%2A> est facultatif et peut être utilisé pour spécifier une chaîne supplémentaire contenant des informations telles que le nom de l'assembly ou d'autres informations souhaitées.</span><span class="sxs-lookup"><span data-stu-id="5e114-116"><xref:System.Activities.WorkflowIdentity.Name%2A> and <xref:System.Activities.WorkflowIdentity.Version%2A> contain a name and a <xref:System.Version> and are required, and <xref:System.Activities.WorkflowIdentity.Package%2A> is optional and can be used to specify an additional string containing information such as assembly name or other desired information.</span></span> <span data-ttu-id="5e114-117"><xref:System.Activities.WorkflowIdentity> est unique si l'une de ses trois propriétés est différente d'un autre <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="5e114-117">A <xref:System.Activities.WorkflowIdentity> is unique if any of its three properties are different from another <xref:System.Activities.WorkflowIdentity>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5e114-118">Un <xref:System.Activities.WorkflowIdentity> ne devrait contenir aucune information d'identification personnelle (PII).</span><span class="sxs-lookup"><span data-stu-id="5e114-118">A <xref:System.Activities.WorkflowIdentity> should not contain any personally identifiable information (PII).</span></span> <span data-ttu-id="5e114-119">Les informations relatives au <xref:System.Activities.WorkflowIdentity> utilisées pour créer une instance sont émises vers n'importe quel service de suivi configuré sur plusieurs points du cycle de vie du workflow différents par le runtime.</span><span class="sxs-lookup"><span data-stu-id="5e114-119">Information about the <xref:System.Activities.WorkflowIdentity> used to create an instance is emitted to any configured tracking services at several different points of the activity life-cycle by the runtime.</span></span> <span data-ttu-id="5e114-120">Le suivi WF ne dispose pas d'un mécanisme de masquage des informations PII (données utilisateur sensibles).</span><span class="sxs-lookup"><span data-stu-id="5e114-120">WF Tracking does not have any mechanism to hide PII (sensitive user data).</span></span> <span data-ttu-id="5e114-121">Par conséquent, une instance <xref:System.Activities.WorkflowIdentity> ne doit contenir aucune donnée PII, car elle est émise par le runtime dans les enregistrements de suivi et peut être vue par n'importe quelle personne qui dispose d'un accès permettant d'afficher les enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="5e114-121">Therefore, a <xref:System.Activities.WorkflowIdentity> instance should not contain any PII data as it will be emitted by the runtime in tracking records and may be visible to anyone with access to view the tracking records.</span></span>  
  
 <span data-ttu-id="5e114-122">Dans l'exemple suivant, un <xref:System.Activities.WorkflowIdentity> est créé et associé à une instance d'un workflow créée à l'aide d'une définition de workflow `MortgageWorkflow`.</span><span class="sxs-lookup"><span data-stu-id="5e114-122">In the following example, a <xref:System.Activities.WorkflowIdentity> is created and associated with an instance of a workflow created using a `MortgageWorkflow` workflow definition.</span></span>  
  
```csharp  
WorkflowIdentity identityV1 = new WorkflowIdentity  
{  
    Name = "MortgageWorkflow v1",  
    Version = new Version(1, 0, 0, 0)  
};  
  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Run the workflow.  
wfApp.Run();  
```  
  
 <span data-ttu-id="5e114-123">Lors du rechargement et de la reprise d'un workflow, un <xref:System.Activities.WorkflowIdentity>, configuré pour correspondre à <xref:System.Activities.WorkflowIdentity> de l'instance persistante de workflow doit être utilisé.</span><span class="sxs-lookup"><span data-stu-id="5e114-123">When reloading and resuming a workflow, a <xref:System.Activities.WorkflowIdentity> that is configured to match the <xref:System.Activities.WorkflowIdentity> of the persisted workflow instance must be used.</span></span>  
  
```csharp  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Load the workflow.  
wfApp.Load(instanceId);  
  
// Resume the workflow...  
```  
  
 <span data-ttu-id="5e114-124">Si <xref:System.Activities.WorkflowIdentity> utilisé pour recharger l'instance du workflow ne correspond pas au <xref:System.Activities.WorkflowIdentity> persistant, une exception <xref:System.Activities.VersionMismatchException> est levée.</span><span class="sxs-lookup"><span data-stu-id="5e114-124">If the <xref:System.Activities.WorkflowIdentity> used when reloading the workflow instance does not match the persisted <xref:System.Activities.WorkflowIdentity>, a <xref:System.Activities.VersionMismatchException> is thrown.</span></span> <span data-ttu-id="5e114-125">Dans l'exemple suivant, une tentative de chargement est faite sur l'instance `MortgageWorkflow` qui a été rendue persistante dans l'exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="5e114-125">In the following example a load attempt is made on the `MortgageWorkflow` instance that was persisted in the previous example.</span></span> <span data-ttu-id="5e114-126">Cette tentative de chargement est effectuée à l'aide de <xref:System.Activities.WorkflowIdentity> configuré pour une version plus récente du workflow d'emprunts qui ne correspond pas à l'instance persistante.</span><span class="sxs-lookup"><span data-stu-id="5e114-126">This load attempt is made using a <xref:System.Activities.WorkflowIdentity> configured for a newer version of the mortgage workflow that does not match the persisted instance.</span></span>  
  
```csharp  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow_v2(), identityV2);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Attempt to load the workflow instance.  
wfApp.Load(instanceId);  
  
// Resume the workflow...  
```  
  
 <span data-ttu-id="5e114-127">Lorsque le code précédent est exécuté, l'exception <xref:System.Activities.VersionMismatchException> suivante est levée.</span><span class="sxs-lookup"><span data-stu-id="5e114-127">When the previous code is executed, the following <xref:System.Activities.VersionMismatchException> is thrown.</span></span>  
  
 <span data-ttu-id="5e114-128">**Le WorkflowIdentity ('MortgageWorkflow v1 ; Version = 1.0.0.0") de l’instance chargée ne correspond pas au WorkflowIdentity ('MortgageWorkflow v2 ; Version = 2.0.0.0") de la définition de workflow fournie. L’instance peut être chargée à l’aide d’une autre définition, ou de mettre à jour à l’aide de la mise à jour dynamique.**</span><span class="sxs-lookup"><span data-stu-id="5e114-128">**The WorkflowIdentity ('MortgageWorkflow v1; Version=1.0.0.0') of the loaded instance does not match the WorkflowIdentity ('MortgageWorkflow v2; Version=2.0.0.0') of the provided workflow definition. The instance can be loaded using a different definition, or updated using Dynamic Update.**</span></span>  
###  <span data-ttu-id="5e114-129"><a name="SxS"></a>Exécution côte à côte à l’aide de WorkflowIdentity</span><span class="sxs-lookup"><span data-stu-id="5e114-129"><a name="SxS"></a> Side-by-side Execution using WorkflowIdentity</span></span>  
 <span data-ttu-id="5e114-130"><xref:System.Activities.WorkflowIdentity> peut être utilisé pour faciliter l'exécution de plusieurs versions d'un workflow côte à côte.</span><span class="sxs-lookup"><span data-stu-id="5e114-130"><xref:System.Activities.WorkflowIdentity> can be used to facilitate the execution of multiple versions of a workflow side-by-side.</span></span> <span data-ttu-id="5e114-131">Un scénario courant modifie les besoins de l'entreprise sur un workflow de longue durée.</span><span class="sxs-lookup"><span data-stu-id="5e114-131">One common scenario is changing business requirements on a long-running workflow.</span></span> <span data-ttu-id="5e114-132">De nombreuses instances d'un workflow peuvent s'exécuter lorsqu'une version mise à jour est déployée.</span><span class="sxs-lookup"><span data-stu-id="5e114-132">Many instances of a workflow could be running when an updated version is deployed.</span></span> <span data-ttu-id="5e114-133">L'application hôte peut être configurée pour utiliser la définition mise à jour de workflow lors du démarrage de nouvelles instances, et il est de la responsabilité de l'application hôte de fournir la définition correcte de workflow lors de la reprise des instances.</span><span class="sxs-lookup"><span data-stu-id="5e114-133">The host application can be configured to use the updated workflow definition when starting new instances, and it is the responsibility of the host application to provide the correct workflow definition when resuming instances.</span></span> <span data-ttu-id="5e114-134"><xref:System.Activities.WorkflowIdentity> peut être utilisé pour identifier et fournir la définition correspondante de workflow lors de la reprise des instances de workflow.</span><span class="sxs-lookup"><span data-stu-id="5e114-134"><xref:System.Activities.WorkflowIdentity> can be used to identify and supply the matching workflow definition when resuming workflow instances.</span></span>  
  
 <span data-ttu-id="5e114-135">Pour récupérer le <xref:System.Activities.WorkflowIdentity> d'une instance persistante de workflow, la méthode <xref:System.Activities.WorkflowApplication.GetInstance%2A> est utilisée.</span><span class="sxs-lookup"><span data-stu-id="5e114-135">To retrieve the <xref:System.Activities.WorkflowIdentity> of a persisted workflow instance, the <xref:System.Activities.WorkflowApplication.GetInstance%2A> method is used.</span></span> <span data-ttu-id="5e114-136">La méthode <xref:System.Activities.WorkflowApplication.GetInstance%2A> prend le <xref:System.Activities.WorkflowApplication.Id%2A> de l'instance persistante de workflow et le <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> qui contient l'instance rendue persistante et retourne un <xref:System.Activities.WorkflowApplicationInstance>.</span><span class="sxs-lookup"><span data-stu-id="5e114-136">The <xref:System.Activities.WorkflowApplication.GetInstance%2A> method takes the <xref:System.Activities.WorkflowApplication.Id%2A> of the persisted workflow instance and the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> that contains the persisted instance and returns a <xref:System.Activities.WorkflowApplicationInstance>.</span></span> <span data-ttu-id="5e114-137">Un <xref:System.Activities.WorkflowApplicationInstance> contient des informations sur une instance persistante de workflow, y compris son <xref:System.Activities.WorkflowIdentity> associé.</span><span class="sxs-lookup"><span data-stu-id="5e114-137">A <xref:System.Activities.WorkflowApplicationInstance> contains information about a persisted workflow instance, including its associated <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="5e114-138">Ce <xref:System.Activities.WorkflowIdentity> associé peut être utilisé par l'hôte pour fournir la définition correcte de workflow lors du chargement et de la reprise de l'instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="5e114-138">This associated <xref:System.Activities.WorkflowIdentity> can be used by the host to supply the correct workflow definition when loading and resuming the workflow instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e114-139">Un <xref:System.Activities.WorkflowIdentity> null est valide, et peut être utilisé par l'hôte pour mapper les instances qui ont été rendues persistantes sans <xref:System.Activities.WorkflowIdentity> associé à la définition appropriée de workflow.</span><span class="sxs-lookup"><span data-stu-id="5e114-139">A null <xref:System.Activities.WorkflowIdentity> is valid, and can be used by the host to map instances that were persisted with no associated <xref:System.Activities.WorkflowIdentity> to the proper workflow definition.</span></span> <span data-ttu-id="5e114-140">Ce scénario peut se produire lorsqu'une application de workflow n'a pas été écrite initialement avec versioning de workflow, ou lorsqu'une application est mise à niveau à partir du [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5e114-140">This scenario can occur when a workflow application was not initially written with workflow versioning, or when an application is upgraded from [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="5e114-141">[La mise à niveau des bases de données de persistance .NET Framework 4 pour prendre en charge le Versioning de Workflow](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).</span><span class="sxs-lookup"><span data-stu-id="5e114-141"> [Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).</span></span>  
  
 <span data-ttu-id="5e114-142">Dans l’exemple suivant un `Dictionary<WorkflowIdentity, Activity>` est utilisé pour associer <xref:System.Activities.WorkflowIdentity> instances avec leurs définitions correspondantes de workflow et d’un flux de travail est démarré à l’aide de la `MortgageWorkflow` définition de flux de travail, qui est associée à la `identityV1` <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="5e114-142">In the following example a `Dictionary<WorkflowIdentity, Activity>` is used to associate <xref:System.Activities.WorkflowIdentity> instances with their matching workflow definitions, and a workflow is started using the `MortgageWorkflow` workflow definition, which is associated with the `identityV1` <xref:System.Activities.WorkflowIdentity>.</span></span>  
  
```csharp  
WorkflowIdentity identityV1 = new WorkflowIdentity  
{  
    Name = "MortgageWorkflow v1",  
    Version = new Version(1, 0, 0, 0)  
};  
  
WorkflowIdentity identityV2 = new WorkflowIdentity  
{  
    Name = "MortgageWorkflow v2",  
    Version = new Version(2, 0, 0, 0)  
};  
  
Dictionary<WorkflowIdentity, Activity> WorkflowVersionMap = new Dictionary<WorkflowIdentity, Activity>();  
WorkflowVersionMap.Add(identityV1, new MortgageWorkflow());  
WorkflowVersionMap.Add(identityV2, new MortgageWorkflow_v2());  
  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Run the workflow.  
wfApp.Run();  
```  
  
 <span data-ttu-id="5e114-143">Dans l'exemple suivant, les informations sur l'instance persistante de workflow de l'exemple précédent sont récupérées en appelant <xref:System.Activities.WorkflowApplication.GetInstance%2A>, et les informations <xref:System.Activities.WorkflowIdentity> persistantes sont utilisées pour récupérer la définition correspondante de workflow.</span><span class="sxs-lookup"><span data-stu-id="5e114-143">In the following example, information about the persisted workflow instance from the previous example is retrieved by calling <xref:System.Activities.WorkflowApplication.GetInstance%2A>, and the persisted <xref:System.Activities.WorkflowIdentity> information is used to retrieve the matching workflow definition.</span></span> <span data-ttu-id="5e114-144">Ces informations sont utilisées pour configurer <xref:System.Activities.WorkflowApplication>, puis le workflow est chargé.</span><span class="sxs-lookup"><span data-stu-id="5e114-144">This information is used to configure the <xref:System.Activities.WorkflowApplication>, and then the workflow is loaded.</span></span> <span data-ttu-id="5e114-145">Étant donné que la surcharge <xref:System.Activities.WorkflowApplication.Load%2A> qui prend <xref:System.Activities.WorkflowApplicationInstance> est utilisée, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> qui a été configuré sur <xref:System.Activities.WorkflowApplicationInstance> est utilisé par <xref:System.Activities.WorkflowApplication> et par conséquent sa propriété <xref:System.Activities.WorkflowApplication.InstanceStore%2A> n'a pas besoin d'être configurée.</span><span class="sxs-lookup"><span data-stu-id="5e114-145">Note that because the <xref:System.Activities.WorkflowApplication.Load%2A> overload that takes the <xref:System.Activities.WorkflowApplicationInstance> is used, the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> that was configured on the <xref:System.Activities.WorkflowApplicationInstance> is used by the <xref:System.Activities.WorkflowApplication> and therefore its <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property does not need to be configured.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e114-146">Si la propriété <xref:System.Activities.WorkflowApplication.InstanceStore%2A> est définie, elle doit être définie avec la même instance <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> que celle utilisée par <xref:System.Activities.WorkflowApplicationInstance>, sinon une exception <xref:System.ArgumentException> sera levée avec le message suivant : `The instance is configured with a different InstanceStore than this WorkflowApplication.`.</span><span class="sxs-lookup"><span data-stu-id="5e114-146">If the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property is set, it must be set with the same <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> instance used by the <xref:System.Activities.WorkflowApplicationInstance> or else an <xref:System.ArgumentException> will be thrown with the following message: `The instance is configured with a different InstanceStore than this WorkflowApplication.`.</span></span>  
  
```csharp  
// Get the WorkflowApplicationInstance of the desired workflow from the specified  
// SqlWorkflowInstanceStore.  
WorkflowApplicationInstance instance = WorkflowApplication.GetInstance(instanceId, store);  
  
// Use the persisted WorkflowIdentity to retrieve the correct workflow  
// definition from the dictionary.  
Activity definition = WorkflowVersionMap[instance.DefinitionIdentity];  
  
WorkflowApplication wfApp = new WorkflowApplication(definition, instance.DefinitionIdentity);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Load the persisted workflow instance.  
wfApp.Load(instance);  
  
// Resume the workflow...  
```  
  
##  <span data-ttu-id="5e114-147"><a name="UpdatingWF4PersistenceDatabases"></a>La mise à niveau des bases de données de persistance 4 .NET Framework pour prendre en charge le Versioning de Workflow</span><span class="sxs-lookup"><span data-stu-id="5e114-147"><a name="UpdatingWF4PersistenceDatabases"></a> Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning</span></span>  
 <span data-ttu-id="5e114-148">Le script de base de données SqlWorkflowInstanceStoreSchemaUpgrade.sql est fourni pour mettre à niveau les bases de données de persistance créées à l'aide de scripts de base de données [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5e114-148">A SqlWorkflowInstanceStoreSchemaUpgrade.sql database script is provided to upgrade persistence databases created using the [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] database scripts.</span></span> <span data-ttu-id="5e114-149">Ce script met à jour les bases de données pour prendre en charge les nouvelles fonctions de versioning introduites dans le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5e114-149">This script updates the databases to support the new versioning capabilities introduced in [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="5e114-150">Des valeurs de versioning par défaut sont attribuées à toutes les instances persistantes de workflow dans les bases de données et ces instances peuvent ensuite participer côte à côte à l'exécution et à la mise à jour dynamique.</span><span class="sxs-lookup"><span data-stu-id="5e114-150">Any persisted workflow instances in the databases are given default versioning values, and can then participate in side-by-side execution and dynamic update.</span></span>  
  
 <span data-ttu-id="5e114-151">Si une application de workflow [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] tente d'effectuer une opération de persistance qui utilise les nouvelles fonctions de versioning sur une base de données de persistance qui n'a pas été mise à niveau à l'aide du script indiqué, une exception <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> est levée avec un message similaire au message suivant.</span><span class="sxs-lookup"><span data-stu-id="5e114-151">If a [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] workflow application attempts any persistence operations that use the new versioning features on a persistence database which has not been upgraded using the provided script, an <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> is thrown with a message similar to the following message.</span></span>  
  
 <span data-ttu-id="5e114-152">**SqlWorkflowInstanceStore a une version de base de données de « 4.0.0.0 ». InstancePersistenceCommand « System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand » ne peut pas être exécuté sur cette version de la base de données.  Mettez à niveau la base de données « 4.5.0.0 ».**</span><span class="sxs-lookup"><span data-stu-id="5e114-152">**The SqlWorkflowInstanceStore has a database version of '4.0.0.0'. InstancePersistenceCommand 'System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand' cannot be run against this database version.  Please upgrade the database to '4.5.0.0'.**</span></span>  
###  <span data-ttu-id="5e114-153"><a name="ToUpgrade"></a>Pour mettre à niveau le schéma de base de données</span><span class="sxs-lookup"><span data-stu-id="5e114-153"><a name="ToUpgrade"></a> To upgrade the database schema</span></span>  
  
1.  <span data-ttu-id="5e114-154">Ouvrez SQL Server Management Studio et connectez-vous au serveur de base de données de persistance, par exemple **. \SQLEXPRESS**.</span><span class="sxs-lookup"><span data-stu-id="5e114-154">Open SQL Server Management Studio and connect to the persistence database server, for example **.\SQLEXPRESS**.</span></span>  
  
2.  <span data-ttu-id="5e114-155">Choisissez **ouvrir**, **fichier** à partir de la **fichier** menu.</span><span class="sxs-lookup"><span data-stu-id="5e114-155">Choose **Open**, **File** from the **File** menu.</span></span> <span data-ttu-id="5e114-156">Accédez au dossier suivant : `C:\Windows\Microsoft.NET\Framework\4.0.30319\sql\en`</span><span class="sxs-lookup"><span data-stu-id="5e114-156">Browse to the following folder: `C:\Windows\Microsoft.NET\Framework\4.0.30319\sql\en`</span></span>  
  
3.  <span data-ttu-id="5e114-157">Sélectionnez **SqlWorkflowInstanceStoreSchemaUpgrade.sql** et cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="5e114-157">Select **SqlWorkflowInstanceStoreSchemaUpgrade.sql** and click **Open**.</span></span>  
  
4.  <span data-ttu-id="5e114-158">Sélectionnez le nom de la base de données de persistance dans le **bases de données disponibles** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="5e114-158">Select the name of the persistence database in the **Available Databases** drop-down.</span></span>  
  
5.  <span data-ttu-id="5e114-159">Choisissez **Execute** à partir de la **requête** menu.</span><span class="sxs-lookup"><span data-stu-id="5e114-159">Choose **Execute** from the **Query** menu.</span></span>  
  
 <span data-ttu-id="5e114-160">Lorsque la requête est terminée, le schéma de base de données est mis à niveau, et si vous le souhaitez, vous pouvez afficher l'identité du workflow par défaut affectée aux instances persistantes de workflow.</span><span class="sxs-lookup"><span data-stu-id="5e114-160">When the query completes, the database schema is upgraded, and if desired, you can view the default workflow identity that was assigned to the persisted workflow instances.</span></span> <span data-ttu-id="5e114-161">Développez la base de données de persistance dans le **bases de données** nœud de la **l’Explorateur d’objets**, puis développez le **vues** nœud.</span><span class="sxs-lookup"><span data-stu-id="5e114-161">Expand your persistence database in the **Databases** node of the **Object Explorer**, and then expand the **Views** node.</span></span> <span data-ttu-id="5e114-162">Avec le bouton droit **System.Activities.DurableInstancing.Instances** et choisissez **sélectionnez 1000 lignes du haut**.</span><span class="sxs-lookup"><span data-stu-id="5e114-162">Right-click **System.Activities.DurableInstancing.Instances** and choose **Select Top 1000 Rows**.</span></span> <span data-ttu-id="5e114-163">Faites défiler jusqu'à la fin des colonnes et notez qu’il existe six colonnes supplémentaires ajoutées à la vue : **IdentityName**, **IdentityPackage**, **générer**, **principale** , **Secondaire**, et **révision**.</span><span class="sxs-lookup"><span data-stu-id="5e114-163">Scroll to end of the columns and note that there are six additional columns added to the view: **IdentityName**, **IdentityPackage**, **Build**, **Major**, **Minor**, and **Revision**.</span></span> <span data-ttu-id="5e114-164">Les workflows persistants auront une valeur de **NULL** pour ces champs, qui représente une identité de workflow null.</span><span class="sxs-lookup"><span data-stu-id="5e114-164">Any persisted workflows will have a value of **NULL** for these fields, representing a null workflow identity.</span></span>
