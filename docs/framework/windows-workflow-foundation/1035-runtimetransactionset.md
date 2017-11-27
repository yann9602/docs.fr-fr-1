---
title: 1035 - RuntimeTransactionSet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c3fcd93dbc30b20f7822a54babde8277e32d8335
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1035---runtimetransactionset"></a><span data-ttu-id="205b9-102">1035 - RuntimeTransactionSet</span><span class="sxs-lookup"><span data-stu-id="205b9-102">1035 - RuntimeTransactionSet</span></span>
## <a name="properties"></a><span data-ttu-id="205b9-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="205b9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="205b9-104">ID</span><span class="sxs-lookup"><span data-stu-id="205b9-104">ID</span></span>|<span data-ttu-id="205b9-105">1035</span><span class="sxs-lookup"><span data-stu-id="205b9-105">1035</span></span>|  
|<span data-ttu-id="205b9-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="205b9-106">Keywords</span></span>|<span data-ttu-id="205b9-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="205b9-107">WFRuntime</span></span>|  
|<span data-ttu-id="205b9-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="205b9-108">Level</span></span>|<span data-ttu-id="205b9-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="205b9-109">Verbose</span></span>|  
|<span data-ttu-id="205b9-110">Canal</span><span class="sxs-lookup"><span data-stu-id="205b9-110">Channel</span></span>|<span data-ttu-id="205b9-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="205b9-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="205b9-112">Description</span><span class="sxs-lookup"><span data-stu-id="205b9-112">Description</span></span>  
 <span data-ttu-id="205b9-113">Indique qu'une activité a défini la transaction d'exécution.</span><span class="sxs-lookup"><span data-stu-id="205b9-113">Indicates an activity has set the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="205b9-114">Message</span><span class="sxs-lookup"><span data-stu-id="205b9-114">Message</span></span>  
 <span data-ttu-id="205b9-115">La transaction runtime a été définie par l’activité '%1', DisplayName : '%2', InstanceId : '%3'.</span><span class="sxs-lookup"><span data-stu-id="205b9-115">The runtime transaction has been set by Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="205b9-116">L’exécution isolée à l’activité '%4', DisplayName : '%5', InstanceId : '%6'.</span><span class="sxs-lookup"><span data-stu-id="205b9-116">Execution isolated to Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="205b9-117">Détails</span><span class="sxs-lookup"><span data-stu-id="205b9-117">Details</span></span>  
  
|<span data-ttu-id="205b9-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="205b9-118">Data Item Name</span></span>|<span data-ttu-id="205b9-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="205b9-119">Data Item Type</span></span>|<span data-ttu-id="205b9-120">Description</span><span class="sxs-lookup"><span data-stu-id="205b9-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="205b9-121">Activité</span><span class="sxs-lookup"><span data-stu-id="205b9-121">Activity</span></span>|<span data-ttu-id="205b9-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="205b9-122">xs:string</span></span>|<span data-ttu-id="205b9-123">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="205b9-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="205b9-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="205b9-124">DisplayName</span></span>|<span data-ttu-id="205b9-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="205b9-125">xs:string</span></span>|<span data-ttu-id="205b9-126">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="205b9-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="205b9-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="205b9-127">InstanceId</span></span>|<span data-ttu-id="205b9-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="205b9-128">xs:string</span></span>|<span data-ttu-id="205b9-129">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="205b9-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="205b9-130">IsolatedActivity</span><span class="sxs-lookup"><span data-stu-id="205b9-130">IsolatedActivity</span></span>|<span data-ttu-id="205b9-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="205b9-131">xs:string</span></span>|<span data-ttu-id="205b9-132">Nom de type de l'activité dans laquelle la transaction est isolée.</span><span class="sxs-lookup"><span data-stu-id="205b9-132">The type name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="205b9-133">IsolatedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="205b9-133">IsolatedActivityDisplayName</span></span>|<span data-ttu-id="205b9-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="205b9-134">xs:string</span></span>|<span data-ttu-id="205b9-135">Nom complet de l'activité dans laquelle la transaction est isolée.</span><span class="sxs-lookup"><span data-stu-id="205b9-135">The display name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="205b9-136">IsolatedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="205b9-136">IsolatedActivityInstanceId</span></span>|<span data-ttu-id="205b9-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="205b9-137">xs:string</span></span>|<span data-ttu-id="205b9-138">ID d'instance de l'activité dans laquelle la transaction est isolée.</span><span class="sxs-lookup"><span data-stu-id="205b9-138">The instance id of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="205b9-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="205b9-139">AppDomain</span></span>|<span data-ttu-id="205b9-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="205b9-140">xs:string</span></span>|<span data-ttu-id="205b9-141">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="205b9-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
