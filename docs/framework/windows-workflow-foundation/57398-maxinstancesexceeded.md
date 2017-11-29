---
title: 57398 - MaxInstancesExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7417d2e0e850017e65910be32e7449255f0761c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="57398---maxinstancesexceeded"></a><span data-ttu-id="68979-102">57398 - MaxInstancesExceeded</span><span class="sxs-lookup"><span data-stu-id="68979-102">57398 - MaxInstancesExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="68979-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="68979-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="68979-104">ID</span><span class="sxs-lookup"><span data-stu-id="68979-104">ID</span></span>|<span data-ttu-id="68979-105">57398</span><span class="sxs-lookup"><span data-stu-id="68979-105">57398</span></span>|  
|<span data-ttu-id="68979-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="68979-106">Keywords</span></span>|<span data-ttu-id="68979-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="68979-107">WFServices</span></span>|  
|<span data-ttu-id="68979-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="68979-108">Level</span></span>|<span data-ttu-id="68979-109">Avertissement</span><span class="sxs-lookup"><span data-stu-id="68979-109">Warning</span></span>|  
|<span data-ttu-id="68979-110">Canal</span><span class="sxs-lookup"><span data-stu-id="68979-110">Channel</span></span>|<span data-ttu-id="68979-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="68979-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="68979-112">Description</span><span class="sxs-lookup"><span data-stu-id="68979-112">Description</span></span>  
 <span data-ttu-id="68979-113">Indique que le système a atteint la limite définie pour la limitation des « MaxConcurrentInstances ».</span><span class="sxs-lookup"><span data-stu-id="68979-113">Indicates the system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span>  
  
## <a name="message"></a><span data-ttu-id="68979-114">Message</span><span class="sxs-lookup"><span data-stu-id="68979-114">Message</span></span>  
 <span data-ttu-id="68979-115">Le système a atteint la limite définie pour la limitation des 'MaxConcurrentInstances'.</span><span class="sxs-lookup"><span data-stu-id="68979-115">The system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span> <span data-ttu-id="68979-116">La limite a été définie sur %1.</span><span class="sxs-lookup"><span data-stu-id="68979-116">Limit for this throttle was set to %1.</span></span> <span data-ttu-id="68979-117">La valeur de limitation peut être modifiée en modifiant l'attribut « maxConcurrentInstances » de l'élément serviceThrottle ou en modifiant la propriété « MaxConcurrentInstances » à l'aide du comportement ServiceThrottlingBehavior.</span><span class="sxs-lookup"><span data-stu-id="68979-117">Throttle value can be changed by modifying attribute 'maxConcurrentInstances' in serviceThrottle element or by modifying 'MaxConcurrentInstances' property on behavior ServiceThrottlingBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="68979-118">Détails</span><span class="sxs-lookup"><span data-stu-id="68979-118">Details</span></span>  
  
|<span data-ttu-id="68979-119">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="68979-119">Data Item Name</span></span>|<span data-ttu-id="68979-120">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="68979-120">Data Item Type</span></span>|<span data-ttu-id="68979-121">Description</span><span class="sxs-lookup"><span data-stu-id="68979-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="68979-122">Nom</span><span class="sxs-lookup"><span data-stu-id="68979-122">Name</span></span>|<span data-ttu-id="68979-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="68979-123">xs:string</span></span>|<span data-ttu-id="68979-124">Nom de l'élément.</span><span class="sxs-lookup"><span data-stu-id="68979-124">The name of the item.</span></span>|  
|<span data-ttu-id="68979-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="68979-125">AppDomain</span></span>|<span data-ttu-id="68979-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="68979-126">xs:string</span></span>|<span data-ttu-id="68979-127">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="68979-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
