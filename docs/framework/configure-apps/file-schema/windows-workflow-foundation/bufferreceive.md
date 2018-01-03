---
title: '&lt;bufferReceive&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5b5b6176e7c5b982bc9f41b13c669af104bf784f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltbufferreceivegt"></a><span data-ttu-id="5ea92-102">&lt;bufferReceive&gt;</span><span class="sxs-lookup"><span data-stu-id="5ea92-102">&lt;bufferReceive&gt;</span></span>
<span data-ttu-id="5ea92-103">Comportement de service qui permet à un service d'utiliser le traitement de la réception mise en mémoire tampon, ce qui permet à un service de flux de travail de traiter les messages dans le désordre.</span><span class="sxs-lookup"><span data-stu-id="5ea92-103">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="5ea92-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5ea92-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5ea92-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="5ea92-105">\<behaviors></span></span>  
<span data-ttu-id="5ea92-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5ea92-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="5ea92-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="5ea92-107">\<behavior></span></span>  
<span data-ttu-id="5ea92-108">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="5ea92-108">\<bufferReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ea92-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ea92-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ea92-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5ea92-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5ea92-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5ea92-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ea92-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="5ea92-112">Attributes</span></span>  
  
|<span data-ttu-id="5ea92-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="5ea92-113">Attribute</span></span>|<span data-ttu-id="5ea92-114">Description</span><span class="sxs-lookup"><span data-stu-id="5ea92-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5ea92-115">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="5ea92-115">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="5ea92-116">Entier qui spécifie le nombre maximal de messages en attente autorisé pour chaque canal.</span><span class="sxs-lookup"><span data-stu-id="5ea92-116">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="5ea92-117">La valeur par défaut est 512.</span><span class="sxs-lookup"><span data-stu-id="5ea92-117">The default value is 512.</span></span> <span data-ttu-id="5ea92-118">Cette propriété limite le nombre de messages non ordonnés qui peuvent être reçus par un service de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="5ea92-118">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ea92-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5ea92-119">Child Elements</span></span>  
 <span data-ttu-id="5ea92-120">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5ea92-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5ea92-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5ea92-121">Parent Elements</span></span>  
  
|<span data-ttu-id="5ea92-122">Élément</span><span class="sxs-lookup"><span data-stu-id="5ea92-122">Element</span></span>|<span data-ttu-id="5ea92-123">Description</span><span class="sxs-lookup"><span data-stu-id="5ea92-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ea92-124">\<comportement > de \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5ea92-124">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="5ea92-125">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="5ea92-125">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5ea92-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ea92-126">See Also</span></span>  
<!-- <xref:System.ServiceModel.Activities.Description.BufferReceiveServiceBehavior>  -->
 <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
