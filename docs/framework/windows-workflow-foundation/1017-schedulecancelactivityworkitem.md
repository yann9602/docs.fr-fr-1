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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c6d348ec18b4d5eff7156d1e9809eb793ac1681d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1017---schedulecancelactivityworkitem"></a><span data-ttu-id="8828d-102">1017 - ScheduleCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="8828d-102">1017 - ScheduleCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="8828d-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="8828d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8828d-104">ID</span><span class="sxs-lookup"><span data-stu-id="8828d-104">ID</span></span>|<span data-ttu-id="8828d-105">1017</span><span class="sxs-lookup"><span data-stu-id="8828d-105">1017</span></span>|  
|<span data-ttu-id="8828d-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="8828d-106">Keywords</span></span>|<span data-ttu-id="8828d-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="8828d-107">WFRuntime</span></span>|  
|<span data-ttu-id="8828d-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="8828d-108">Level</span></span>|<span data-ttu-id="8828d-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="8828d-109">Verbose</span></span>|  
|<span data-ttu-id="8828d-110">Canal</span><span class="sxs-lookup"><span data-stu-id="8828d-110">Channel</span></span>|<span data-ttu-id="8828d-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="8828d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8828d-112">Description</span><span class="sxs-lookup"><span data-stu-id="8828d-112">Description</span></span>  
 <span data-ttu-id="8828d-113">Indique qu'un CancelActivityWorkItem a été planifié.</span><span class="sxs-lookup"><span data-stu-id="8828d-113">Indicates a CancelActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8828d-114">Message</span><span class="sxs-lookup"><span data-stu-id="8828d-114">Message</span></span>  
 <span data-ttu-id="8828d-115">CancelActivityWorkItem a été planifié pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="8828d-115">A CancelActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8828d-116">Détails</span><span class="sxs-lookup"><span data-stu-id="8828d-116">Details</span></span>  
  
|<span data-ttu-id="8828d-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="8828d-117">Data Item Name</span></span>|<span data-ttu-id="8828d-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="8828d-118">Data Item Type</span></span>|<span data-ttu-id="8828d-119">Description</span><span class="sxs-lookup"><span data-stu-id="8828d-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8828d-120">Activité</span><span class="sxs-lookup"><span data-stu-id="8828d-120">Activity</span></span>|<span data-ttu-id="8828d-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="8828d-121">xs:string</span></span>|<span data-ttu-id="8828d-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="8828d-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="8828d-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="8828d-123">DisplayName</span></span>|<span data-ttu-id="8828d-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="8828d-124">xs:string</span></span>|<span data-ttu-id="8828d-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="8828d-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="8828d-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="8828d-126">InstanceId</span></span>|<span data-ttu-id="8828d-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="8828d-127">xs:string</span></span>|<span data-ttu-id="8828d-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="8828d-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="8828d-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8828d-129">AppDomain</span></span>|<span data-ttu-id="8828d-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="8828d-130">xs:string</span></span>|<span data-ttu-id="8828d-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="8828d-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
