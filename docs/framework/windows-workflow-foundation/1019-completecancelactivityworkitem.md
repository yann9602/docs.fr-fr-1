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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4cf96d665bcd5ff703f54d2f15d1912ad0b9573c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="1019---completecancelactivityworkitem"></a><span data-ttu-id="b62ae-102">1019 - CompleteCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="b62ae-102">1019 - CompleteCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="b62ae-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="b62ae-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b62ae-104">ID</span><span class="sxs-lookup"><span data-stu-id="b62ae-104">ID</span></span>|<span data-ttu-id="b62ae-105">1019</span><span class="sxs-lookup"><span data-stu-id="b62ae-105">1019</span></span>|  
|<span data-ttu-id="b62ae-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="b62ae-106">Keywords</span></span>|<span data-ttu-id="b62ae-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b62ae-107">WFRuntime</span></span>|  
|<span data-ttu-id="b62ae-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="b62ae-108">Level</span></span>|<span data-ttu-id="b62ae-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="b62ae-109">Verbose</span></span>|  
|<span data-ttu-id="b62ae-110">Canal</span><span class="sxs-lookup"><span data-stu-id="b62ae-110">Channel</span></span>|<span data-ttu-id="b62ae-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="b62ae-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b62ae-112">Description</span><span class="sxs-lookup"><span data-stu-id="b62ae-112">Description</span></span>  
 <span data-ttu-id="b62ae-113">Indique qu'un CancelActivityWorkItem est terminé.</span><span class="sxs-lookup"><span data-stu-id="b62ae-113">Indicates a CancelActivityWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b62ae-114">Message</span><span class="sxs-lookup"><span data-stu-id="b62ae-114">Message</span></span>  
 <span data-ttu-id="b62ae-115">CancelActivityWorkItem est terminé pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="b62ae-115">A CancelActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b62ae-116">Détails</span><span class="sxs-lookup"><span data-stu-id="b62ae-116">Details</span></span>  
  
|<span data-ttu-id="b62ae-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="b62ae-117">Data Item Name</span></span>|<span data-ttu-id="b62ae-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="b62ae-118">Data Item Type</span></span>|<span data-ttu-id="b62ae-119">Description</span><span class="sxs-lookup"><span data-stu-id="b62ae-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b62ae-120">Activité</span><span class="sxs-lookup"><span data-stu-id="b62ae-120">Activity</span></span>|<span data-ttu-id="b62ae-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="b62ae-121">xs:string</span></span>|<span data-ttu-id="b62ae-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="b62ae-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="b62ae-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="b62ae-123">DisplayName</span></span>|<span data-ttu-id="b62ae-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="b62ae-124">xs:string</span></span>|<span data-ttu-id="b62ae-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="b62ae-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="b62ae-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="b62ae-126">InstanceId</span></span>|<span data-ttu-id="b62ae-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="b62ae-127">xs:string</span></span>|<span data-ttu-id="b62ae-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="b62ae-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="b62ae-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b62ae-129">AppDomain</span></span>|<span data-ttu-id="b62ae-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="b62ae-130">xs:string</span></span>|<span data-ttu-id="b62ae-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b62ae-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
