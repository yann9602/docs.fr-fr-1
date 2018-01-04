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
ms.workload: dotnet
ms.openlocfilehash: 1ffd44cf9d2333b22e3be809d05f2fa8c33d4cac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="a7e3e-102">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="a7e3e-102">4211 - QueuingSqlRetry</span></span>
## <a name="properties"></a><span data-ttu-id="a7e3e-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="a7e3e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a7e3e-104">ID</span><span class="sxs-lookup"><span data-stu-id="a7e3e-104">ID</span></span>|<span data-ttu-id="a7e3e-105">4211</span><span class="sxs-lookup"><span data-stu-id="a7e3e-105">4211</span></span>|  
|<span data-ttu-id="a7e3e-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="a7e3e-106">Keywords</span></span>|<span data-ttu-id="a7e3e-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="a7e3e-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="a7e3e-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="a7e3e-108">Level</span></span>|<span data-ttu-id="a7e3e-109">Avertissement</span><span class="sxs-lookup"><span data-stu-id="a7e3e-109">Warning</span></span>|  
|<span data-ttu-id="a7e3e-110">Canal</span><span class="sxs-lookup"><span data-stu-id="a7e3e-110">Channel</span></span>|<span data-ttu-id="a7e3e-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="a7e3e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a7e3e-112">Description</span><span class="sxs-lookup"><span data-stu-id="a7e3e-112">Description</span></span>  
 <span data-ttu-id="a7e3e-113">Indique une nouvelle tentative de mise en file d'attente SQL.</span><span class="sxs-lookup"><span data-stu-id="a7e3e-113">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a7e3e-114">Message</span><span class="sxs-lookup"><span data-stu-id="a7e3e-114">Message</span></span>  
 <span data-ttu-id="a7e3e-115">Mise en file d'attente d'une tentative SQL avec un retard de %1 millisecondes.</span><span class="sxs-lookup"><span data-stu-id="a7e3e-115">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a7e3e-116">Détails</span><span class="sxs-lookup"><span data-stu-id="a7e3e-116">Details</span></span>  
  
|<span data-ttu-id="a7e3e-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="a7e3e-117">Data Item Name</span></span>|<span data-ttu-id="a7e3e-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="a7e3e-118">Data Item Type</span></span>|<span data-ttu-id="a7e3e-119">Description</span><span class="sxs-lookup"><span data-stu-id="a7e3e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a7e3e-120">Delay</span><span class="sxs-lookup"><span data-stu-id="a7e3e-120">Delay</span></span>|<span data-ttu-id="a7e3e-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="a7e3e-121">xs:string</span></span>|<span data-ttu-id="a7e3e-122">Délai entre les tentatives.</span><span class="sxs-lookup"><span data-stu-id="a7e3e-122">The delay between retries.</span></span>|  
|<span data-ttu-id="a7e3e-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a7e3e-123">AppDomain</span></span>|<span data-ttu-id="a7e3e-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="a7e3e-124">xs:string</span></span>|<span data-ttu-id="a7e3e-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="a7e3e-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
