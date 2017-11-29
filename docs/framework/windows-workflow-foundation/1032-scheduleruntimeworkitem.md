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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4de69b1fc2647d7723db8aebb02942938db7478f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1032---scheduleruntimeworkitem"></a><span data-ttu-id="c7b08-102">1032 - ScheduleRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="c7b08-102">1032 - ScheduleRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="c7b08-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="c7b08-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c7b08-104">ID</span><span class="sxs-lookup"><span data-stu-id="c7b08-104">ID</span></span>|<span data-ttu-id="c7b08-105">1032</span><span class="sxs-lookup"><span data-stu-id="c7b08-105">1032</span></span>|  
|<span data-ttu-id="c7b08-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="c7b08-106">Keywords</span></span>|<span data-ttu-id="c7b08-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c7b08-107">WFRuntime</span></span>|  
|<span data-ttu-id="c7b08-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="c7b08-108">Level</span></span>|<span data-ttu-id="c7b08-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="c7b08-109">Verbose</span></span>|  
|<span data-ttu-id="c7b08-110">Canal</span><span class="sxs-lookup"><span data-stu-id="c7b08-110">Channel</span></span>|<span data-ttu-id="c7b08-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="c7b08-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c7b08-112">Description</span><span class="sxs-lookup"><span data-stu-id="c7b08-112">Description</span></span>  
 <span data-ttu-id="c7b08-113">Indique qu'un RuntimeWorkItem a été planifié.</span><span class="sxs-lookup"><span data-stu-id="c7b08-113">Indicates a RuntimeWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c7b08-114">Message</span><span class="sxs-lookup"><span data-stu-id="c7b08-114">Message</span></span>  
 <span data-ttu-id="c7b08-115">Un élément de travail runtime a été planifié pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="c7b08-115">A runtime work item has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c7b08-116">Détails</span><span class="sxs-lookup"><span data-stu-id="c7b08-116">Details</span></span>  
  
|<span data-ttu-id="c7b08-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="c7b08-117">Data Item Name</span></span>|<span data-ttu-id="c7b08-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="c7b08-118">Data Item Type</span></span>|<span data-ttu-id="c7b08-119">Description</span><span class="sxs-lookup"><span data-stu-id="c7b08-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c7b08-120">Activité</span><span class="sxs-lookup"><span data-stu-id="c7b08-120">Activity</span></span>|<span data-ttu-id="c7b08-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="c7b08-121">xs:string</span></span>|<span data-ttu-id="c7b08-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="c7b08-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="c7b08-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="c7b08-123">DisplayName</span></span>|<span data-ttu-id="c7b08-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="c7b08-124">xs:string</span></span>|<span data-ttu-id="c7b08-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="c7b08-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="c7b08-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="c7b08-126">InstanceId</span></span>|<span data-ttu-id="c7b08-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="c7b08-127">xs:string</span></span>|<span data-ttu-id="c7b08-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="c7b08-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="c7b08-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c7b08-129">AppDomain</span></span>|<span data-ttu-id="c7b08-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="c7b08-130">xs:string</span></span>|<span data-ttu-id="c7b08-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c7b08-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
