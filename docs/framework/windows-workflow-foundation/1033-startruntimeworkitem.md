---
title: 1033 - StartRuntimeWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 172b5346-9f3b-46ae-bc06-39872022376a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: df5502c3d2cb1e9ec9454ed43c3a468a27307d07
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="1033---startruntimeworkitem"></a><span data-ttu-id="63549-102">1033 - StartRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="63549-102">1033 - StartRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="63549-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="63549-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="63549-104">ID</span><span class="sxs-lookup"><span data-stu-id="63549-104">ID</span></span>|<span data-ttu-id="63549-105">1033</span><span class="sxs-lookup"><span data-stu-id="63549-105">1033</span></span>|  
|<span data-ttu-id="63549-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="63549-106">Keywords</span></span>|<span data-ttu-id="63549-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="63549-107">WFRuntime</span></span>|  
|<span data-ttu-id="63549-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="63549-108">Level</span></span>|<span data-ttu-id="63549-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="63549-109">Verbose</span></span>|  
|<span data-ttu-id="63549-110">Canal</span><span class="sxs-lookup"><span data-stu-id="63549-110">Channel</span></span>|<span data-ttu-id="63549-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="63549-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="63549-112">Description</span><span class="sxs-lookup"><span data-stu-id="63549-112">Description</span></span>  
 <span data-ttu-id="63549-113">Indique qu'un RuntimeWorkItem démarre l'exécution.</span><span class="sxs-lookup"><span data-stu-id="63549-113">Indicates a RuntimeWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="63549-114">Message</span><span class="sxs-lookup"><span data-stu-id="63549-114">Message</span></span>  
 <span data-ttu-id="63549-115">Début de l'exécution d'un élément de travail runtime pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="63549-115">Starting execution of a runtime work item for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="63549-116">Détails</span><span class="sxs-lookup"><span data-stu-id="63549-116">Details</span></span>  
  
|<span data-ttu-id="63549-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="63549-117">Data Item Name</span></span>|<span data-ttu-id="63549-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="63549-118">Data Item Type</span></span>|<span data-ttu-id="63549-119">Description</span><span class="sxs-lookup"><span data-stu-id="63549-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="63549-120">Activité</span><span class="sxs-lookup"><span data-stu-id="63549-120">Activity</span></span>|<span data-ttu-id="63549-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="63549-121">xs:string</span></span>|<span data-ttu-id="63549-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="63549-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="63549-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="63549-123">DisplayName</span></span>|<span data-ttu-id="63549-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="63549-124">xs:string</span></span>|<span data-ttu-id="63549-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="63549-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="63549-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="63549-126">InstanceId</span></span>|<span data-ttu-id="63549-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="63549-127">xs:string</span></span>|<span data-ttu-id="63549-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="63549-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="63549-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="63549-129">AppDomain</span></span>|<span data-ttu-id="63549-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="63549-130">xs:string</span></span>|<span data-ttu-id="63549-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="63549-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
