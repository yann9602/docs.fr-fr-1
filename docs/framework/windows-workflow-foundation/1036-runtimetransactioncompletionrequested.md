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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 91fcac0bdfe885051941d100f1a2c131c547f19e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="5c425-102">1036 - RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="5c425-102">1036 - RuntimeTransactionCompletionRequested</span></span>
## <a name="properties"></a><span data-ttu-id="5c425-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="5c425-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5c425-104">ID</span><span class="sxs-lookup"><span data-stu-id="5c425-104">ID</span></span>|<span data-ttu-id="5c425-105">1036</span><span class="sxs-lookup"><span data-stu-id="5c425-105">1036</span></span>|  
|<span data-ttu-id="5c425-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="5c425-106">Keywords</span></span>|<span data-ttu-id="5c425-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="5c425-107">WFRuntime</span></span>|  
|<span data-ttu-id="5c425-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="5c425-108">Level</span></span>|<span data-ttu-id="5c425-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="5c425-109">Verbose</span></span>|  
|<span data-ttu-id="5c425-110">Canal</span><span class="sxs-lookup"><span data-stu-id="5c425-110">Channel</span></span>|<span data-ttu-id="5c425-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="5c425-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5c425-112">Description</span><span class="sxs-lookup"><span data-stu-id="5c425-112">Description</span></span>  
 <span data-ttu-id="5c425-113">Indique qu'une activité a planifié la fin de la transaction runtime.</span><span class="sxs-lookup"><span data-stu-id="5c425-113">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5c425-114">Message</span><span class="sxs-lookup"><span data-stu-id="5c425-114">Message</span></span>  
 <span data-ttu-id="5c425-115">L'activité « %1 », DisplayName : « %2 », InstanceId : « %3 » a planifié la fin de la transaction runtime.</span><span class="sxs-lookup"><span data-stu-id="5c425-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5c425-116">Détails</span><span class="sxs-lookup"><span data-stu-id="5c425-116">Details</span></span>  
  
|<span data-ttu-id="5c425-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="5c425-117">Data Item Name</span></span>|<span data-ttu-id="5c425-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="5c425-118">Data Item Type</span></span>|<span data-ttu-id="5c425-119">Description</span><span class="sxs-lookup"><span data-stu-id="5c425-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5c425-120">Activité</span><span class="sxs-lookup"><span data-stu-id="5c425-120">Activity</span></span>|<span data-ttu-id="5c425-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="5c425-121">xs:string</span></span>|<span data-ttu-id="5c425-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="5c425-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="5c425-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="5c425-123">DisplayName</span></span>|<span data-ttu-id="5c425-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="5c425-124">xs:string</span></span>|<span data-ttu-id="5c425-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="5c425-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="5c425-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="5c425-126">InstanceId</span></span>|<span data-ttu-id="5c425-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="5c425-127">xs:string</span></span>|<span data-ttu-id="5c425-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="5c425-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="5c425-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5c425-129">AppDomain</span></span>|<span data-ttu-id="5c425-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="5c425-130">xs:string</span></span>|<span data-ttu-id="5c425-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="5c425-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
