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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1378ddd1550db614c9eddc44f79b19ff94ed585c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1010---activitycompleted"></a><span data-ttu-id="86509-102">1010 - ActivityCompleted</span><span class="sxs-lookup"><span data-stu-id="86509-102">1010 - ActivityCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="86509-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="86509-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="86509-104">ID</span><span class="sxs-lookup"><span data-stu-id="86509-104">ID</span></span>|<span data-ttu-id="86509-105">1010</span><span class="sxs-lookup"><span data-stu-id="86509-105">1010</span></span>|  
|<span data-ttu-id="86509-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="86509-106">Keywords</span></span>|<span data-ttu-id="86509-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="86509-107">WFRuntime</span></span>|  
|<span data-ttu-id="86509-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="86509-108">Level</span></span>|<span data-ttu-id="86509-109">Information</span><span class="sxs-lookup"><span data-stu-id="86509-109">Information</span></span>|  
|<span data-ttu-id="86509-110">Canal</span><span class="sxs-lookup"><span data-stu-id="86509-110">Channel</span></span>|<span data-ttu-id="86509-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="86509-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="86509-112">Description</span><span class="sxs-lookup"><span data-stu-id="86509-112">Description</span></span>  
 <span data-ttu-id="86509-113">Indique que l'exécution d'une activité est terminée.</span><span class="sxs-lookup"><span data-stu-id="86509-113">Indicates an activity has completed execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="86509-114">Message</span><span class="sxs-lookup"><span data-stu-id="86509-114">Message</span></span>  
 <span data-ttu-id="86509-115">L'activité « %1 », DisplayName : « %2 », InstanceId : « %3 » s'est terminée à l'état « %4 ».</span><span class="sxs-lookup"><span data-stu-id="86509-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has completed in the '%4' state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="86509-116">Détails</span><span class="sxs-lookup"><span data-stu-id="86509-116">Details</span></span>  
  
|<span data-ttu-id="86509-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="86509-117">Data Item Name</span></span>|<span data-ttu-id="86509-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="86509-118">Data Item Type</span></span>|<span data-ttu-id="86509-119">Description</span><span class="sxs-lookup"><span data-stu-id="86509-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="86509-120">Activité</span><span class="sxs-lookup"><span data-stu-id="86509-120">Activity</span></span>|<span data-ttu-id="86509-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="86509-121">xs:string</span></span>|<span data-ttu-id="86509-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="86509-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="86509-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="86509-123">DisplayName</span></span>|<span data-ttu-id="86509-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="86509-124">xs:string</span></span>|<span data-ttu-id="86509-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="86509-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="86509-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="86509-126">InstanceId</span></span>|<span data-ttu-id="86509-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="86509-127">xs:string</span></span>|<span data-ttu-id="86509-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="86509-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="86509-129">État</span><span class="sxs-lookup"><span data-stu-id="86509-129">State</span></span>|<span data-ttu-id="86509-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="86509-130">xs:string</span></span>|<span data-ttu-id="86509-131">État de l'activité.</span><span class="sxs-lookup"><span data-stu-id="86509-131">The state of the activity.</span></span>|  
|<span data-ttu-id="86509-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="86509-132">AppDomain</span></span>|<span data-ttu-id="86509-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="86509-133">xs:string</span></span>|<span data-ttu-id="86509-134">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="86509-134">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
