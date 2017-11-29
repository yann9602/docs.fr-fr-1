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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 40278c0a3d99dd5c37df1d642b8a2e13e9f62633
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltbehaviorsgt-of-workflow"></a><span data-ttu-id="2054f-102">&lt;behaviors&gt; de workflow</span><span class="sxs-lookup"><span data-stu-id="2054f-102">&lt;behaviors&gt; of workflow</span></span>
<span data-ttu-id="2054f-103">Cet élément contient le **serviceBehaviors** collection.</span><span class="sxs-lookup"><span data-stu-id="2054f-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="2054f-104">Chaque élément dans la collection définit des éléments de comportement consommés par des services de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="2054f-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="2054f-105">Chaque élément de comportement est identifié par son unique **nom** attribut.</span><span class="sxs-lookup"><span data-stu-id="2054f-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
 <span data-ttu-id="2054f-106">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="2054f-106">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2054f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2054f-107">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2054f-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2054f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2054f-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2054f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2054f-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="2054f-110">Attributes</span></span>  
 <span data-ttu-id="2054f-111">Aucun</span><span class="sxs-lookup"><span data-stu-id="2054f-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2054f-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2054f-112">Child Elements</span></span>  
  
|<span data-ttu-id="2054f-113">Élément</span><span class="sxs-lookup"><span data-stu-id="2054f-113">Element</span></span>|<span data-ttu-id="2054f-114">Description</span><span class="sxs-lookup"><span data-stu-id="2054f-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2054f-115">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="2054f-115">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|<span data-ttu-id="2054f-116">Cette section de configuration représente tous les comportements définis pour un service de flux de travail spécifique.</span><span class="sxs-lookup"><span data-stu-id="2054f-116">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2054f-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2054f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="2054f-118">Élément</span><span class="sxs-lookup"><span data-stu-id="2054f-118">Element</span></span>|<span data-ttu-id="2054f-119">Description</span><span class="sxs-lookup"><span data-stu-id="2054f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2054f-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2054f-120">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="2054f-121">Élément racine de tous les éléments de configuration de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="2054f-121">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2054f-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2054f-122">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BehaviorsSection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>  
 [<span data-ttu-id="2054f-123">Configuration et extension de l’exécution des comportements</span><span class="sxs-lookup"><span data-stu-id="2054f-123">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
