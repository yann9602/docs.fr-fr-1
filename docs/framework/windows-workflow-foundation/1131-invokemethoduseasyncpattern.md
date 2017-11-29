---
title: 1131 - InvokeMethodUseAsyncPattern
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eca50fa7-5276-4759-ad1c-e490b9bd1f82
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6f9f8f4e836d5c5b437edcfaff6460c7b97210ce
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1131---invokemethoduseasyncpattern"></a><span data-ttu-id="02073-102">1131 - InvokeMethodUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="02073-102">1131 - InvokeMethodUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="02073-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="02073-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="02073-104">ID</span><span class="sxs-lookup"><span data-stu-id="02073-104">ID</span></span>|<span data-ttu-id="02073-105">1131</span><span class="sxs-lookup"><span data-stu-id="02073-105">1131</span></span>|  
|<span data-ttu-id="02073-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="02073-106">Keywords</span></span>|<span data-ttu-id="02073-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="02073-107">WFRuntime</span></span>|  
|<span data-ttu-id="02073-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="02073-108">Level</span></span>|<span data-ttu-id="02073-109">Information</span><span class="sxs-lookup"><span data-stu-id="02073-109">Information</span></span>|  
|<span data-ttu-id="02073-110">Canal</span><span class="sxs-lookup"><span data-stu-id="02073-110">Channel</span></span>|<span data-ttu-id="02073-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="02073-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="02073-112">Description</span><span class="sxs-lookup"><span data-stu-id="02073-112">Description</span></span>  
 <span data-ttu-id="02073-113">Pendant l'étape CacheMetadata, l'activité InvokeMethod indique qu'elle utilise le modèle asynchrone lors de l'appel de la méthode.</span><span class="sxs-lookup"><span data-stu-id="02073-113">During CacheMetadata step, InvokeMethod activity indicates that it is using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="02073-114">Message</span><span class="sxs-lookup"><span data-stu-id="02073-114">Message</span></span>  
 <span data-ttu-id="02073-115">InvokeMethod « %1 » - la méthode utilise un modèle asynchrone de « %2 » et « %3 ».</span><span class="sxs-lookup"><span data-stu-id="02073-115">InvokeMethod '%1' - method uses asynchronous pattern of '%2' and '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="02073-116">Détails</span><span class="sxs-lookup"><span data-stu-id="02073-116">Details</span></span>  
  
|<span data-ttu-id="02073-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="02073-117">Data Item Name</span></span>|<span data-ttu-id="02073-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="02073-118">Data Item Type</span></span>|<span data-ttu-id="02073-119">Description</span><span class="sxs-lookup"><span data-stu-id="02073-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="02073-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="02073-120">InvokeMethod</span></span>|<span data-ttu-id="02073-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="02073-121">xs:string</span></span>|<span data-ttu-id="02073-122">Nom complet de l'activité InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="02073-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="02073-123">BeginMethod</span><span class="sxs-lookup"><span data-stu-id="02073-123">BeginMethod</span></span>|<span data-ttu-id="02073-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="02073-124">xs:string</span></span>|<span data-ttu-id="02073-125">Nom de la méthode Begin.</span><span class="sxs-lookup"><span data-stu-id="02073-125">The name of the begin method.</span></span>|  
|<span data-ttu-id="02073-126">EndMethod</span><span class="sxs-lookup"><span data-stu-id="02073-126">EndMethod</span></span>|<span data-ttu-id="02073-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="02073-127">xs:string</span></span>|<span data-ttu-id="02073-128">Nom de la méthode End.</span><span class="sxs-lookup"><span data-stu-id="02073-128">The name of the end method.</span></span>|  
|<span data-ttu-id="02073-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="02073-129">AppDomain</span></span>|<span data-ttu-id="02073-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="02073-130">xs:string</span></span>|<span data-ttu-id="02073-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="02073-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
