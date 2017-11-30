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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ecefda0a3447aa029079fbb3633b05054f42195a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltservicetimeoutsgt"></a><span data-ttu-id="f1699-102">&lt;serviceTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="f1699-102">&lt;serviceTimeouts&gt;</span></span>
<span data-ttu-id="f1699-103">Spécifie le délai d'attente pour un service.</span><span class="sxs-lookup"><span data-stu-id="f1699-103">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="f1699-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f1699-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f1699-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="f1699-105">\<behaviors></span></span>  
<span data-ttu-id="f1699-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="f1699-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="f1699-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="f1699-107">\<behavior></span></span>  
<span data-ttu-id="f1699-108">\<serviceTimeouts ></span><span class="sxs-lookup"><span data-stu-id="f1699-108">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1699-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1699-109">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />  
```  
  
## <a name="type"></a><span data-ttu-id="f1699-110">Type</span><span class="sxs-lookup"><span data-stu-id="f1699-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1699-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f1699-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f1699-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f1699-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1699-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="f1699-113">Attributes</span></span>  
  
|<span data-ttu-id="f1699-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="f1699-114">Attribute</span></span>|<span data-ttu-id="f1699-115">Description</span><span class="sxs-lookup"><span data-stu-id="f1699-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="f1699-116">Valeur <xref:System.TimeSpan> qui spécifie l'intervalle de temps pour le transfert d'une transaction du client au serveur.</span><span class="sxs-lookup"><span data-stu-id="f1699-116">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="f1699-117">La valeur par défaut est « 00 : 00:00 ».</span><span class="sxs-lookup"><span data-stu-id="f1699-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f1699-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f1699-118">Child Elements</span></span>  
 <span data-ttu-id="f1699-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f1699-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f1699-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f1699-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f1699-121">Élément</span><span class="sxs-lookup"><span data-stu-id="f1699-121">Element</span></span>|<span data-ttu-id="f1699-122">Description</span><span class="sxs-lookup"><span data-stu-id="f1699-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1699-123">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="f1699-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="f1699-124">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="f1699-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f1699-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1699-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
