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
ms.openlocfilehash: 2cc905fbd960b3ed5c36cac40300ba58697f8903
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="1033---startruntimeworkitem"></a><span data-ttu-id="ae203-102">1033 - StartRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="ae203-102">1033 - StartRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="ae203-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="ae203-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ae203-104">ID</span><span class="sxs-lookup"><span data-stu-id="ae203-104">ID</span></span>|<span data-ttu-id="ae203-105">1036</span><span class="sxs-lookup"><span data-stu-id="ae203-105">1033</span></span>|  
|<span data-ttu-id="ae203-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="ae203-106">Keywords</span></span>|<span data-ttu-id="ae203-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ae203-107">WFRuntime</span></span>|  
|<span data-ttu-id="ae203-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="ae203-108">Level</span></span>|<span data-ttu-id="ae203-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="ae203-109">Verbose</span></span>|  
|<span data-ttu-id="ae203-110">Canal</span><span class="sxs-lookup"><span data-stu-id="ae203-110">Channel</span></span>|<span data-ttu-id="ae203-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="ae203-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ae203-112">Description</span><span class="sxs-lookup"><span data-stu-id="ae203-112">Description</span></span>  
 <span data-ttu-id="ae203-113">Indique qu'un RuntimeWorkItem démarre l'exécution.</span><span class="sxs-lookup"><span data-stu-id="ae203-113">Indicates a RuntimeWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ae203-114">Message</span><span class="sxs-lookup"><span data-stu-id="ae203-114">Message</span></span>  
 <span data-ttu-id="ae203-115">Début de l'exécution d'un élément de travail runtime pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="ae203-115">Starting execution of a runtime work item for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ae203-116">Détails</span><span class="sxs-lookup"><span data-stu-id="ae203-116">Details</span></span>  
  
|<span data-ttu-id="ae203-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="ae203-117">Data Item Name</span></span>|<span data-ttu-id="ae203-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="ae203-118">Data Item Type</span></span>|<span data-ttu-id="ae203-119">Description</span><span class="sxs-lookup"><span data-stu-id="ae203-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ae203-120">Activité</span><span class="sxs-lookup"><span data-stu-id="ae203-120">Activity</span></span>|<span data-ttu-id="ae203-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="ae203-121">xs:string</span></span>|<span data-ttu-id="ae203-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="ae203-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="ae203-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="ae203-123">DisplayName</span></span>|<span data-ttu-id="ae203-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="ae203-124">xs:string</span></span>|<span data-ttu-id="ae203-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="ae203-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="ae203-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="ae203-126">InstanceId</span></span>|<span data-ttu-id="ae203-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="ae203-127">xs:string</span></span>|<span data-ttu-id="ae203-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="ae203-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="ae203-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ae203-129">AppDomain</span></span>|<span data-ttu-id="ae203-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="ae203-130">xs:string</span></span>|<span data-ttu-id="ae203-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ae203-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
