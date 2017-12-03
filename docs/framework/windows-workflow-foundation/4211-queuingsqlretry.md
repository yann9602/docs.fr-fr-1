---
title: 4211 - QueuingSqlRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df569f88-c86b-4503-840d-1399b67f4df7
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 349a91f5b4708d829aee8d7f055871ac7dcc8914
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="917fe-102">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="917fe-102">4211 - QueuingSqlRetry</span></span>
## <a name="properties"></a><span data-ttu-id="917fe-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="917fe-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="917fe-104">ID</span><span class="sxs-lookup"><span data-stu-id="917fe-104">ID</span></span>|<span data-ttu-id="917fe-105">4211</span><span class="sxs-lookup"><span data-stu-id="917fe-105">4211</span></span>|  
|<span data-ttu-id="917fe-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="917fe-106">Keywords</span></span>|<span data-ttu-id="917fe-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="917fe-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="917fe-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="917fe-108">Level</span></span>|<span data-ttu-id="917fe-109">Avertissement</span><span class="sxs-lookup"><span data-stu-id="917fe-109">Warning</span></span>|  
|<span data-ttu-id="917fe-110">Canal</span><span class="sxs-lookup"><span data-stu-id="917fe-110">Channel</span></span>|<span data-ttu-id="917fe-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="917fe-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="917fe-112">Description</span><span class="sxs-lookup"><span data-stu-id="917fe-112">Description</span></span>  
 <span data-ttu-id="917fe-113">Indique une nouvelle tentative de mise en file d'attente SQL.</span><span class="sxs-lookup"><span data-stu-id="917fe-113">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="917fe-114">Message</span><span class="sxs-lookup"><span data-stu-id="917fe-114">Message</span></span>  
 <span data-ttu-id="917fe-115">Mise en file d'attente d'une tentative SQL avec un retard de %1 millisecondes.</span><span class="sxs-lookup"><span data-stu-id="917fe-115">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="917fe-116">Détails</span><span class="sxs-lookup"><span data-stu-id="917fe-116">Details</span></span>  
  
|<span data-ttu-id="917fe-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="917fe-117">Data Item Name</span></span>|<span data-ttu-id="917fe-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="917fe-118">Data Item Type</span></span>|<span data-ttu-id="917fe-119">Description</span><span class="sxs-lookup"><span data-stu-id="917fe-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="917fe-120">Delay</span><span class="sxs-lookup"><span data-stu-id="917fe-120">Delay</span></span>|<span data-ttu-id="917fe-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="917fe-121">xs:string</span></span>|<span data-ttu-id="917fe-122">Délai entre les tentatives.</span><span class="sxs-lookup"><span data-stu-id="917fe-122">The delay between retries.</span></span>|  
|<span data-ttu-id="917fe-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="917fe-123">AppDomain</span></span>|<span data-ttu-id="917fe-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="917fe-124">xs:string</span></span>|<span data-ttu-id="917fe-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="917fe-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
