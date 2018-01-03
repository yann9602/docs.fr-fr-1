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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63923121ae96b85bd192899a8d8ad285a3ad5b2d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsynchronousreceivegt-element"></a><span data-ttu-id="93a79-102">&lt;synchronousReceive&gt;, élément</span><span class="sxs-lookup"><span data-stu-id="93a79-102">&lt;synchronousReceive&gt; element</span></span>
<span data-ttu-id="93a79-103">Cet élément de configuration est utilisé en vue de spécifier le comportement de réception des messages au moment de l'exécution dans une application cliente ou de service.</span><span class="sxs-lookup"><span data-stu-id="93a79-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="93a79-104">Il n'a aucun attribut ou élément enfant.</span><span class="sxs-lookup"><span data-stu-id="93a79-104">It does not have any attributes or child elements.</span></span>  
  
 <span data-ttu-id="93a79-105">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="93a79-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="93a79-106">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="93a79-106">\<behaviors></span></span>  
<span data-ttu-id="93a79-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="93a79-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="93a79-108">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="93a79-108">\<behavior></span></span>  
<span data-ttu-id="93a79-109">\<synchronousReceive ></span><span class="sxs-lookup"><span data-stu-id="93a79-109">\<synchronousReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93a79-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93a79-110">Syntax</span></span>  
  
```xml  
<synchronousReceive />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93a79-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="93a79-111">Attributes and Elements</span></span>  
 <span data-ttu-id="93a79-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="93a79-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93a79-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="93a79-113">Attributes</span></span>  
 <span data-ttu-id="93a79-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="93a79-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="93a79-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="93a79-115">Child Elements</span></span>  
 <span data-ttu-id="93a79-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="93a79-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="93a79-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="93a79-117">Parent Elements</span></span>  
  
|<span data-ttu-id="93a79-118">Élément</span><span class="sxs-lookup"><span data-stu-id="93a79-118">Element</span></span>|<span data-ttu-id="93a79-119">Description</span><span class="sxs-lookup"><span data-stu-id="93a79-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="93a79-120">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="93a79-120">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="93a79-121">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="93a79-121">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93a79-122">Notes</span><span class="sxs-lookup"><span data-stu-id="93a79-122">Remarks</span></span>  
 <span data-ttu-id="93a79-123">Utilisez ce comportement pour indiquer à l’écouteur de canal d’utiliser une réception synchrone au lieu de celle par défaut (asynchrone).</span><span class="sxs-lookup"><span data-stu-id="93a79-123">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="93a79-124"> émet un nouveau thread pour pomper chaque canal accepté.</span><span class="sxs-lookup"><span data-stu-id="93a79-124"> issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="93a79-125">Si le nombre de canaux est important, il est possible de rencontrer une insuffisance de threads.</span><span class="sxs-lookup"><span data-stu-id="93a79-125">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93a79-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93a79-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>  
 <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
