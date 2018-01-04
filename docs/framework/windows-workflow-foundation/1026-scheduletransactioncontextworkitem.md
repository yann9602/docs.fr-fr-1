---
title: 1026 - ScheduleTransactionContextWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d5f86ba-ec21-4129-a726-5432e425384c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83c99ddf9c5d4a8fa468303fb198abc349ace6d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="1026---scheduletransactioncontextworkitem"></a><span data-ttu-id="9e45d-102">1026 - ScheduleTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="9e45d-102">1026 - ScheduleTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="9e45d-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="9e45d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9e45d-104">ID</span><span class="sxs-lookup"><span data-stu-id="9e45d-104">ID</span></span>|<span data-ttu-id="9e45d-105">1026</span><span class="sxs-lookup"><span data-stu-id="9e45d-105">1026</span></span>|  
|<span data-ttu-id="9e45d-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="9e45d-106">Keywords</span></span>|<span data-ttu-id="9e45d-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9e45d-107">WFRuntime</span></span>|  
|<span data-ttu-id="9e45d-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="9e45d-108">Level</span></span>|<span data-ttu-id="9e45d-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="9e45d-109">Verbose</span></span>|  
|<span data-ttu-id="9e45d-110">Canal</span><span class="sxs-lookup"><span data-stu-id="9e45d-110">Channel</span></span>|<span data-ttu-id="9e45d-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="9e45d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9e45d-112">Description</span><span class="sxs-lookup"><span data-stu-id="9e45d-112">Description</span></span>  
 <span data-ttu-id="9e45d-113">Indique qu'un TransactionContextWorkItem a été planifié.</span><span class="sxs-lookup"><span data-stu-id="9e45d-113">Indicates a TransactionContextWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9e45d-114">Message</span><span class="sxs-lookup"><span data-stu-id="9e45d-114">Message</span></span>  
 <span data-ttu-id="9e45d-115">TransactionContextWorkItem a été planifié pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="9e45d-115">A TransactionContextWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9e45d-116">Détails</span><span class="sxs-lookup"><span data-stu-id="9e45d-116">Details</span></span>  
  
|<span data-ttu-id="9e45d-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="9e45d-117">Data Item Name</span></span>|<span data-ttu-id="9e45d-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="9e45d-118">Data Item Type</span></span>|<span data-ttu-id="9e45d-119">Description</span><span class="sxs-lookup"><span data-stu-id="9e45d-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9e45d-120">Activité</span><span class="sxs-lookup"><span data-stu-id="9e45d-120">Activity</span></span>|<span data-ttu-id="9e45d-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="9e45d-121">xs:string</span></span>|<span data-ttu-id="9e45d-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="9e45d-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="9e45d-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="9e45d-123">DisplayName</span></span>|<span data-ttu-id="9e45d-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="9e45d-124">xs:string</span></span>|<span data-ttu-id="9e45d-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="9e45d-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="9e45d-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="9e45d-126">InstanceId</span></span>|<span data-ttu-id="9e45d-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="9e45d-127">xs:string</span></span>|<span data-ttu-id="9e45d-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="9e45d-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="9e45d-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9e45d-129">AppDomain</span></span>|<span data-ttu-id="9e45d-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="9e45d-130">xs:string</span></span>|<span data-ttu-id="9e45d-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9e45d-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
