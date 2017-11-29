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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 623ff924e171282c399bddcdc212a0606a3416d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltbufferreceivegt"></a><span data-ttu-id="4f7ab-102">&lt;bufferReceive&gt;</span><span class="sxs-lookup"><span data-stu-id="4f7ab-102">&lt;bufferReceive&gt;</span></span>
<span data-ttu-id="4f7ab-103">Comportement de service qui permet à un service d'utiliser le traitement de la réception mise en mémoire tampon, ce qui permet à un service de flux de travail de traiter les messages dans le désordre.</span><span class="sxs-lookup"><span data-stu-id="4f7ab-103">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="4f7ab-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="4f7ab-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4f7ab-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="4f7ab-105">\<behaviors></span></span>  
<span data-ttu-id="4f7ab-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="4f7ab-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="4f7ab-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="4f7ab-107">\<behavior></span></span>  
<span data-ttu-id="4f7ab-108">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="4f7ab-108">\<bufferReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f7ab-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f7ab-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f7ab-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4f7ab-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4f7ab-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4f7ab-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f7ab-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="4f7ab-112">Attributes</span></span>  
  
|<span data-ttu-id="4f7ab-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="4f7ab-113">Attribute</span></span>|<span data-ttu-id="4f7ab-114">Description</span><span class="sxs-lookup"><span data-stu-id="4f7ab-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4f7ab-115">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="4f7ab-115">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="4f7ab-116">Entier qui spécifie le nombre maximal de messages en attente autorisé pour chaque canal.</span><span class="sxs-lookup"><span data-stu-id="4f7ab-116">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="4f7ab-117">La valeur par défaut est 512.</span><span class="sxs-lookup"><span data-stu-id="4f7ab-117">The default value is 512.</span></span> <span data-ttu-id="4f7ab-118">Cette propriété limite le nombre de messages non ordonnés qui peuvent être reçus par un service de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="4f7ab-118">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4f7ab-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4f7ab-119">Child Elements</span></span>  
 <span data-ttu-id="4f7ab-120">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4f7ab-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4f7ab-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4f7ab-121">Parent Elements</span></span>  
  
|<span data-ttu-id="4f7ab-122">Élément</span><span class="sxs-lookup"><span data-stu-id="4f7ab-122">Element</span></span>|<span data-ttu-id="4f7ab-123">Description</span><span class="sxs-lookup"><span data-stu-id="4f7ab-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f7ab-124">\<comportement > de \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="4f7ab-124">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="4f7ab-125">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="4f7ab-125">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4f7ab-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f7ab-126">See Also</span></span>  
<!-- <xref:System.ServiceModel.Activities.Description.BufferReceiveServiceBehavior>  -->
 <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
