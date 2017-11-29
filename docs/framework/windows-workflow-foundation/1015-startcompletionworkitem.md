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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7457b65f81e9e26b9de6055df474a83ce4264846
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1015---startcompletionworkitem"></a><span data-ttu-id="1aecf-102">1015 - StartCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="1aecf-102">1015 - StartCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="1aecf-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="1aecf-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1aecf-104">ID</span><span class="sxs-lookup"><span data-stu-id="1aecf-104">ID</span></span>|<span data-ttu-id="1aecf-105">1015</span><span class="sxs-lookup"><span data-stu-id="1aecf-105">1015</span></span>|  
|<span data-ttu-id="1aecf-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="1aecf-106">Keywords</span></span>|<span data-ttu-id="1aecf-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="1aecf-107">WFRuntime</span></span>|  
|<span data-ttu-id="1aecf-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="1aecf-108">Level</span></span>|<span data-ttu-id="1aecf-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="1aecf-109">Verbose</span></span>|  
|<span data-ttu-id="1aecf-110">Canal</span><span class="sxs-lookup"><span data-stu-id="1aecf-110">Channel</span></span>|<span data-ttu-id="1aecf-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="1aecf-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1aecf-112">Description</span><span class="sxs-lookup"><span data-stu-id="1aecf-112">Description</span></span>  
 <span data-ttu-id="1aecf-113">Indique qu'un CompletionWorkItem démarre l'exécution.</span><span class="sxs-lookup"><span data-stu-id="1aecf-113">Indicates a CompletionWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1aecf-114">Message</span><span class="sxs-lookup"><span data-stu-id="1aecf-114">Message</span></span>  
 <span data-ttu-id="1aecf-115">Début de l'exécution d'un CompletionWorkItem pour l'activité parente « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="1aecf-115">Starting execution of a CompletionWorkItem for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="1aecf-116">Activité terminée « %4 », DisplayName : « %5 », InstanceId : « %6 ».</span><span class="sxs-lookup"><span data-stu-id="1aecf-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1aecf-117">Détails</span><span class="sxs-lookup"><span data-stu-id="1aecf-117">Details</span></span>  
  
|<span data-ttu-id="1aecf-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="1aecf-118">Data Item Name</span></span>|<span data-ttu-id="1aecf-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="1aecf-119">Data Item Type</span></span>|<span data-ttu-id="1aecf-120">Description</span><span class="sxs-lookup"><span data-stu-id="1aecf-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1aecf-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="1aecf-121">ParentActivity</span></span>|<span data-ttu-id="1aecf-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="1aecf-122">xs:string</span></span>|<span data-ttu-id="1aecf-123">Nom de type de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="1aecf-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="1aecf-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="1aecf-124">ParentDisplayName</span></span>|<span data-ttu-id="1aecf-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="1aecf-125">xs:string</span></span>|<span data-ttu-id="1aecf-126">Nom complet de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="1aecf-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="1aecf-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="1aecf-127">ParentInstanceId</span></span>|<span data-ttu-id="1aecf-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="1aecf-128">xs:string</span></span>|<span data-ttu-id="1aecf-129">ID d'instance de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="1aecf-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="1aecf-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="1aecf-130">CompletedActivity</span></span>|<span data-ttu-id="1aecf-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="1aecf-131">xs:string</span></span>|<span data-ttu-id="1aecf-132">Nom de type de l'activité achevée.</span><span class="sxs-lookup"><span data-stu-id="1aecf-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="1aecf-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="1aecf-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="1aecf-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="1aecf-134">xs:string</span></span>|<span data-ttu-id="1aecf-135">Nom complet de l'activité achevée.</span><span class="sxs-lookup"><span data-stu-id="1aecf-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="1aecf-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="1aecf-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="1aecf-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="1aecf-137">xs:string</span></span>|<span data-ttu-id="1aecf-138">ID d'instance de l'activité achevée.</span><span class="sxs-lookup"><span data-stu-id="1aecf-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="1aecf-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1aecf-139">AppDomain</span></span>|<span data-ttu-id="1aecf-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="1aecf-140">xs:string</span></span>|<span data-ttu-id="1aecf-141">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="1aecf-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
