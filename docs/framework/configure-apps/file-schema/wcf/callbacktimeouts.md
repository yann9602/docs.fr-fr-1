---
title: '&lt;callbackTimeouts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e86b69b7d633fd99728936070e94da964e16de58
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltcallbacktimeoutsgt"></a><span data-ttu-id="8ce8d-102">&lt;callbackTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="8ce8d-102">&lt;callbackTimeouts&gt;</span></span>
<span data-ttu-id="8ce8d-103">Spécifie la valeur du délai d’attente lors du transfert de transactions du serveur vers un client dans un scénario de contrat de rappel duplex.</span><span class="sxs-lookup"><span data-stu-id="8ce8d-103">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
 <span data-ttu-id="8ce8d-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="8ce8d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8ce8d-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="8ce8d-105">\<behaviors></span></span>  
<span data-ttu-id="8ce8d-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="8ce8d-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="8ce8d-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="8ce8d-107">\<behavior></span></span>  
<span data-ttu-id="8ce8d-108">\<callbackTimeOuts ></span><span class="sxs-lookup"><span data-stu-id="8ce8d-108">\<callbackTimeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ce8d-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ce8d-109">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />  
```  
  
## <a name="type"></a><span data-ttu-id="8ce8d-110">Type</span><span class="sxs-lookup"><span data-stu-id="8ce8d-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ce8d-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8ce8d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8ce8d-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8ce8d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ce8d-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="8ce8d-113">Attributes</span></span>  
  
|<span data-ttu-id="8ce8d-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="8ce8d-114">Attribute</span></span>|<span data-ttu-id="8ce8d-115">Description</span><span class="sxs-lookup"><span data-stu-id="8ce8d-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="8ce8d-116">Valeur <xref:System.TimeSpan> qui spécifie l'intervalle au cours duquel les transactions doivent être automatiquement effectuées ou arrêtées.</span><span class="sxs-lookup"><span data-stu-id="8ce8d-116">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="8ce8d-117">La valeur par défaut est « 00 : 00:00 ».</span><span class="sxs-lookup"><span data-stu-id="8ce8d-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8ce8d-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8ce8d-118">Child Elements</span></span>  
 <span data-ttu-id="8ce8d-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8ce8d-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8ce8d-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8ce8d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="8ce8d-121">Élément</span><span class="sxs-lookup"><span data-stu-id="8ce8d-121">Element</span></span>|<span data-ttu-id="8ce8d-122">Description</span><span class="sxs-lookup"><span data-stu-id="8ce8d-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8ce8d-123">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="8ce8d-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="8ce8d-124">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="8ce8d-124">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8ce8d-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ce8d-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
