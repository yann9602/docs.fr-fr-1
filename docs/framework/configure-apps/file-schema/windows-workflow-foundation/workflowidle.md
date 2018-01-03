---
title: '&lt;workflowIdle&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2440f322ea7dbd3a6d6f9d56878273c49b26bfa6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltworkflowidlegt"></a><span data-ttu-id="28b8a-102">&lt;workflowIdle&gt;</span><span class="sxs-lookup"><span data-stu-id="28b8a-102">&lt;workflowIdle&gt;</span></span>
<span data-ttu-id="28b8a-103">Comportement de service qui contrôle à quel moment les instances de workflow inactives sont déchargées et rendues persistantes.</span><span class="sxs-lookup"><span data-stu-id="28b8a-103">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
<span data-ttu-id="28b8a-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="28b8a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="28b8a-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="28b8a-105">\<behaviors></span></span>  
<span data-ttu-id="28b8a-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="28b8a-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="28b8a-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="28b8a-107">\<behavior></span></span>  
<span data-ttu-id="28b8a-108">\<workflowIdle ></span><span class="sxs-lookup"><span data-stu-id="28b8a-108">\<workflowIdle></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28b8a-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28b8a-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowIdle timeToPersist="TimeSpan" 
                    timeToUnload="TimeSpan" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28b8a-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="28b8a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="28b8a-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="28b8a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28b8a-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="28b8a-112">Attributes</span></span>  
  
|<span data-ttu-id="28b8a-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="28b8a-113">Attribute</span></span>|<span data-ttu-id="28b8a-114">Description</span><span class="sxs-lookup"><span data-stu-id="28b8a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="28b8a-115">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="28b8a-115">timeToPersist</span></span>|<span data-ttu-id="28b8a-116">Une valeur Timespan qui spécifie la durée entre le moment où le flux de travail devienne inactif et est rendue persistante.</span><span class="sxs-lookup"><span data-stu-id="28b8a-116">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="28b8a-117">La valeur par défaut a la valeur TimeSpan.MaxValue.</span><span class="sxs-lookup"><span data-stu-id="28b8a-117">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="28b8a-118">La durée commence à s'écouler lorsque l'instance de flux de travail devient inactive.</span><span class="sxs-lookup"><span data-stu-id="28b8a-118">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="28b8a-119">Cet attribut est utile si vous souhaitez conserver une instance de flux de travail plus efficacement tout en conservant l’instance en mémoire aussi longtemps que possible.</span><span class="sxs-lookup"><span data-stu-id="28b8a-119">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="28b8a-120">Cet attribut est valide uniquement si sa valeur est inférieure à la **timeToUnload** attribut.</span><span class="sxs-lookup"><span data-stu-id="28b8a-120">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="28b8a-121">Si elle est supérieure, elle est ignorée.</span><span class="sxs-lookup"><span data-stu-id="28b8a-121">If it is greater, it is ignored.</span></span> <span data-ttu-id="28b8a-122">Si cet attribut est écoulé avant que la valeur spécifiée par la **timeToUnload** attribut, persistance doit s’effectuer avant que le workflow est déchargé.</span><span class="sxs-lookup"><span data-stu-id="28b8a-122">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="28b8a-123">Cela implique un éventuel retard de l'opération de déchargement tant que le flux de travail n'a pas été rendu persistant.</span><span class="sxs-lookup"><span data-stu-id="28b8a-123">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="28b8a-124">La couche de persistance est responsable de la gestion de toutes les tentatives pour les erreurs temporaires et lève uniquement des exceptions sur les erreurs non récupérables.</span><span class="sxs-lookup"><span data-stu-id="28b8a-124">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="28b8a-125">Par conséquent, toutes les exceptions levées pendant la persistance sont traitées comme fatales et l'instance de flux de travail est abandonnée.</span><span class="sxs-lookup"><span data-stu-id="28b8a-125">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="28b8a-126">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="28b8a-126">timeToUnload</span></span>|<span data-ttu-id="28b8a-127">Valeur Timespan qui spécifie la durée entre l'inactivation et le déchargement du flux de travail.</span><span class="sxs-lookup"><span data-stu-id="28b8a-127">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="28b8a-128">La valeur par défaut est égale à 1 minute.</span><span class="sxs-lookup"><span data-stu-id="28b8a-128">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="28b8a-129">Le déchargement d'un flux de travail implique qu'il soit également rendu persistant.</span><span class="sxs-lookup"><span data-stu-id="28b8a-129">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="28b8a-130">Si cet attribut est défini à zéro l’instance de workflow est persistant et déchargée immédiatement après le workflow devient inactif.</span><span class="sxs-lookup"><span data-stu-id="28b8a-130">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="28b8a-131">Cet attribut TimeSpan.MaxValue efficacement désactive l’opération de déchargement.</span><span class="sxs-lookup"><span data-stu-id="28b8a-131">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="28b8a-132">Les instances de flux de travail inactives ne sont jamais déchargées.</span><span class="sxs-lookup"><span data-stu-id="28b8a-132">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="28b8a-133">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="28b8a-133">Child Elements</span></span>  
 <span data-ttu-id="28b8a-134">Aucun.</span><span class="sxs-lookup"><span data-stu-id="28b8a-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="28b8a-135">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="28b8a-135">Parent Elements</span></span>  
  
|<span data-ttu-id="28b8a-136">Élément</span><span class="sxs-lookup"><span data-stu-id="28b8a-136">Element</span></span>|<span data-ttu-id="28b8a-137">Description</span><span class="sxs-lookup"><span data-stu-id="28b8a-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28b8a-138">\<comportement > de \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="28b8a-138">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="28b8a-139">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="28b8a-139">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="28b8a-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28b8a-140">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
