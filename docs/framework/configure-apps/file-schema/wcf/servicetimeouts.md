---
title: '&lt;serviceTimeouts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0d8bfde535eb417614eee4ec6a2db7985152be33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicetimeoutsgt"></a><span data-ttu-id="e7343-102">&lt;serviceTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="e7343-102">&lt;serviceTimeouts&gt;</span></span>
<span data-ttu-id="e7343-103">Spécifie le délai d'attente pour un service.</span><span class="sxs-lookup"><span data-stu-id="e7343-103">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="e7343-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e7343-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e7343-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="e7343-105">\<behaviors></span></span>  
<span data-ttu-id="e7343-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="e7343-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="e7343-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="e7343-107">\<behavior></span></span>  
<span data-ttu-id="e7343-108">\<serviceTimeouts ></span><span class="sxs-lookup"><span data-stu-id="e7343-108">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7343-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7343-109">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />  
```  
  
## <a name="type"></a><span data-ttu-id="e7343-110">Type</span><span class="sxs-lookup"><span data-stu-id="e7343-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7343-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e7343-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e7343-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e7343-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7343-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="e7343-113">Attributes</span></span>  
  
|<span data-ttu-id="e7343-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="e7343-114">Attribute</span></span>|<span data-ttu-id="e7343-115">Description</span><span class="sxs-lookup"><span data-stu-id="e7343-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="e7343-116">Valeur <xref:System.TimeSpan> qui spécifie l'intervalle de temps pour le transfert d'une transaction du client au serveur.</span><span class="sxs-lookup"><span data-stu-id="e7343-116">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="e7343-117">La valeur par défaut est « 00 : 00:00 ».</span><span class="sxs-lookup"><span data-stu-id="e7343-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e7343-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e7343-118">Child Elements</span></span>  
 <span data-ttu-id="e7343-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e7343-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e7343-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e7343-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e7343-121">Élément</span><span class="sxs-lookup"><span data-stu-id="e7343-121">Element</span></span>|<span data-ttu-id="e7343-122">Description</span><span class="sxs-lookup"><span data-stu-id="e7343-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e7343-123">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="e7343-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="e7343-124">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="e7343-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7343-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7343-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
