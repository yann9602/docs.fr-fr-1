---
title: "&lt;synchronousReceive&gt;, élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b630f5ad2fbf5e3f20667e0bd1b7ae711992dc18
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsynchronousreceivegt-element"></a><span data-ttu-id="6235d-102">&lt;synchronousReceive&gt;, élément</span><span class="sxs-lookup"><span data-stu-id="6235d-102">&lt;synchronousReceive&gt; element</span></span>
<span data-ttu-id="6235d-103">Cet élément de configuration est utilisé en vue de spécifier le comportement de réception des messages au moment de l'exécution dans une application cliente ou de service.</span><span class="sxs-lookup"><span data-stu-id="6235d-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="6235d-104">Il n'a aucun attribut ou élément enfant.</span><span class="sxs-lookup"><span data-stu-id="6235d-104">It does not have any attributes or child elements.</span></span>  
  
 <span data-ttu-id="6235d-105">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="6235d-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="6235d-106">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="6235d-106">\<behaviors></span></span>  
<span data-ttu-id="6235d-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="6235d-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="6235d-108">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="6235d-108">\<behavior></span></span>  
<span data-ttu-id="6235d-109">\<synchronousReceive ></span><span class="sxs-lookup"><span data-stu-id="6235d-109">\<synchronousReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6235d-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6235d-110">Syntax</span></span>  
  
```xml  
<synchronousReceive />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6235d-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6235d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6235d-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6235d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6235d-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="6235d-113">Attributes</span></span>  
 <span data-ttu-id="6235d-114">Aucun</span><span class="sxs-lookup"><span data-stu-id="6235d-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6235d-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6235d-115">Child Elements</span></span>  
 <span data-ttu-id="6235d-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6235d-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6235d-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6235d-117">Parent Elements</span></span>  
  
|<span data-ttu-id="6235d-118">Élément</span><span class="sxs-lookup"><span data-stu-id="6235d-118">Element</span></span>|<span data-ttu-id="6235d-119">Description</span><span class="sxs-lookup"><span data-stu-id="6235d-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6235d-120">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="6235d-120">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="6235d-121">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="6235d-121">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6235d-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="6235d-122">Remarks</span></span>  
 <span data-ttu-id="6235d-123">Utilisez ce comportement pour indiquer à l’écouteur de canal d’utiliser une réception synchrone au lieu de celle par défaut (asynchrone).</span><span class="sxs-lookup"><span data-stu-id="6235d-123">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="6235d-124"> émet un nouveau thread pour pomper chaque canal accepté.</span><span class="sxs-lookup"><span data-stu-id="6235d-124"> issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="6235d-125">Si le nombre de canaux est important, il est possible de rencontrer une insuffisance de threads.</span><span class="sxs-lookup"><span data-stu-id="6235d-125">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6235d-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6235d-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>  
 <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
