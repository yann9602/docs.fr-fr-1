---
title: "Procédure : activer la persistance pour les workflows et les services de workflow"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: eb380b8fdfb6b293cfcd02f056895109bf221d83
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="9d778-102">Procédure : activer la persistance pour les workflows et les services de workflow</span><span class="sxs-lookup"><span data-stu-id="9d778-102">How to: Enable Persistence for Workflows and Workflow Services</span></span>
<span data-ttu-id="9d778-103">Cette rubrique décrit la procédure d'activation de la persistance pour les flux de travail et les services de workflow.</span><span class="sxs-lookup"><span data-stu-id="9d778-103">This topic describes how to enable persistence for workflows and workflow services.</span></span>  
  
## <a name="enable-persistence-for-workflows"></a><span data-ttu-id="9d778-104">Activation de la persistance pour les flux de travail</span><span class="sxs-lookup"><span data-stu-id="9d778-104">Enable Persistence for Workflows</span></span>  
 <span data-ttu-id="9d778-105">Vous pouvez associer un magasin d’instances avec un **WorkflowApplication** à l’aide de la <xref:System.Activities.WorkflowApplication.InstanceStore%2A> propriété de la <xref:System.Activities.WorkflowApplication> classe.</span><span class="sxs-lookup"><span data-stu-id="9d778-105">You can associate an instance store with a **WorkflowApplication** by using the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property of the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="9d778-106">La méthode <xref:System.Activities.WorkflowApplication.Persist%2A> enregistre ou rend persistant un flux de travail dans le magasin d'instances associé à l'application.</span><span class="sxs-lookup"><span data-stu-id="9d778-106">The <xref:System.Activities.WorkflowApplication.Persist%2A> method saves or persists a workflow into the instance store associated with the application.</span></span> <span data-ttu-id="9d778-107">La méthode <xref:System.Activities.WorkflowApplication.Unload%2A> rend persistant un flux de travail dans le magasin d'instances, puis décharge l'instance de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="9d778-107">The <xref:System.Activities.WorkflowApplication.Unload%2A> method persists a workflow into the instance store and then unloads the instance from the memory.</span></span> <span data-ttu-id="9d778-108">Le **charge** méthode charge un flux de travail en mémoire à l’aide des données de workflow stockées dans le magasin de persistance d’instance.</span><span class="sxs-lookup"><span data-stu-id="9d778-108">The **Load** method loads a workflow into memory using the workflow data stored in the instance persistence store.</span></span>  
  
 <span data-ttu-id="9d778-109">Le **Persist** méthode effectue les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="9d778-109">The **Persist** method performs the following steps:</span></span>  
  
1.  <span data-ttu-id="9d778-110">Suspend le service de planification de workflow et attend jusqu'à ce que le flux de travail entre en état d'inactivité.</span><span class="sxs-lookup"><span data-stu-id="9d778-110">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>  
  
2.  <span data-ttu-id="9d778-111">Rend le flux de travail persistant ou l'enregistre dans le magasin de persistance.</span><span class="sxs-lookup"><span data-stu-id="9d778-111">Persists or saves the workflow into the persistence store.</span></span>  
  
3.  <span data-ttu-id="9d778-112">Reprend le service de planification de workflow.</span><span class="sxs-lookup"><span data-stu-id="9d778-112">Resumes the workflow scheduler.</span></span>  
  
 <span data-ttu-id="9d778-113">Le **Unload** méthode effectue les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="9d778-113">The **Unload** method performs the following steps:</span></span>  
  
1.  <span data-ttu-id="9d778-114">Suspend le service de planification de workflow et attend jusqu'à ce que le flux de travail entre en état d'inactivité.</span><span class="sxs-lookup"><span data-stu-id="9d778-114">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>  
  
2.  <span data-ttu-id="9d778-115">Rend le flux de travail persistant ou l'enregistre dans le magasin de persistance.</span><span class="sxs-lookup"><span data-stu-id="9d778-115">Persists or saves the workflow into the persistence store.</span></span>  
  
3.  <span data-ttu-id="9d778-116">Supprime l'instance de workflow en mémoire.</span><span class="sxs-lookup"><span data-stu-id="9d778-116">Disposes the workflow instance in the memory.</span></span>  
  
 <span data-ttu-id="9d778-117">Les deux le **Persist** et **Unload** méthodes se bloquent pendant un flux de travail est dans une zone de non-persistance jusqu'à ce que le flux de travail quitte la zone sans persistance.</span><span class="sxs-lookup"><span data-stu-id="9d778-117">Both the **Persist** and **Unload** methods will block while a workflow is in a no-persist zone until the workflow exits the no-persist zone.</span></span> <span data-ttu-id="9d778-118">La méthode poursuit les opérations de persistance ou de déchargement une fois la zone sans persistance fermée.</span><span class="sxs-lookup"><span data-stu-id="9d778-118">The method continues with the persist or unload operation after the no-persist zone completes.</span></span> <span data-ttu-id="9d778-119">Si la zone sans persistance ne se ferme pas avant que le délai d'attente ne s'écoule ou si le processus de persistance prend trop de temps, une TimeoutException est levée.</span><span class="sxs-lookup"><span data-stu-id="9d778-119">If the no-persist zone does not complete before the time-out elapses, or if the persistence process takes too long, a TimeoutException will be thrown.</span></span>  
  
## <a name="enable-persistence-for-workflow-services-in-code"></a><span data-ttu-id="9d778-120">Activation de la persistance pour les services de workflow dans le code</span><span class="sxs-lookup"><span data-stu-id="9d778-120">Enable Persistence for Workflow Services in Code</span></span>  
 <span data-ttu-id="9d778-121">Le **DurableInstancingOptions** membre de la <xref:System.ServiceModel.WorkflowServiceHost> classe a une propriété nommée **InstanceStore** que vous pouvez utiliser pour associer un magasin d’instances le **WorkflowServiceHost** .</span><span class="sxs-lookup"><span data-stu-id="9d778-121">The **DurableInstancingOptions** member of the <xref:System.ServiceModel.WorkflowServiceHost> class has a property named **InstanceStore** that you can use to associate an instance store with the **WorkflowServiceHost**.</span></span>  
  
```  
// wsh is an instance of WorkflowServiceHost class  
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();  
```  
  
 <span data-ttu-id="9d778-122">Lorsque le **WorkflowServiceHost** est ouvert, la persistance est automatiquement activée si le **DurableInstancingOptions.InstanceStore** n’est pas null.</span><span class="sxs-lookup"><span data-stu-id="9d778-122">When the **WorkflowServiceHost** is opened, persistence is automatically enabled if the **DurableInstancingOptions.InstanceStore** is not null.</span></span>  
  
 <span data-ttu-id="9d778-123">En règle générale, un comportement de service fournit le magasin d’instances concrètes à utiliser avec un hôte de service de flux de travail à l’aide de la **InstanceStore** propriété.</span><span class="sxs-lookup"><span data-stu-id="9d778-123">Typically, a service behavior provides the concrete instance store to be used with a workflow service host by using the **InstanceStore** property.</span></span> <span data-ttu-id="9d778-124">Par exemple, le SqlWorkflowInstanceStoreBehavior crée une instance de la **SqlWorkflowInstanceStore**, configure et l’assigne à la **DurableInstancingOptions.InstanceStore**.</span><span class="sxs-lookup"><span data-stu-id="9d778-124">For example, the SqlWorkflowInstanceStoreBehavior creates an instance of the **SqlWorkflowInstanceStore**, configures it, and assigns it to the **DurableInstancingOptions.InstanceStore**.</span></span>  
  
## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a><span data-ttu-id="9d778-125">Activation de la persistance pour les services de workflow à l'aide d'un fichier de configuration d'application</span><span class="sxs-lookup"><span data-stu-id="9d778-125">Enable Persistence for Workflow Services Using an Application Configuration File</span></span>  
 <span data-ttu-id="9d778-126">La persistance peut être activée à l'aide d'un fichier de configuration de l'application en ajoutant le code suivant à votre fichier app.config ou web.config :</span><span class="sxs-lookup"><span data-stu-id="9d778-126">Persistence can be enabled using an application configuration file by adding the following code to your app.config or web.config file:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="myBehavior">  
          <SqlWorkflowInstanceStore connectionString="Data Source=myDatatbaseServer;Initial Catalog=myPersistenceDatabase">  
        </behavior>  
      </serviceBehaviors>  
    <behaviors>  
  </system.serviceModel>  
</configuration>  
```
