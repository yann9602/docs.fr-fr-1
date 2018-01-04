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
ms.workload: dotnet
ms.openlocfilehash: 378f756003e45905e3697e2e9470aa1e582a2ad6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="1019---completecancelactivityworkitem"></a><span data-ttu-id="9774b-102">1019 - CompleteCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="9774b-102">1019 - CompleteCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="9774b-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="9774b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9774b-104">ID</span><span class="sxs-lookup"><span data-stu-id="9774b-104">ID</span></span>|<span data-ttu-id="9774b-105">1019</span><span class="sxs-lookup"><span data-stu-id="9774b-105">1019</span></span>|  
|<span data-ttu-id="9774b-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="9774b-106">Keywords</span></span>|<span data-ttu-id="9774b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9774b-107">WFRuntime</span></span>|  
|<span data-ttu-id="9774b-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="9774b-108">Level</span></span>|<span data-ttu-id="9774b-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="9774b-109">Verbose</span></span>|  
|<span data-ttu-id="9774b-110">Canal</span><span class="sxs-lookup"><span data-stu-id="9774b-110">Channel</span></span>|<span data-ttu-id="9774b-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="9774b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9774b-112">Description</span><span class="sxs-lookup"><span data-stu-id="9774b-112">Description</span></span>  
 <span data-ttu-id="9774b-113">Indique qu'un CancelActivityWorkItem est terminé.</span><span class="sxs-lookup"><span data-stu-id="9774b-113">Indicates a CancelActivityWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9774b-114">Message</span><span class="sxs-lookup"><span data-stu-id="9774b-114">Message</span></span>  
 <span data-ttu-id="9774b-115">CancelActivityWorkItem est terminé pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="9774b-115">A CancelActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9774b-116">Détails</span><span class="sxs-lookup"><span data-stu-id="9774b-116">Details</span></span>  
  
|<span data-ttu-id="9774b-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="9774b-117">Data Item Name</span></span>|<span data-ttu-id="9774b-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="9774b-118">Data Item Type</span></span>|<span data-ttu-id="9774b-119">Description</span><span class="sxs-lookup"><span data-stu-id="9774b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9774b-120">Activité</span><span class="sxs-lookup"><span data-stu-id="9774b-120">Activity</span></span>|<span data-ttu-id="9774b-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="9774b-121">xs:string</span></span>|<span data-ttu-id="9774b-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="9774b-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="9774b-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="9774b-123">DisplayName</span></span>|<span data-ttu-id="9774b-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="9774b-124">xs:string</span></span>|<span data-ttu-id="9774b-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="9774b-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="9774b-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="9774b-126">InstanceId</span></span>|<span data-ttu-id="9774b-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="9774b-127">xs:string</span></span>|<span data-ttu-id="9774b-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="9774b-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="9774b-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9774b-129">AppDomain</span></span>|<span data-ttu-id="9774b-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="9774b-130">xs:string</span></span>|<span data-ttu-id="9774b-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9774b-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
