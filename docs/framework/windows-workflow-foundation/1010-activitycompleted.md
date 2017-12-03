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
ms.openlocfilehash: d26aa2c30defd2eb794d013155e05ccd496eebe6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="1010---activitycompleted"></a><span data-ttu-id="7106e-102">1010 - ActivityCompleted</span><span class="sxs-lookup"><span data-stu-id="7106e-102">1010 - ActivityCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="7106e-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="7106e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7106e-104">ID</span><span class="sxs-lookup"><span data-stu-id="7106e-104">ID</span></span>|<span data-ttu-id="7106e-105">1010</span><span class="sxs-lookup"><span data-stu-id="7106e-105">1010</span></span>|  
|<span data-ttu-id="7106e-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="7106e-106">Keywords</span></span>|<span data-ttu-id="7106e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="7106e-107">WFRuntime</span></span>|  
|<span data-ttu-id="7106e-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="7106e-108">Level</span></span>|<span data-ttu-id="7106e-109">Information</span><span class="sxs-lookup"><span data-stu-id="7106e-109">Information</span></span>|  
|<span data-ttu-id="7106e-110">Canal</span><span class="sxs-lookup"><span data-stu-id="7106e-110">Channel</span></span>|<span data-ttu-id="7106e-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="7106e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7106e-112">Description</span><span class="sxs-lookup"><span data-stu-id="7106e-112">Description</span></span>  
 <span data-ttu-id="7106e-113">Indique que l'exécution d'une activité est terminée.</span><span class="sxs-lookup"><span data-stu-id="7106e-113">Indicates an activity has completed execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7106e-114">Message</span><span class="sxs-lookup"><span data-stu-id="7106e-114">Message</span></span>  
 <span data-ttu-id="7106e-115">L'activité « %1 », DisplayName : « %2 », InstanceId : « %3 » s'est terminée à l'état « %4 ».</span><span class="sxs-lookup"><span data-stu-id="7106e-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has completed in the '%4' state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7106e-116">Détails</span><span class="sxs-lookup"><span data-stu-id="7106e-116">Details</span></span>  
  
|<span data-ttu-id="7106e-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="7106e-117">Data Item Name</span></span>|<span data-ttu-id="7106e-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="7106e-118">Data Item Type</span></span>|<span data-ttu-id="7106e-119">Description</span><span class="sxs-lookup"><span data-stu-id="7106e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7106e-120">Activité</span><span class="sxs-lookup"><span data-stu-id="7106e-120">Activity</span></span>|<span data-ttu-id="7106e-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="7106e-121">xs:string</span></span>|<span data-ttu-id="7106e-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="7106e-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="7106e-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="7106e-123">DisplayName</span></span>|<span data-ttu-id="7106e-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="7106e-124">xs:string</span></span>|<span data-ttu-id="7106e-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="7106e-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="7106e-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="7106e-126">InstanceId</span></span>|<span data-ttu-id="7106e-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="7106e-127">xs:string</span></span>|<span data-ttu-id="7106e-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="7106e-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="7106e-129">État</span><span class="sxs-lookup"><span data-stu-id="7106e-129">State</span></span>|<span data-ttu-id="7106e-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="7106e-130">xs:string</span></span>|<span data-ttu-id="7106e-131">État de l'activité.</span><span class="sxs-lookup"><span data-stu-id="7106e-131">The state of the activity.</span></span>|  
|<span data-ttu-id="7106e-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7106e-132">AppDomain</span></span>|<span data-ttu-id="7106e-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="7106e-133">xs:string</span></span>|<span data-ttu-id="7106e-134">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="7106e-134">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
