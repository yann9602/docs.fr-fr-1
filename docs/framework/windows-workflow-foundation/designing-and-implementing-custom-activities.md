---
title: "Conception et implémentation d'activités personnalisées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e30e63d-6e33-4842-a7a4-ce807cef1fad
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 944f8d7c015d2522ae4fb8f0805ca6a40d494a75
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="designing-and-implementing-custom-activities"></a><span data-ttu-id="9761a-102">Conception et implémentation d'activités personnalisées</span><span class="sxs-lookup"><span data-stu-id="9761a-102">Designing and Implementing Custom Activities</span></span>
<span data-ttu-id="9761a-103">Dans [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)], les activités personnalisées sont créées soit en assemblant des activités fournies par le système dans des activités composites, soit en créant de nouveaux types qui dérivent des objets <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, ou <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="9761a-103">Custom activities in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] are created by either assembling system-provided activities into composite activities or by creating new types that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, or <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="9761a-104">Cette section décrit la procédure de création des activités personnalisées avec l'une ou l'autre de ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="9761a-104">This section describes how to create custom activities with either method.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9761a-105">Les activités personnalisées s'affichent par défaut dans le concepteur de workflow comme un rectangle simple avec le nom d'activité.</span><span class="sxs-lookup"><span data-stu-id="9761a-105">Custom activities by default display within the workflow designer as a simple rectangle with the activity’s name.</span></span> <span data-ttu-id="9761a-106">Pour fournir une représentation visuelle personnalisée de votre activité dans le concepteur de workflow, vous devez également créer un concepteur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="9761a-106">To provide a custom visual representation of your activity in the workflow designer you must also create a custom designer.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="9761a-107">[à l’aide des concepteurs d’activités personnalisées et les modèles](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md).</span><span class="sxs-lookup"><span data-stu-id="9761a-107"> [Using Custom Activity Designers and Templates](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9761a-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9761a-108">In This Section</span></span>  
 [<span data-ttu-id="9761a-109">Options de création d’activités</span><span class="sxs-lookup"><span data-stu-id="9761a-109">Activity Authoring Options</span></span>](../../../docs/framework/windows-workflow-foundation/activity-authoring-options-in-wf.md)  
 <span data-ttu-id="9761a-110">Traite des styles de création disponibles dans [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9761a-110">Discusses the authoring styles available in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="9761a-111">Utilisation d’une activité personnalisée</span><span class="sxs-lookup"><span data-stu-id="9761a-111">Using a custom activity</span></span>](../../../docs/framework/windows-workflow-foundation/using-a-custom-activity.md)  
 <span data-ttu-id="9761a-112">Décrit comment ajouter une activité personnalisée à un projet de workflow.</span><span class="sxs-lookup"><span data-stu-id="9761a-112">Describes how to add a custom activity to a workflow project.</span></span>  
  
  [<span data-ttu-id="9761a-113">Création d’activités asynchrones</span><span class="sxs-lookup"><span data-stu-id="9761a-113">Creating Asynchronous Activities</span></span>](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md)  
 <span data-ttu-id="9761a-114">Décrit comment créer des activités asynchrones.</span><span class="sxs-lookup"><span data-stu-id="9761a-114">Describes how to create asynchronous activities.</span></span>  
  
 [<span data-ttu-id="9761a-115">Configuration de la validation d’activité</span><span class="sxs-lookup"><span data-stu-id="9761a-115">Configuring Activity Validation</span></span>](../../../docs/framework/windows-workflow-foundation/configuring-activity-validation.md)  
 <span data-ttu-id="9761a-116">Décrit comment utiliser la validation d’activité pour identifier et signaler des erreurs dans la configuration d’une activité, avant son exécution.</span><span class="sxs-lookup"><span data-stu-id="9761a-116">Describes how activity validation can be used to identify and report errors in an activity’s configuration prior to its execution.</span></span>  
  
 [<span data-ttu-id="9761a-117">Création d’une activité en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="9761a-117">Creating an Activity at Runtime</span></span>](../../../docs/framework/windows-workflow-foundation/creating-an-activity-at-runtime-with-dynamicactivity.md)  
 <span data-ttu-id="9761a-118">Explique comment créer des activités au moment de l'exécution en utilisant <xref:System.Activities.DynamicActivity>.</span><span class="sxs-lookup"><span data-stu-id="9761a-118">Discusses how to create activities at runtime using <xref:System.Activities.DynamicActivity>.</span></span>  
  
 [<span data-ttu-id="9761a-119">Propriétés d’exécution de workflow</span><span class="sxs-lookup"><span data-stu-id="9761a-119">Workflow Execution Properties</span></span>](../../../docs/framework/windows-workflow-foundation/workflow-execution-properties.md)  
 <span data-ttu-id="9761a-120">Décrit comment utiliser les propriétés d'exécution de workflow pour ajouter des propriétés spécifiques au contexte à l'environnement d'une activité.</span><span class="sxs-lookup"><span data-stu-id="9761a-120">Describes how to use workflow execution properties to add context specific properties to an activity’s environment</span></span>  
  
 [<span data-ttu-id="9761a-121">Utilisation de délégués d’activité</span><span class="sxs-lookup"><span data-stu-id="9761a-121">Using Activity Delegates</span></span>](../../../docs/framework/windows-workflow-foundation/using-activity-delegates.md)  
 <span data-ttu-id="9761a-122">Explique comment créer et utiliser des activités qui contiennent des délégués d'activité.</span><span class="sxs-lookup"><span data-stu-id="9761a-122">Discusses how to author and use activities that contain activity delegates.</span></span>  
  
 [<span data-ttu-id="9761a-123">Localisation d’activité</span><span class="sxs-lookup"><span data-stu-id="9761a-123">Activity Localization</span></span>](../../../docs/framework/windows-workflow-foundation/activity-localization.md)  
 <span data-ttu-id="9761a-124">Décrit comment utiliser la localisation des ressources de type chaîne dans les activités.</span><span class="sxs-lookup"><span data-stu-id="9761a-124">Describes how to use localization of string resources in activities.</span></span>  
  
 [<span data-ttu-id="9761a-125">Utilisation d’extensions d’activité</span><span class="sxs-lookup"><span data-stu-id="9761a-125">Using Activity Extensions</span></span>](../../../docs/framework/windows-workflow-foundation/using-activity-extensions.md)  
 <span data-ttu-id="9761a-126">Décrit comment créer et utiliser des extensions d’activité.</span><span class="sxs-lookup"><span data-stu-id="9761a-126">Describes how to author and use activity extensions.</span></span>  
  
 [<span data-ttu-id="9761a-127">Consommation de flux OData à partir d’un workflow</span><span class="sxs-lookup"><span data-stu-id="9761a-127">Consuming OData Feeds from a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/consuming-odata-feeds-from-a-workflow.md)  
 <span data-ttu-id="9761a-128">Décrit plusieurs méthodes pour appeler un service de données WCF à partir d'un workflow.</span><span class="sxs-lookup"><span data-stu-id="9761a-128">Describes several methods for calling a WCF Data Service from a workflow.</span></span>  
  
 [<span data-ttu-id="9761a-129">Portée et visibilité de la définition de l’activité</span><span class="sxs-lookup"><span data-stu-id="9761a-129">Activity Definition Scoping and Visibility</span></span>](../../../docs/framework/windows-workflow-foundation/activity-definition-scoping-and-visibility.md)  
 <span data-ttu-id="9761a-130">Décrit les options et les règles pour définir la portée des données et la visibilité des membres pour les activités.</span><span class="sxs-lookup"><span data-stu-id="9761a-130">Describes the options and rules for defining data scoping and member visibility for activities.</span></span>
