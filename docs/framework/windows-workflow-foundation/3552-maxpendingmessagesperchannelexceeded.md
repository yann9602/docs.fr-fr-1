---
title: 3552 - MaxPendingMessagesPerChannelExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5455472a5b9ebdba7aea7d0384ce9cd4a9a2849d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a><span data-ttu-id="e8752-102">3552 - MaxPendingMessagesPerChannelExceeded</span><span class="sxs-lookup"><span data-stu-id="e8752-102">3552 - MaxPendingMessagesPerChannelExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="e8752-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="e8752-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e8752-104">ID</span><span class="sxs-lookup"><span data-stu-id="e8752-104">ID</span></span>|<span data-ttu-id="e8752-105">3552</span><span class="sxs-lookup"><span data-stu-id="e8752-105">3552</span></span>|  
|<span data-ttu-id="e8752-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="e8752-106">Keywords</span></span>|<span data-ttu-id="e8752-107">Quota, WFServices</span><span class="sxs-lookup"><span data-stu-id="e8752-107">Quota, WFServices</span></span>|  
|<span data-ttu-id="e8752-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="e8752-108">Level</span></span>|<span data-ttu-id="e8752-109">Avertissement</span><span class="sxs-lookup"><span data-stu-id="e8752-109">Warning</span></span>|  
|<span data-ttu-id="e8752-110">Canal</span><span class="sxs-lookup"><span data-stu-id="e8752-110">Channel</span></span>|<span data-ttu-id="e8752-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="e8752-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e8752-112">Description</span><span class="sxs-lookup"><span data-stu-id="e8752-112">Description</span></span>  
 <span data-ttu-id="e8752-113">Indique que la limitation « MaxPendingMessagesPerChannel » a été atteinte.</span><span class="sxs-lookup"><span data-stu-id="e8752-113">Indicates the throttle 'MaxPendingMessagesPerChannel' limit was hit.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e8752-114">Message</span><span class="sxs-lookup"><span data-stu-id="e8752-114">Message</span></span>  
 <span data-ttu-id="e8752-115">La limitation ' maxpendingmessagesperchannel ' de '%1' a été atteinte.</span><span class="sxs-lookup"><span data-stu-id="e8752-115">The throttle 'MaxPendingMessagesPerChannel' limit of  '%1' was hit.</span></span> <span data-ttu-id="e8752-116">Pour accroître cette limite, modifiez la propriété MaxPendingMessagesPerChannel sur BufferedReceiveServiceBehavior.</span><span class="sxs-lookup"><span data-stu-id="e8752-116">To increase this limit, adjust the MaxPendingMessagesPerChannel property on BufferedReceiveServiceBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e8752-117">Détails</span><span class="sxs-lookup"><span data-stu-id="e8752-117">Details</span></span>  
  
|<span data-ttu-id="e8752-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="e8752-118">Data Item Name</span></span>|<span data-ttu-id="e8752-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="e8752-119">Data Item Type</span></span>|<span data-ttu-id="e8752-120">Description</span><span class="sxs-lookup"><span data-stu-id="e8752-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e8752-121">Limitation</span><span class="sxs-lookup"><span data-stu-id="e8752-121">Limit</span></span>|<span data-ttu-id="e8752-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="e8752-122">xs:string</span></span>|<span data-ttu-id="e8752-123">La limite de MaxPendingMessagesPerChannel.</span><span class="sxs-lookup"><span data-stu-id="e8752-123">The limit of the MaxPendingMessagesPerChannel throttle.</span></span>|  
|<span data-ttu-id="e8752-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e8752-124">AppDomain</span></span>|<span data-ttu-id="e8752-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="e8752-125">xs:string</span></span>|<span data-ttu-id="e8752-126">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e8752-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
