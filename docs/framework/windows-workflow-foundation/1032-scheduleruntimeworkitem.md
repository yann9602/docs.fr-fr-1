---
title: 1032 - ScheduleRuntimeWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54688101-becf-42f3-80ca-f53a7b527620
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d2a150b9e9c78a9ce1f5e20b962a58ef2d5dde9d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="1032---scheduleruntimeworkitem"></a><span data-ttu-id="05448-102">1032 - ScheduleRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="05448-102">1032 - ScheduleRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="05448-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="05448-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="05448-104">ID</span><span class="sxs-lookup"><span data-stu-id="05448-104">ID</span></span>|<span data-ttu-id="05448-105">1032</span><span class="sxs-lookup"><span data-stu-id="05448-105">1032</span></span>|  
|<span data-ttu-id="05448-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="05448-106">Keywords</span></span>|<span data-ttu-id="05448-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="05448-107">WFRuntime</span></span>|  
|<span data-ttu-id="05448-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="05448-108">Level</span></span>|<span data-ttu-id="05448-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="05448-109">Verbose</span></span>|  
|<span data-ttu-id="05448-110">Canal</span><span class="sxs-lookup"><span data-stu-id="05448-110">Channel</span></span>|<span data-ttu-id="05448-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="05448-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="05448-112">Description</span><span class="sxs-lookup"><span data-stu-id="05448-112">Description</span></span>  
 <span data-ttu-id="05448-113">Indique qu'un RuntimeWorkItem a été planifié.</span><span class="sxs-lookup"><span data-stu-id="05448-113">Indicates a RuntimeWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="05448-114">Message</span><span class="sxs-lookup"><span data-stu-id="05448-114">Message</span></span>  
 <span data-ttu-id="05448-115">Un élément de travail runtime a été planifié pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="05448-115">A runtime work item has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="05448-116">Détails</span><span class="sxs-lookup"><span data-stu-id="05448-116">Details</span></span>  
  
|<span data-ttu-id="05448-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="05448-117">Data Item Name</span></span>|<span data-ttu-id="05448-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="05448-118">Data Item Type</span></span>|<span data-ttu-id="05448-119">Description</span><span class="sxs-lookup"><span data-stu-id="05448-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="05448-120">Activité</span><span class="sxs-lookup"><span data-stu-id="05448-120">Activity</span></span>|<span data-ttu-id="05448-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="05448-121">xs:string</span></span>|<span data-ttu-id="05448-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="05448-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="05448-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="05448-123">DisplayName</span></span>|<span data-ttu-id="05448-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="05448-124">xs:string</span></span>|<span data-ttu-id="05448-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="05448-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="05448-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="05448-126">InstanceId</span></span>|<span data-ttu-id="05448-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="05448-127">xs:string</span></span>|<span data-ttu-id="05448-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="05448-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="05448-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="05448-129">AppDomain</span></span>|<span data-ttu-id="05448-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="05448-130">xs:string</span></span>|<span data-ttu-id="05448-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="05448-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
