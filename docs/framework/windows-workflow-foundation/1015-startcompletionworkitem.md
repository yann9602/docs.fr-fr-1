---
title: 1015 - StartCompletionWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bc317157ed7658a52aa60c9b74942f9e84d47257
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="1015---startcompletionworkitem"></a><span data-ttu-id="9c722-102">1015 - StartCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="9c722-102">1015 - StartCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="9c722-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="9c722-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9c722-104">ID</span><span class="sxs-lookup"><span data-stu-id="9c722-104">ID</span></span>|<span data-ttu-id="9c722-105">1015</span><span class="sxs-lookup"><span data-stu-id="9c722-105">1015</span></span>|  
|<span data-ttu-id="9c722-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="9c722-106">Keywords</span></span>|<span data-ttu-id="9c722-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9c722-107">WFRuntime</span></span>|  
|<span data-ttu-id="9c722-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="9c722-108">Level</span></span>|<span data-ttu-id="9c722-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="9c722-109">Verbose</span></span>|  
|<span data-ttu-id="9c722-110">Canal</span><span class="sxs-lookup"><span data-stu-id="9c722-110">Channel</span></span>|<span data-ttu-id="9c722-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="9c722-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9c722-112">Description</span><span class="sxs-lookup"><span data-stu-id="9c722-112">Description</span></span>  
 <span data-ttu-id="9c722-113">Indique qu'un CompletionWorkItem démarre l'exécution.</span><span class="sxs-lookup"><span data-stu-id="9c722-113">Indicates a CompletionWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9c722-114">Message</span><span class="sxs-lookup"><span data-stu-id="9c722-114">Message</span></span>  
 <span data-ttu-id="9c722-115">Début de l'exécution d'un CompletionWorkItem pour l'activité parente « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="9c722-115">Starting execution of a CompletionWorkItem for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="9c722-116">Activité terminée « %4 », DisplayName : « %5 », InstanceId : « %6 ».</span><span class="sxs-lookup"><span data-stu-id="9c722-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9c722-117">Détails</span><span class="sxs-lookup"><span data-stu-id="9c722-117">Details</span></span>  
  
|<span data-ttu-id="9c722-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="9c722-118">Data Item Name</span></span>|<span data-ttu-id="9c722-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="9c722-119">Data Item Type</span></span>|<span data-ttu-id="9c722-120">Description</span><span class="sxs-lookup"><span data-stu-id="9c722-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9c722-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="9c722-121">ParentActivity</span></span>|<span data-ttu-id="9c722-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="9c722-122">xs:string</span></span>|<span data-ttu-id="9c722-123">Nom de type de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="9c722-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="9c722-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="9c722-124">ParentDisplayName</span></span>|<span data-ttu-id="9c722-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="9c722-125">xs:string</span></span>|<span data-ttu-id="9c722-126">Nom complet de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="9c722-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="9c722-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="9c722-127">ParentInstanceId</span></span>|<span data-ttu-id="9c722-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="9c722-128">xs:string</span></span>|<span data-ttu-id="9c722-129">ID d'instance de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="9c722-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="9c722-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="9c722-130">CompletedActivity</span></span>|<span data-ttu-id="9c722-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="9c722-131">xs:string</span></span>|<span data-ttu-id="9c722-132">Nom de type de l'activité achevée.</span><span class="sxs-lookup"><span data-stu-id="9c722-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="9c722-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="9c722-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="9c722-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="9c722-134">xs:string</span></span>|<span data-ttu-id="9c722-135">Nom complet de l'activité achevée.</span><span class="sxs-lookup"><span data-stu-id="9c722-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="9c722-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="9c722-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="9c722-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="9c722-137">xs:string</span></span>|<span data-ttu-id="9c722-138">ID d'instance de l'activité achevée.</span><span class="sxs-lookup"><span data-stu-id="9c722-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="9c722-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9c722-139">AppDomain</span></span>|<span data-ttu-id="9c722-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="9c722-140">xs:string</span></span>|<span data-ttu-id="9c722-141">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9c722-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
