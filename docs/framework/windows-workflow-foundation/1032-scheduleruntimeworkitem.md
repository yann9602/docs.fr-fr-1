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
ms.workload: dotnet
ms.openlocfilehash: 81cc73a5ab58e90f1a0ee5bdaf9a491d20206fb3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="1032---scheduleruntimeworkitem"></a><span data-ttu-id="efff3-102">1032 - ScheduleRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="efff3-102">1032 - ScheduleRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="efff3-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="efff3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="efff3-104">ID</span><span class="sxs-lookup"><span data-stu-id="efff3-104">ID</span></span>|<span data-ttu-id="efff3-105">1032</span><span class="sxs-lookup"><span data-stu-id="efff3-105">1032</span></span>|  
|<span data-ttu-id="efff3-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="efff3-106">Keywords</span></span>|<span data-ttu-id="efff3-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="efff3-107">WFRuntime</span></span>|  
|<span data-ttu-id="efff3-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="efff3-108">Level</span></span>|<span data-ttu-id="efff3-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="efff3-109">Verbose</span></span>|  
|<span data-ttu-id="efff3-110">Canal</span><span class="sxs-lookup"><span data-stu-id="efff3-110">Channel</span></span>|<span data-ttu-id="efff3-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="efff3-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="efff3-112">Description</span><span class="sxs-lookup"><span data-stu-id="efff3-112">Description</span></span>  
 <span data-ttu-id="efff3-113">Indique qu'un RuntimeWorkItem a été planifié.</span><span class="sxs-lookup"><span data-stu-id="efff3-113">Indicates a RuntimeWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="efff3-114">Message</span><span class="sxs-lookup"><span data-stu-id="efff3-114">Message</span></span>  
 <span data-ttu-id="efff3-115">Un élément de travail runtime a été planifié pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="efff3-115">A runtime work item has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="efff3-116">Détails</span><span class="sxs-lookup"><span data-stu-id="efff3-116">Details</span></span>  
  
|<span data-ttu-id="efff3-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="efff3-117">Data Item Name</span></span>|<span data-ttu-id="efff3-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="efff3-118">Data Item Type</span></span>|<span data-ttu-id="efff3-119">Description</span><span class="sxs-lookup"><span data-stu-id="efff3-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="efff3-120">Activité</span><span class="sxs-lookup"><span data-stu-id="efff3-120">Activity</span></span>|<span data-ttu-id="efff3-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="efff3-121">xs:string</span></span>|<span data-ttu-id="efff3-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="efff3-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="efff3-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="efff3-123">DisplayName</span></span>|<span data-ttu-id="efff3-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="efff3-124">xs:string</span></span>|<span data-ttu-id="efff3-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="efff3-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="efff3-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="efff3-126">InstanceId</span></span>|<span data-ttu-id="efff3-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="efff3-127">xs:string</span></span>|<span data-ttu-id="efff3-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="efff3-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="efff3-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="efff3-129">AppDomain</span></span>|<span data-ttu-id="efff3-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="efff3-130">xs:string</span></span>|<span data-ttu-id="efff3-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="efff3-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
