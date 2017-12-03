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
ms.openlocfilehash: a5fb800718c1fd231d0cd02bf015333a44fa794f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="1026---scheduletransactioncontextworkitem"></a><span data-ttu-id="40037-102">1026 - ScheduleTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="40037-102">1026 - ScheduleTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="40037-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="40037-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="40037-104">ID</span><span class="sxs-lookup"><span data-stu-id="40037-104">ID</span></span>|<span data-ttu-id="40037-105">1026</span><span class="sxs-lookup"><span data-stu-id="40037-105">1026</span></span>|  
|<span data-ttu-id="40037-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="40037-106">Keywords</span></span>|<span data-ttu-id="40037-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="40037-107">WFRuntime</span></span>|  
|<span data-ttu-id="40037-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="40037-108">Level</span></span>|<span data-ttu-id="40037-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="40037-109">Verbose</span></span>|  
|<span data-ttu-id="40037-110">Canal</span><span class="sxs-lookup"><span data-stu-id="40037-110">Channel</span></span>|<span data-ttu-id="40037-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="40037-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="40037-112">Description</span><span class="sxs-lookup"><span data-stu-id="40037-112">Description</span></span>  
 <span data-ttu-id="40037-113">Indique qu'un TransactionContextWorkItem a été planifié.</span><span class="sxs-lookup"><span data-stu-id="40037-113">Indicates a TransactionContextWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="40037-114">Message</span><span class="sxs-lookup"><span data-stu-id="40037-114">Message</span></span>  
 <span data-ttu-id="40037-115">TransactionContextWorkItem a été planifié pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="40037-115">A TransactionContextWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="40037-116">Détails</span><span class="sxs-lookup"><span data-stu-id="40037-116">Details</span></span>  
  
|<span data-ttu-id="40037-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="40037-117">Data Item Name</span></span>|<span data-ttu-id="40037-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="40037-118">Data Item Type</span></span>|<span data-ttu-id="40037-119">Description</span><span class="sxs-lookup"><span data-stu-id="40037-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="40037-120">Activité</span><span class="sxs-lookup"><span data-stu-id="40037-120">Activity</span></span>|<span data-ttu-id="40037-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="40037-121">xs:string</span></span>|<span data-ttu-id="40037-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="40037-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="40037-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="40037-123">DisplayName</span></span>|<span data-ttu-id="40037-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="40037-124">xs:string</span></span>|<span data-ttu-id="40037-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="40037-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="40037-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="40037-126">InstanceId</span></span>|<span data-ttu-id="40037-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="40037-127">xs:string</span></span>|<span data-ttu-id="40037-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="40037-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="40037-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="40037-129">AppDomain</span></span>|<span data-ttu-id="40037-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="40037-130">xs:string</span></span>|<span data-ttu-id="40037-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="40037-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
