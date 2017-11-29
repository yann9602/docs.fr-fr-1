---
title: '&lt;workflowInstanceManagement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9883cedbbe3657eb82c25abbad66487e39ce2579
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltworkflowinstancemanagementgt"></a><span data-ttu-id="d4c1f-102">&lt;workflowInstanceManagement&gt;</span><span class="sxs-lookup"><span data-stu-id="d4c1f-102">&lt;workflowInstanceManagement&gt;</span></span>
<span data-ttu-id="d4c1f-103">Comportement de service qui vous permet de spécifier des paramètres qui contrôlent le mode d'exécution des instances de flux de travail, notamment la persistance, le comportement d'exception non prise en charge et le comportement inactif.</span><span class="sxs-lookup"><span data-stu-id="d4c1f-103">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="d4c1f-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d4c1f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d4c1f-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="d4c1f-105">\<behaviors></span></span>  
<span data-ttu-id="d4c1f-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="d4c1f-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="d4c1f-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="d4c1f-107">\<behavior></span></span>  
<span data-ttu-id="d4c1f-108">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="d4c1f-108">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4c1f-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4c1f-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4c1f-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d4c1f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d4c1f-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d4c1f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4c1f-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="d4c1f-112">Attributes</span></span>  
  
|<span data-ttu-id="d4c1f-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="d4c1f-113">Attribute</span></span>|<span data-ttu-id="d4c1f-114">Description</span><span class="sxs-lookup"><span data-stu-id="d4c1f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d4c1f-115">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="d4c1f-115">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="d4c1f-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d4c1f-116">Child Elements</span></span>  
 <span data-ttu-id="d4c1f-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d4c1f-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d4c1f-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d4c1f-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d4c1f-119">Élément</span><span class="sxs-lookup"><span data-stu-id="d4c1f-119">Element</span></span>|<span data-ttu-id="d4c1f-120">Description</span><span class="sxs-lookup"><span data-stu-id="d4c1f-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4c1f-121">\<comportement > de \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="d4c1f-121">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="d4c1f-122">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="d4c1f-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d4c1f-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4c1f-123">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
