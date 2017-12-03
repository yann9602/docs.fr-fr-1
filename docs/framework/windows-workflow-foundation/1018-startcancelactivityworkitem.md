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
ms.openlocfilehash: b64ea860e9881ed31aa0d8e78dec55f329cc6fad
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="1018---startcancelactivityworkitem"></a><span data-ttu-id="ccd98-102">1018 - StartCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="ccd98-102">1018 - StartCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="ccd98-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="ccd98-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ccd98-104">ID</span><span class="sxs-lookup"><span data-stu-id="ccd98-104">ID</span></span>|<span data-ttu-id="ccd98-105">1018</span><span class="sxs-lookup"><span data-stu-id="ccd98-105">1018</span></span>|  
|<span data-ttu-id="ccd98-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="ccd98-106">Keywords</span></span>|<span data-ttu-id="ccd98-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ccd98-107">WFRuntime</span></span>|  
|<span data-ttu-id="ccd98-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="ccd98-108">Level</span></span>|<span data-ttu-id="ccd98-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="ccd98-109">Verbose</span></span>|  
|<span data-ttu-id="ccd98-110">Canal</span><span class="sxs-lookup"><span data-stu-id="ccd98-110">Channel</span></span>|<span data-ttu-id="ccd98-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="ccd98-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ccd98-112">Description</span><span class="sxs-lookup"><span data-stu-id="ccd98-112">Description</span></span>  
 <span data-ttu-id="ccd98-113">Indique qu'un CancelActivityWorkItem démarre l'exécution.</span><span class="sxs-lookup"><span data-stu-id="ccd98-113">Indicates a CancelActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ccd98-114">Message</span><span class="sxs-lookup"><span data-stu-id="ccd98-114">Message</span></span>  
 <span data-ttu-id="ccd98-115">Début de l'exécution d'un CancelActivityWorkItem pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="ccd98-115">Starting execution of a CancelActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ccd98-116">Détails</span><span class="sxs-lookup"><span data-stu-id="ccd98-116">Details</span></span>  
  
|<span data-ttu-id="ccd98-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="ccd98-117">Data Item Name</span></span>|<span data-ttu-id="ccd98-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="ccd98-118">Data Item Type</span></span>|<span data-ttu-id="ccd98-119">Description</span><span class="sxs-lookup"><span data-stu-id="ccd98-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ccd98-120">Activité</span><span class="sxs-lookup"><span data-stu-id="ccd98-120">Activity</span></span>|<span data-ttu-id="ccd98-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="ccd98-121">xs:string</span></span>|<span data-ttu-id="ccd98-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="ccd98-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="ccd98-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="ccd98-123">DisplayName</span></span>|<span data-ttu-id="ccd98-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="ccd98-124">xs:string</span></span>|<span data-ttu-id="ccd98-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="ccd98-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="ccd98-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="ccd98-126">InstanceId</span></span>|<span data-ttu-id="ccd98-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="ccd98-127">xs:string</span></span>|<span data-ttu-id="ccd98-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="ccd98-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="ccd98-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ccd98-129">AppDomain</span></span>|<span data-ttu-id="ccd98-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="ccd98-130">xs:string</span></span>|<span data-ttu-id="ccd98-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ccd98-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
