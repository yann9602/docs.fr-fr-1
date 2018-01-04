---
title: 1018 - StartCancelActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68b4fa1d-eee6-4a2a-8c16-7e9d89f08ab9
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d64d18474ff867ee5679e07c18a288f07185f60
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="1018---startcancelactivityworkitem"></a><span data-ttu-id="685b6-102">1018 - StartCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="685b6-102">1018 - StartCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="685b6-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="685b6-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="685b6-104">ID</span><span class="sxs-lookup"><span data-stu-id="685b6-104">ID</span></span>|<span data-ttu-id="685b6-105">1018</span><span class="sxs-lookup"><span data-stu-id="685b6-105">1018</span></span>|  
|<span data-ttu-id="685b6-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="685b6-106">Keywords</span></span>|<span data-ttu-id="685b6-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="685b6-107">WFRuntime</span></span>|  
|<span data-ttu-id="685b6-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="685b6-108">Level</span></span>|<span data-ttu-id="685b6-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="685b6-109">Verbose</span></span>|  
|<span data-ttu-id="685b6-110">Canal</span><span class="sxs-lookup"><span data-stu-id="685b6-110">Channel</span></span>|<span data-ttu-id="685b6-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="685b6-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="685b6-112">Description</span><span class="sxs-lookup"><span data-stu-id="685b6-112">Description</span></span>  
 <span data-ttu-id="685b6-113">Indique qu'un CancelActivityWorkItem démarre l'exécution.</span><span class="sxs-lookup"><span data-stu-id="685b6-113">Indicates a CancelActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="685b6-114">Message</span><span class="sxs-lookup"><span data-stu-id="685b6-114">Message</span></span>  
 <span data-ttu-id="685b6-115">Début de l'exécution d'un CancelActivityWorkItem pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="685b6-115">Starting execution of a CancelActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="685b6-116">Détails</span><span class="sxs-lookup"><span data-stu-id="685b6-116">Details</span></span>  
  
|<span data-ttu-id="685b6-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="685b6-117">Data Item Name</span></span>|<span data-ttu-id="685b6-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="685b6-118">Data Item Type</span></span>|<span data-ttu-id="685b6-119">Description</span><span class="sxs-lookup"><span data-stu-id="685b6-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="685b6-120">Activité</span><span class="sxs-lookup"><span data-stu-id="685b6-120">Activity</span></span>|<span data-ttu-id="685b6-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="685b6-121">xs:string</span></span>|<span data-ttu-id="685b6-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="685b6-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="685b6-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="685b6-123">DisplayName</span></span>|<span data-ttu-id="685b6-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="685b6-124">xs:string</span></span>|<span data-ttu-id="685b6-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="685b6-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="685b6-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="685b6-126">InstanceId</span></span>|<span data-ttu-id="685b6-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="685b6-127">xs:string</span></span>|<span data-ttu-id="685b6-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="685b6-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="685b6-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="685b6-129">AppDomain</span></span>|<span data-ttu-id="685b6-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="685b6-130">xs:string</span></span>|<span data-ttu-id="685b6-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="685b6-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
