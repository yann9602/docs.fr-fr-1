---
title: 1012 - StartExecuteActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29e9b1c6-c5d7-4b58-b59d-a06a923d3c80
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6a06cec1ab251b8f7e82aef71589bd56e5f55f2e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="1012---startexecuteactivityworkitem"></a><span data-ttu-id="3f234-102">1012 - StartExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="3f234-102">1012 - StartExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="3f234-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="3f234-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3f234-104">ID</span><span class="sxs-lookup"><span data-stu-id="3f234-104">ID</span></span>|<span data-ttu-id="3f234-105">1012</span><span class="sxs-lookup"><span data-stu-id="3f234-105">1012</span></span>|  
|<span data-ttu-id="3f234-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="3f234-106">Keywords</span></span>|<span data-ttu-id="3f234-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3f234-107">WFRuntime</span></span>|  
|<span data-ttu-id="3f234-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="3f234-108">Level</span></span>|<span data-ttu-id="3f234-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="3f234-109">Verbose</span></span>|  
|<span data-ttu-id="3f234-110">Canal</span><span class="sxs-lookup"><span data-stu-id="3f234-110">Channel</span></span>|<span data-ttu-id="3f234-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="3f234-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3f234-112">Description</span><span class="sxs-lookup"><span data-stu-id="3f234-112">Description</span></span>  
 <span data-ttu-id="3f234-113">Indique qu'un ExecuteActivityWorkItem démarre l'exécution.</span><span class="sxs-lookup"><span data-stu-id="3f234-113">Indicates an ExecuteActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3f234-114">Message</span><span class="sxs-lookup"><span data-stu-id="3f234-114">Message</span></span>  
 <span data-ttu-id="3f234-115">Début de l'exécution d'un ExecuteActivityWorkItem pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="3f234-115">Starting execution of an ExecuteActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3f234-116">Détails</span><span class="sxs-lookup"><span data-stu-id="3f234-116">Details</span></span>  
  
|<span data-ttu-id="3f234-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="3f234-117">Data Item Name</span></span>|<span data-ttu-id="3f234-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="3f234-118">Data Item Type</span></span>|<span data-ttu-id="3f234-119">Description</span><span class="sxs-lookup"><span data-stu-id="3f234-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3f234-120">Activité</span><span class="sxs-lookup"><span data-stu-id="3f234-120">Activity</span></span>|<span data-ttu-id="3f234-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="3f234-121">xs:string</span></span>|<span data-ttu-id="3f234-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="3f234-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="3f234-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="3f234-123">DisplayName</span></span>|<span data-ttu-id="3f234-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="3f234-124">xs:string</span></span>|<span data-ttu-id="3f234-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="3f234-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="3f234-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="3f234-126">InstanceId</span></span>|<span data-ttu-id="3f234-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="3f234-127">xs:string</span></span>|<span data-ttu-id="3f234-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="3f234-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="3f234-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3f234-129">AppDomain</span></span>|<span data-ttu-id="3f234-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="3f234-130">xs:string</span></span>|<span data-ttu-id="3f234-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="3f234-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
