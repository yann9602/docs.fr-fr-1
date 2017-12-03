---
title: 1013 - CompleteExecuteActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31fc57b3-ef2f-48f0-a5de-b4e2c5c9ded7
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: de9add3f537c1d8ff97c92892197598bcc7a4fe7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="1013---completeexecuteactivityworkitem"></a><span data-ttu-id="b658f-102">1013 - CompleteExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="b658f-102">1013 - CompleteExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="b658f-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="b658f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b658f-104">ID</span><span class="sxs-lookup"><span data-stu-id="b658f-104">ID</span></span>|<span data-ttu-id="b658f-105">1013</span><span class="sxs-lookup"><span data-stu-id="b658f-105">1013</span></span>|  
|<span data-ttu-id="b658f-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="b658f-106">Keywords</span></span>|<span data-ttu-id="b658f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b658f-107">WFRuntime</span></span>|  
|<span data-ttu-id="b658f-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="b658f-108">Level</span></span>|<span data-ttu-id="b658f-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="b658f-109">Verbose</span></span>|  
|<span data-ttu-id="b658f-110">Canal</span><span class="sxs-lookup"><span data-stu-id="b658f-110">Channel</span></span>|<span data-ttu-id="b658f-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="b658f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b658f-112">Description</span><span class="sxs-lookup"><span data-stu-id="b658f-112">Description</span></span>  
 <span data-ttu-id="b658f-113">Indique qu'un ExecuteActivityWorkItem est terminé.</span><span class="sxs-lookup"><span data-stu-id="b658f-113">Indicates an ExecuteActivityWorkItem has completed</span></span>  
  
## <a name="message"></a><span data-ttu-id="b658f-114">Message</span><span class="sxs-lookup"><span data-stu-id="b658f-114">Message</span></span>  
 <span data-ttu-id="b658f-115">ExecuteActivityWorkItem est terminé pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="b658f-115">An ExecuteActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b658f-116">Détails</span><span class="sxs-lookup"><span data-stu-id="b658f-116">Details</span></span>  
  
|<span data-ttu-id="b658f-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="b658f-117">Data Item Name</span></span>|<span data-ttu-id="b658f-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="b658f-118">Data Item Type</span></span>|<span data-ttu-id="b658f-119">Description</span><span class="sxs-lookup"><span data-stu-id="b658f-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b658f-120">Activité</span><span class="sxs-lookup"><span data-stu-id="b658f-120">Activity</span></span>|<span data-ttu-id="b658f-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="b658f-121">xs:string</span></span>|<span data-ttu-id="b658f-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="b658f-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="b658f-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="b658f-123">DisplayName</span></span>|<span data-ttu-id="b658f-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="b658f-124">xs:string</span></span>|<span data-ttu-id="b658f-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="b658f-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="b658f-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="b658f-126">InstanceId</span></span>|<span data-ttu-id="b658f-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="b658f-127">xs:string</span></span>|<span data-ttu-id="b658f-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="b658f-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="b658f-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b658f-129">AppDomain</span></span>|<span data-ttu-id="b658f-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="b658f-130">xs:string</span></span>|<span data-ttu-id="b658f-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b658f-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
