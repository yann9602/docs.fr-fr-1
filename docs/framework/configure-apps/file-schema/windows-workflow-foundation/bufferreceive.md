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
ms.openlocfilehash: e0fc3fb901e0f70b616f403b98abc7b9645b2b44
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltbufferreceivegt"></a><span data-ttu-id="ff1f6-102">&lt;bufferReceive&gt;</span><span class="sxs-lookup"><span data-stu-id="ff1f6-102">&lt;bufferReceive&gt;</span></span>
<span data-ttu-id="ff1f6-103">Comportement de service qui permet à un service d'utiliser le traitement de la réception mise en mémoire tampon, ce qui permet à un service de flux de travail de traiter les messages dans le désordre.</span><span class="sxs-lookup"><span data-stu-id="ff1f6-103">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="ff1f6-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ff1f6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ff1f6-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="ff1f6-105">\<behaviors></span></span>  
<span data-ttu-id="ff1f6-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ff1f6-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="ff1f6-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="ff1f6-107">\<behavior></span></span>  
<span data-ttu-id="ff1f6-108">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="ff1f6-108">\<bufferReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff1f6-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff1f6-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff1f6-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ff1f6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ff1f6-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ff1f6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff1f6-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="ff1f6-112">Attributes</span></span>  
  
|<span data-ttu-id="ff1f6-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="ff1f6-113">Attribute</span></span>|<span data-ttu-id="ff1f6-114">Description</span><span class="sxs-lookup"><span data-stu-id="ff1f6-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ff1f6-115">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="ff1f6-115">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="ff1f6-116">Entier qui spécifie le nombre maximal de messages en attente autorisé pour chaque canal.</span><span class="sxs-lookup"><span data-stu-id="ff1f6-116">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="ff1f6-117">La valeur par défaut est 512.</span><span class="sxs-lookup"><span data-stu-id="ff1f6-117">The default value is 512.</span></span> <span data-ttu-id="ff1f6-118">Cette propriété limite le nombre de messages non ordonnés qui peuvent être reçus par un service de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="ff1f6-118">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff1f6-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ff1f6-119">Child Elements</span></span>  
 <span data-ttu-id="ff1f6-120">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ff1f6-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ff1f6-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ff1f6-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ff1f6-122">Élément</span><span class="sxs-lookup"><span data-stu-id="ff1f6-122">Element</span></span>|<span data-ttu-id="ff1f6-123">Description</span><span class="sxs-lookup"><span data-stu-id="ff1f6-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff1f6-124">\<comportement > de \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ff1f6-124">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="ff1f6-125">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="ff1f6-125">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ff1f6-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff1f6-126">See Also</span></span>  
<!-- <xref:System.ServiceModel.Activities.Description.BufferReceiveServiceBehavior>  -->
 <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
