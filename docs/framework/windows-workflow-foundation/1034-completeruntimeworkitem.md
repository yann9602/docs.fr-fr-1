---
title: 1034 - CompleteRuntimeWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45620011-8b04-4f87-ab5a-65b24145e17d
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 63ab145b8a0688a7f7bbf7dbcbe8dfe612eab294
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1034---completeruntimeworkitem"></a><span data-ttu-id="bdcbe-102">1034 - CompleteRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="bdcbe-102">1034 - CompleteRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="bdcbe-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="bdcbe-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bdcbe-104">ID</span><span class="sxs-lookup"><span data-stu-id="bdcbe-104">ID</span></span>|<span data-ttu-id="bdcbe-105">1034</span><span class="sxs-lookup"><span data-stu-id="bdcbe-105">1034</span></span>|  
|<span data-ttu-id="bdcbe-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="bdcbe-106">Keywords</span></span>|<span data-ttu-id="bdcbe-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="bdcbe-107">WFRuntime</span></span>|  
|<span data-ttu-id="bdcbe-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="bdcbe-108">Level</span></span>|<span data-ttu-id="bdcbe-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="bdcbe-109">Verbose</span></span>|  
|<span data-ttu-id="bdcbe-110">Canal</span><span class="sxs-lookup"><span data-stu-id="bdcbe-110">Channel</span></span>|<span data-ttu-id="bdcbe-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="bdcbe-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bdcbe-112">Description</span><span class="sxs-lookup"><span data-stu-id="bdcbe-112">Description</span></span>  
 <span data-ttu-id="bdcbe-113">Indique qu'un RuntimeWorkItem est terminé.</span><span class="sxs-lookup"><span data-stu-id="bdcbe-113">Indicates a RuntimeWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bdcbe-114">Message</span><span class="sxs-lookup"><span data-stu-id="bdcbe-114">Message</span></span>  
 <span data-ttu-id="bdcbe-115">Un élément de travail runtime est terminé pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="bdcbe-115">A runtime work item has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bdcbe-116">Détails</span><span class="sxs-lookup"><span data-stu-id="bdcbe-116">Details</span></span>  
  
|<span data-ttu-id="bdcbe-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="bdcbe-117">Data Item Name</span></span>|<span data-ttu-id="bdcbe-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="bdcbe-118">Data Item Type</span></span>|<span data-ttu-id="bdcbe-119">Description</span><span class="sxs-lookup"><span data-stu-id="bdcbe-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bdcbe-120">Activité</span><span class="sxs-lookup"><span data-stu-id="bdcbe-120">Activity</span></span>|<span data-ttu-id="bdcbe-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="bdcbe-121">xs:string</span></span>|<span data-ttu-id="bdcbe-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="bdcbe-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="bdcbe-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="bdcbe-123">DisplayName</span></span>|<span data-ttu-id="bdcbe-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="bdcbe-124">xs:string</span></span>|<span data-ttu-id="bdcbe-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="bdcbe-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="bdcbe-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="bdcbe-126">InstanceId</span></span>|<span data-ttu-id="bdcbe-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="bdcbe-127">xs:string</span></span>|<span data-ttu-id="bdcbe-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="bdcbe-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="bdcbe-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="bdcbe-129">AppDomain</span></span>|<span data-ttu-id="bdcbe-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="bdcbe-130">xs:string</span></span>|<span data-ttu-id="bdcbe-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="bdcbe-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
