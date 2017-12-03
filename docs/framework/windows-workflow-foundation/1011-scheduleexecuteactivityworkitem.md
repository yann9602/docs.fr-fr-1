---
title: 1011 - ScheduleExecuteActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e503ae46-ad6b-4fcb-8c0e-146d59a8eff1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec89acb9d83a28ac280db7c3d536bfe63669fa97
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="1011---scheduleexecuteactivityworkitem"></a><span data-ttu-id="98bc8-102">1011 - ScheduleExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="98bc8-102">1011 - ScheduleExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="98bc8-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="98bc8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="98bc8-104">ID</span><span class="sxs-lookup"><span data-stu-id="98bc8-104">ID</span></span>|<span data-ttu-id="98bc8-105">1011</span><span class="sxs-lookup"><span data-stu-id="98bc8-105">1011</span></span>|  
|<span data-ttu-id="98bc8-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="98bc8-106">Keywords</span></span>|<span data-ttu-id="98bc8-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="98bc8-107">WFRuntime</span></span>|  
|<span data-ttu-id="98bc8-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="98bc8-108">Level</span></span>|<span data-ttu-id="98bc8-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="98bc8-109">Verbose</span></span>|  
|<span data-ttu-id="98bc8-110">Canal</span><span class="sxs-lookup"><span data-stu-id="98bc8-110">Channel</span></span>|<span data-ttu-id="98bc8-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="98bc8-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="98bc8-112">Description</span><span class="sxs-lookup"><span data-stu-id="98bc8-112">Description</span></span>  
 <span data-ttu-id="98bc8-113">Indique qu'un ExecuteActivityWorkItem a été planifié.</span><span class="sxs-lookup"><span data-stu-id="98bc8-113">Indicates an ExecuteActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="98bc8-114">Message</span><span class="sxs-lookup"><span data-stu-id="98bc8-114">Message</span></span>  
 <span data-ttu-id="98bc8-115">ExecuteActivityWorkItem a été planifié pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="98bc8-115">An ExecuteActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="98bc8-116">Détails</span><span class="sxs-lookup"><span data-stu-id="98bc8-116">Details</span></span>  
  
|<span data-ttu-id="98bc8-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="98bc8-117">Data Item Name</span></span>|<span data-ttu-id="98bc8-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="98bc8-118">Data Item Type</span></span>|<span data-ttu-id="98bc8-119">Description</span><span class="sxs-lookup"><span data-stu-id="98bc8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="98bc8-120">Activité</span><span class="sxs-lookup"><span data-stu-id="98bc8-120">Activity</span></span>|<span data-ttu-id="98bc8-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="98bc8-121">xs:string</span></span>|<span data-ttu-id="98bc8-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="98bc8-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="98bc8-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="98bc8-123">DisplayName</span></span>|<span data-ttu-id="98bc8-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="98bc8-124">xs:string</span></span>|<span data-ttu-id="98bc8-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="98bc8-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="98bc8-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="98bc8-126">InstanceId</span></span>|<span data-ttu-id="98bc8-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="98bc8-127">xs:string</span></span>|<span data-ttu-id="98bc8-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="98bc8-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="98bc8-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="98bc8-129">AppDomain</span></span>|<span data-ttu-id="98bc8-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="98bc8-130">xs:string</span></span>|<span data-ttu-id="98bc8-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="98bc8-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
