---
title: 1017 - ScheduleCancelActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 864546ab-d65c-4989-8fcb-537ba03a3cdd
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a632d59ddd75b375ff5e828a9f35aeecb0118f1c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="1017---schedulecancelactivityworkitem"></a><span data-ttu-id="c34be-102">1017 - ScheduleCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="c34be-102">1017 - ScheduleCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="c34be-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="c34be-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c34be-104">ID</span><span class="sxs-lookup"><span data-stu-id="c34be-104">ID</span></span>|<span data-ttu-id="c34be-105">1017</span><span class="sxs-lookup"><span data-stu-id="c34be-105">1017</span></span>|  
|<span data-ttu-id="c34be-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="c34be-106">Keywords</span></span>|<span data-ttu-id="c34be-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c34be-107">WFRuntime</span></span>|  
|<span data-ttu-id="c34be-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="c34be-108">Level</span></span>|<span data-ttu-id="c34be-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="c34be-109">Verbose</span></span>|  
|<span data-ttu-id="c34be-110">Canal</span><span class="sxs-lookup"><span data-stu-id="c34be-110">Channel</span></span>|<span data-ttu-id="c34be-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="c34be-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c34be-112">Description</span><span class="sxs-lookup"><span data-stu-id="c34be-112">Description</span></span>  
 <span data-ttu-id="c34be-113">Indique qu'un CancelActivityWorkItem a été planifié.</span><span class="sxs-lookup"><span data-stu-id="c34be-113">Indicates a CancelActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c34be-114">Message</span><span class="sxs-lookup"><span data-stu-id="c34be-114">Message</span></span>  
 <span data-ttu-id="c34be-115">CancelActivityWorkItem a été planifié pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="c34be-115">A CancelActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c34be-116">Détails</span><span class="sxs-lookup"><span data-stu-id="c34be-116">Details</span></span>  
  
|<span data-ttu-id="c34be-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="c34be-117">Data Item Name</span></span>|<span data-ttu-id="c34be-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="c34be-118">Data Item Type</span></span>|<span data-ttu-id="c34be-119">Description</span><span class="sxs-lookup"><span data-stu-id="c34be-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c34be-120">Activité</span><span class="sxs-lookup"><span data-stu-id="c34be-120">Activity</span></span>|<span data-ttu-id="c34be-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="c34be-121">xs:string</span></span>|<span data-ttu-id="c34be-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="c34be-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="c34be-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="c34be-123">DisplayName</span></span>|<span data-ttu-id="c34be-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="c34be-124">xs:string</span></span>|<span data-ttu-id="c34be-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="c34be-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="c34be-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="c34be-126">InstanceId</span></span>|<span data-ttu-id="c34be-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="c34be-127">xs:string</span></span>|<span data-ttu-id="c34be-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="c34be-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="c34be-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c34be-129">AppDomain</span></span>|<span data-ttu-id="c34be-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="c34be-130">xs:string</span></span>|<span data-ttu-id="c34be-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c34be-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
