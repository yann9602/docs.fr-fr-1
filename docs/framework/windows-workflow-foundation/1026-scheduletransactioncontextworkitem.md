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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4d881f1be4e809cf45f100b966d6013ae8fa88f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1026---scheduletransactioncontextworkitem"></a><span data-ttu-id="4449e-102">1026 - ScheduleTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="4449e-102">1026 - ScheduleTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="4449e-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="4449e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4449e-104">ID</span><span class="sxs-lookup"><span data-stu-id="4449e-104">ID</span></span>|<span data-ttu-id="4449e-105">1026</span><span class="sxs-lookup"><span data-stu-id="4449e-105">1026</span></span>|  
|<span data-ttu-id="4449e-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="4449e-106">Keywords</span></span>|<span data-ttu-id="4449e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4449e-107">WFRuntime</span></span>|  
|<span data-ttu-id="4449e-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="4449e-108">Level</span></span>|<span data-ttu-id="4449e-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="4449e-109">Verbose</span></span>|  
|<span data-ttu-id="4449e-110">Canal</span><span class="sxs-lookup"><span data-stu-id="4449e-110">Channel</span></span>|<span data-ttu-id="4449e-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="4449e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4449e-112">Description</span><span class="sxs-lookup"><span data-stu-id="4449e-112">Description</span></span>  
 <span data-ttu-id="4449e-113">Indique qu'un TransactionContextWorkItem a été planifié.</span><span class="sxs-lookup"><span data-stu-id="4449e-113">Indicates a TransactionContextWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4449e-114">Message</span><span class="sxs-lookup"><span data-stu-id="4449e-114">Message</span></span>  
 <span data-ttu-id="4449e-115">TransactionContextWorkItem a été planifié pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="4449e-115">A TransactionContextWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4449e-116">Détails</span><span class="sxs-lookup"><span data-stu-id="4449e-116">Details</span></span>  
  
|<span data-ttu-id="4449e-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="4449e-117">Data Item Name</span></span>|<span data-ttu-id="4449e-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="4449e-118">Data Item Type</span></span>|<span data-ttu-id="4449e-119">Description</span><span class="sxs-lookup"><span data-stu-id="4449e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4449e-120">Activité</span><span class="sxs-lookup"><span data-stu-id="4449e-120">Activity</span></span>|<span data-ttu-id="4449e-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="4449e-121">xs:string</span></span>|<span data-ttu-id="4449e-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="4449e-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="4449e-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="4449e-123">DisplayName</span></span>|<span data-ttu-id="4449e-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="4449e-124">xs:string</span></span>|<span data-ttu-id="4449e-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="4449e-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="4449e-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="4449e-126">InstanceId</span></span>|<span data-ttu-id="4449e-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="4449e-127">xs:string</span></span>|<span data-ttu-id="4449e-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="4449e-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="4449e-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4449e-129">AppDomain</span></span>|<span data-ttu-id="4449e-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="4449e-130">xs:string</span></span>|<span data-ttu-id="4449e-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="4449e-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
