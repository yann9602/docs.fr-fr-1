---
title: 1019 - CompleteCancelActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75a4a1ab-e5a3-4f4e-88e4-d19806e671d7
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9f8af4486d4659afd4c98016a6f88719271f1a1b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1019---completecancelactivityworkitem"></a><span data-ttu-id="1e2d1-102">1019 - CompleteCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="1e2d1-102">1019 - CompleteCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="1e2d1-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="1e2d1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1e2d1-104">ID</span><span class="sxs-lookup"><span data-stu-id="1e2d1-104">ID</span></span>|<span data-ttu-id="1e2d1-105">1019</span><span class="sxs-lookup"><span data-stu-id="1e2d1-105">1019</span></span>|  
|<span data-ttu-id="1e2d1-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="1e2d1-106">Keywords</span></span>|<span data-ttu-id="1e2d1-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="1e2d1-107">WFRuntime</span></span>|  
|<span data-ttu-id="1e2d1-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="1e2d1-108">Level</span></span>|<span data-ttu-id="1e2d1-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="1e2d1-109">Verbose</span></span>|  
|<span data-ttu-id="1e2d1-110">Canal</span><span class="sxs-lookup"><span data-stu-id="1e2d1-110">Channel</span></span>|<span data-ttu-id="1e2d1-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="1e2d1-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1e2d1-112">Description</span><span class="sxs-lookup"><span data-stu-id="1e2d1-112">Description</span></span>  
 <span data-ttu-id="1e2d1-113">Indique qu'un CancelActivityWorkItem est terminé.</span><span class="sxs-lookup"><span data-stu-id="1e2d1-113">Indicates a CancelActivityWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1e2d1-114">Message</span><span class="sxs-lookup"><span data-stu-id="1e2d1-114">Message</span></span>  
 <span data-ttu-id="1e2d1-115">CancelActivityWorkItem est terminé pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="1e2d1-115">A CancelActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1e2d1-116">Détails</span><span class="sxs-lookup"><span data-stu-id="1e2d1-116">Details</span></span>  
  
|<span data-ttu-id="1e2d1-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="1e2d1-117">Data Item Name</span></span>|<span data-ttu-id="1e2d1-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="1e2d1-118">Data Item Type</span></span>|<span data-ttu-id="1e2d1-119">Description</span><span class="sxs-lookup"><span data-stu-id="1e2d1-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1e2d1-120">Activité</span><span class="sxs-lookup"><span data-stu-id="1e2d1-120">Activity</span></span>|<span data-ttu-id="1e2d1-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="1e2d1-121">xs:string</span></span>|<span data-ttu-id="1e2d1-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="1e2d1-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="1e2d1-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="1e2d1-123">DisplayName</span></span>|<span data-ttu-id="1e2d1-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="1e2d1-124">xs:string</span></span>|<span data-ttu-id="1e2d1-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="1e2d1-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="1e2d1-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="1e2d1-126">InstanceId</span></span>|<span data-ttu-id="1e2d1-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="1e2d1-127">xs:string</span></span>|<span data-ttu-id="1e2d1-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="1e2d1-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="1e2d1-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1e2d1-129">AppDomain</span></span>|<span data-ttu-id="1e2d1-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="1e2d1-130">xs:string</span></span>|<span data-ttu-id="1e2d1-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="1e2d1-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
