---
title: 4212 - LockRetryTimeout
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4ad415a-9871-49fc-85b8-8ee2ea149b1d
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 897e6ef8b739654a61058106966c870c47f8129a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="4212---lockretrytimeout"></a><span data-ttu-id="15595-102">4212 - LockRetryTimeout</span><span class="sxs-lookup"><span data-stu-id="15595-102">4212 - LockRetryTimeout</span></span>
## <a name="properties"></a><span data-ttu-id="15595-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="15595-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="15595-104">ID</span><span class="sxs-lookup"><span data-stu-id="15595-104">ID</span></span>|<span data-ttu-id="15595-105">4212</span><span class="sxs-lookup"><span data-stu-id="15595-105">4212</span></span>|  
|<span data-ttu-id="15595-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="15595-106">Keywords</span></span>|<span data-ttu-id="15595-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="15595-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="15595-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="15595-108">Level</span></span>|<span data-ttu-id="15595-109">Avertissement</span><span class="sxs-lookup"><span data-stu-id="15595-109">Warning</span></span>|  
|<span data-ttu-id="15595-110">Canal</span><span class="sxs-lookup"><span data-stu-id="15595-110">Channel</span></span>|<span data-ttu-id="15595-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="15595-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="15595-112">Description</span><span class="sxs-lookup"><span data-stu-id="15595-112">Description</span></span>  
 <span data-ttu-id="15595-113">Le fournisseur SQL a rencontré une expiration du délai d'attente lors de la tentative d'acquisition du verrou d'instance.</span><span class="sxs-lookup"><span data-stu-id="15595-113">SQL provider encountered a timeout trying to acquire the instance lock.</span></span>  
  
## <a name="message"></a><span data-ttu-id="15595-114">Message</span><span class="sxs-lookup"><span data-stu-id="15595-114">Message</span></span>  
 <span data-ttu-id="15595-115">Délai de la tentative d’acquisition du verrou d’instance.</span><span class="sxs-lookup"><span data-stu-id="15595-115">Timeout trying to acquire the instance lock.</span></span>  <span data-ttu-id="15595-116">L'opération ne s'est pas terminée dans le délai imparti de %1.</span><span class="sxs-lookup"><span data-stu-id="15595-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="15595-117">Le temps alloué à cette opération peut avoir été une partie d'un délai d'expiration plus long.</span><span class="sxs-lookup"><span data-stu-id="15595-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="15595-118">Détails</span><span class="sxs-lookup"><span data-stu-id="15595-118">Details</span></span>  
  
|<span data-ttu-id="15595-119">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="15595-119">Data Item Name</span></span>|<span data-ttu-id="15595-120">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="15595-120">Data Item Type</span></span>|<span data-ttu-id="15595-121">Description</span><span class="sxs-lookup"><span data-stu-id="15595-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="15595-122">Delay</span><span class="sxs-lookup"><span data-stu-id="15595-122">Delay</span></span>|<span data-ttu-id="15595-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="15595-123">xs:string</span></span>|<span data-ttu-id="15595-124">Délai entre les tentatives.</span><span class="sxs-lookup"><span data-stu-id="15595-124">The delay between retries.</span></span>|  
|<span data-ttu-id="15595-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="15595-125">AppDomain</span></span>|<span data-ttu-id="15595-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="15595-126">xs:string</span></span>|<span data-ttu-id="15595-127">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="15595-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
