---
title: 1036 - RuntimeTransactionCompletionRequested
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d36b9f44-7c0f-4083-9d3a-9034dd2b98de
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4f497d777221a98b38603b2ced29342651b1020b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="e62a1-102">1036 - RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="e62a1-102">1036 - RuntimeTransactionCompletionRequested</span></span>
## <a name="properties"></a><span data-ttu-id="e62a1-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="e62a1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e62a1-104">ID</span><span class="sxs-lookup"><span data-stu-id="e62a1-104">ID</span></span>|<span data-ttu-id="e62a1-105">1036</span><span class="sxs-lookup"><span data-stu-id="e62a1-105">1036</span></span>|  
|<span data-ttu-id="e62a1-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="e62a1-106">Keywords</span></span>|<span data-ttu-id="e62a1-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e62a1-107">WFRuntime</span></span>|  
|<span data-ttu-id="e62a1-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="e62a1-108">Level</span></span>|<span data-ttu-id="e62a1-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="e62a1-109">Verbose</span></span>|  
|<span data-ttu-id="e62a1-110">Canal</span><span class="sxs-lookup"><span data-stu-id="e62a1-110">Channel</span></span>|<span data-ttu-id="e62a1-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="e62a1-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e62a1-112">Description</span><span class="sxs-lookup"><span data-stu-id="e62a1-112">Description</span></span>  
 <span data-ttu-id="e62a1-113">Indique qu'une activité a planifié la fin de la transaction runtime.</span><span class="sxs-lookup"><span data-stu-id="e62a1-113">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e62a1-114">Message</span><span class="sxs-lookup"><span data-stu-id="e62a1-114">Message</span></span>  
 <span data-ttu-id="e62a1-115">L'activité « %1 », DisplayName : « %2 », InstanceId : « %3 » a planifié la fin de la transaction runtime.</span><span class="sxs-lookup"><span data-stu-id="e62a1-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e62a1-116">Détails</span><span class="sxs-lookup"><span data-stu-id="e62a1-116">Details</span></span>  
  
|<span data-ttu-id="e62a1-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="e62a1-117">Data Item Name</span></span>|<span data-ttu-id="e62a1-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="e62a1-118">Data Item Type</span></span>|<span data-ttu-id="e62a1-119">Description</span><span class="sxs-lookup"><span data-stu-id="e62a1-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e62a1-120">Activité</span><span class="sxs-lookup"><span data-stu-id="e62a1-120">Activity</span></span>|<span data-ttu-id="e62a1-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="e62a1-121">xs:string</span></span>|<span data-ttu-id="e62a1-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="e62a1-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="e62a1-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="e62a1-123">DisplayName</span></span>|<span data-ttu-id="e62a1-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="e62a1-124">xs:string</span></span>|<span data-ttu-id="e62a1-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="e62a1-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="e62a1-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="e62a1-126">InstanceId</span></span>|<span data-ttu-id="e62a1-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="e62a1-127">xs:string</span></span>|<span data-ttu-id="e62a1-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="e62a1-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="e62a1-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e62a1-129">AppDomain</span></span>|<span data-ttu-id="e62a1-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="e62a1-130">xs:string</span></span>|<span data-ttu-id="e62a1-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e62a1-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
