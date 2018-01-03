---
title: '&lt;behaviors&gt; de workflow'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83c1bf4beb244b72d2fe3d82d749ff6ae6723baf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltbehaviorsgt-of-workflow"></a><span data-ttu-id="3b84d-102">&lt;behaviors&gt; de workflow</span><span class="sxs-lookup"><span data-stu-id="3b84d-102">&lt;behaviors&gt; of workflow</span></span>
<span data-ttu-id="3b84d-103">Cet élément contient le **serviceBehaviors** collection.</span><span class="sxs-lookup"><span data-stu-id="3b84d-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="3b84d-104">Chaque élément dans la collection définit des éléments de comportement consommés par des services de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="3b84d-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="3b84d-105">Chaque élément de comportement est identifié par son unique **nom** attribut.</span><span class="sxs-lookup"><span data-stu-id="3b84d-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
 <span data-ttu-id="3b84d-106">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="3b84d-106">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b84d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b84d-107">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b84d-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3b84d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3b84d-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3b84d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3b84d-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="3b84d-110">Attributes</span></span>  
 <span data-ttu-id="3b84d-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3b84d-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3b84d-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3b84d-112">Child Elements</span></span>  
  
|<span data-ttu-id="3b84d-113">Élément</span><span class="sxs-lookup"><span data-stu-id="3b84d-113">Element</span></span>|<span data-ttu-id="3b84d-114">Description</span><span class="sxs-lookup"><span data-stu-id="3b84d-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3b84d-115">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="3b84d-115">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|<span data-ttu-id="3b84d-116">Cette section de configuration représente tous les comportements définis pour un service de flux de travail spécifique.</span><span class="sxs-lookup"><span data-stu-id="3b84d-116">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3b84d-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3b84d-117">Parent Elements</span></span>  
  
|<span data-ttu-id="3b84d-118">Élément</span><span class="sxs-lookup"><span data-stu-id="3b84d-118">Element</span></span>|<span data-ttu-id="3b84d-119">Description</span><span class="sxs-lookup"><span data-stu-id="3b84d-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3b84d-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3b84d-120">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="3b84d-121">Élément racine de tous les éléments de configuration de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="3b84d-121">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3b84d-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b84d-122">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BehaviorsSection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>  
 [<span data-ttu-id="3b84d-123">Configuration et extension de l’exécution à l’aide de comportements</span><span class="sxs-lookup"><span data-stu-id="3b84d-123">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
