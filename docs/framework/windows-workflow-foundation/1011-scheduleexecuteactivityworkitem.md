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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 498752bfc896891a43a6a2e7a8245c508795c1ce
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1011---scheduleexecuteactivityworkitem"></a><span data-ttu-id="7f0c5-102">1011 - ScheduleExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="7f0c5-102">1011 - ScheduleExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="7f0c5-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="7f0c5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7f0c5-104">ID</span><span class="sxs-lookup"><span data-stu-id="7f0c5-104">ID</span></span>|<span data-ttu-id="7f0c5-105">1011</span><span class="sxs-lookup"><span data-stu-id="7f0c5-105">1011</span></span>|  
|<span data-ttu-id="7f0c5-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="7f0c5-106">Keywords</span></span>|<span data-ttu-id="7f0c5-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="7f0c5-107">WFRuntime</span></span>|  
|<span data-ttu-id="7f0c5-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="7f0c5-108">Level</span></span>|<span data-ttu-id="7f0c5-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="7f0c5-109">Verbose</span></span>|  
|<span data-ttu-id="7f0c5-110">Canal</span><span class="sxs-lookup"><span data-stu-id="7f0c5-110">Channel</span></span>|<span data-ttu-id="7f0c5-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="7f0c5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7f0c5-112">Description</span><span class="sxs-lookup"><span data-stu-id="7f0c5-112">Description</span></span>  
 <span data-ttu-id="7f0c5-113">Indique qu'un ExecuteActivityWorkItem a été planifié.</span><span class="sxs-lookup"><span data-stu-id="7f0c5-113">Indicates an ExecuteActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7f0c5-114">Message</span><span class="sxs-lookup"><span data-stu-id="7f0c5-114">Message</span></span>  
 <span data-ttu-id="7f0c5-115">ExecuteActivityWorkItem a été planifié pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="7f0c5-115">An ExecuteActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7f0c5-116">Détails</span><span class="sxs-lookup"><span data-stu-id="7f0c5-116">Details</span></span>  
  
|<span data-ttu-id="7f0c5-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="7f0c5-117">Data Item Name</span></span>|<span data-ttu-id="7f0c5-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="7f0c5-118">Data Item Type</span></span>|<span data-ttu-id="7f0c5-119">Description</span><span class="sxs-lookup"><span data-stu-id="7f0c5-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7f0c5-120">Activité</span><span class="sxs-lookup"><span data-stu-id="7f0c5-120">Activity</span></span>|<span data-ttu-id="7f0c5-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="7f0c5-121">xs:string</span></span>|<span data-ttu-id="7f0c5-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="7f0c5-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="7f0c5-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="7f0c5-123">DisplayName</span></span>|<span data-ttu-id="7f0c5-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="7f0c5-124">xs:string</span></span>|<span data-ttu-id="7f0c5-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="7f0c5-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="7f0c5-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="7f0c5-126">InstanceId</span></span>|<span data-ttu-id="7f0c5-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="7f0c5-127">xs:string</span></span>|<span data-ttu-id="7f0c5-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="7f0c5-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="7f0c5-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7f0c5-129">AppDomain</span></span>|<span data-ttu-id="7f0c5-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="7f0c5-130">xs:string</span></span>|<span data-ttu-id="7f0c5-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="7f0c5-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
