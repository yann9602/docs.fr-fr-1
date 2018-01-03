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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 71fc89a4b9735c13429b31d8cd7c5995f641afa8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcallbacktimeoutsgt"></a><span data-ttu-id="5477d-102">&lt;callbackTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="5477d-102">&lt;callbackTimeouts&gt;</span></span>
<span data-ttu-id="5477d-103">Spécifie la valeur du délai d’attente lors du transfert de transactions du serveur vers un client dans un scénario de contrat de rappel duplex.</span><span class="sxs-lookup"><span data-stu-id="5477d-103">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
 <span data-ttu-id="5477d-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5477d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5477d-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="5477d-105">\<behaviors></span></span>  
<span data-ttu-id="5477d-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5477d-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="5477d-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="5477d-107">\<behavior></span></span>  
<span data-ttu-id="5477d-108">\<callbackTimeOuts ></span><span class="sxs-lookup"><span data-stu-id="5477d-108">\<callbackTimeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5477d-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5477d-109">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />  
```  
  
## <a name="type"></a><span data-ttu-id="5477d-110">Type</span><span class="sxs-lookup"><span data-stu-id="5477d-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5477d-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5477d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5477d-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5477d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5477d-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="5477d-113">Attributes</span></span>  
  
|<span data-ttu-id="5477d-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="5477d-114">Attribute</span></span>|<span data-ttu-id="5477d-115">Description</span><span class="sxs-lookup"><span data-stu-id="5477d-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="5477d-116">Valeur <xref:System.TimeSpan> qui spécifie l'intervalle au cours duquel les transactions doivent être automatiquement effectuées ou arrêtées.</span><span class="sxs-lookup"><span data-stu-id="5477d-116">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="5477d-117">La valeur par défaut est « 00 : 00:00 ».</span><span class="sxs-lookup"><span data-stu-id="5477d-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5477d-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5477d-118">Child Elements</span></span>  
 <span data-ttu-id="5477d-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5477d-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5477d-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5477d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="5477d-121">Élément</span><span class="sxs-lookup"><span data-stu-id="5477d-121">Element</span></span>|<span data-ttu-id="5477d-122">Description</span><span class="sxs-lookup"><span data-stu-id="5477d-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5477d-123">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="5477d-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="5477d-124">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="5477d-124">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5477d-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5477d-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
