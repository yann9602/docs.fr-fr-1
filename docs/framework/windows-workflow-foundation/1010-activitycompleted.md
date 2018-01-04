---
title: 1010 - ActivityCompleted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d256284e-3fd2-4c33-82f4-abb617575706
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d11bbe013c6f3370064dd8cd9f4f03a0234d6f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="1010---activitycompleted"></a><span data-ttu-id="bc89f-102">1010 - ActivityCompleted</span><span class="sxs-lookup"><span data-stu-id="bc89f-102">1010 - ActivityCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="bc89f-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="bc89f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bc89f-104">ID</span><span class="sxs-lookup"><span data-stu-id="bc89f-104">ID</span></span>|<span data-ttu-id="bc89f-105">1010</span><span class="sxs-lookup"><span data-stu-id="bc89f-105">1010</span></span>|  
|<span data-ttu-id="bc89f-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="bc89f-106">Keywords</span></span>|<span data-ttu-id="bc89f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="bc89f-107">WFRuntime</span></span>|  
|<span data-ttu-id="bc89f-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="bc89f-108">Level</span></span>|<span data-ttu-id="bc89f-109">Information</span><span class="sxs-lookup"><span data-stu-id="bc89f-109">Information</span></span>|  
|<span data-ttu-id="bc89f-110">Canal</span><span class="sxs-lookup"><span data-stu-id="bc89f-110">Channel</span></span>|<span data-ttu-id="bc89f-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="bc89f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bc89f-112">Description</span><span class="sxs-lookup"><span data-stu-id="bc89f-112">Description</span></span>  
 <span data-ttu-id="bc89f-113">Indique que l'exécution d'une activité est terminée.</span><span class="sxs-lookup"><span data-stu-id="bc89f-113">Indicates an activity has completed execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bc89f-114">Message</span><span class="sxs-lookup"><span data-stu-id="bc89f-114">Message</span></span>  
 <span data-ttu-id="bc89f-115">L'activité « %1 », DisplayName : « %2 », InstanceId : « %3 » s'est terminée à l'état « %4 ».</span><span class="sxs-lookup"><span data-stu-id="bc89f-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has completed in the '%4' state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bc89f-116">Détails</span><span class="sxs-lookup"><span data-stu-id="bc89f-116">Details</span></span>  
  
|<span data-ttu-id="bc89f-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="bc89f-117">Data Item Name</span></span>|<span data-ttu-id="bc89f-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="bc89f-118">Data Item Type</span></span>|<span data-ttu-id="bc89f-119">Description</span><span class="sxs-lookup"><span data-stu-id="bc89f-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bc89f-120">Activité</span><span class="sxs-lookup"><span data-stu-id="bc89f-120">Activity</span></span>|<span data-ttu-id="bc89f-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="bc89f-121">xs:string</span></span>|<span data-ttu-id="bc89f-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="bc89f-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="bc89f-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="bc89f-123">DisplayName</span></span>|<span data-ttu-id="bc89f-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="bc89f-124">xs:string</span></span>|<span data-ttu-id="bc89f-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="bc89f-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="bc89f-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="bc89f-126">InstanceId</span></span>|<span data-ttu-id="bc89f-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="bc89f-127">xs:string</span></span>|<span data-ttu-id="bc89f-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="bc89f-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="bc89f-129">État</span><span class="sxs-lookup"><span data-stu-id="bc89f-129">State</span></span>|<span data-ttu-id="bc89f-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="bc89f-130">xs:string</span></span>|<span data-ttu-id="bc89f-131">État de l'activité.</span><span class="sxs-lookup"><span data-stu-id="bc89f-131">The state of the activity.</span></span>|  
|<span data-ttu-id="bc89f-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="bc89f-132">AppDomain</span></span>|<span data-ttu-id="bc89f-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="bc89f-133">xs:string</span></span>|<span data-ttu-id="bc89f-134">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="bc89f-134">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
