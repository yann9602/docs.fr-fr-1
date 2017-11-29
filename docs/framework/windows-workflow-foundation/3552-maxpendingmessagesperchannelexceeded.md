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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5ba5e4aa8e1338321838e40db7d976107315ef64
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a><span data-ttu-id="2242d-102">3552 - MaxPendingMessagesPerChannelExceeded</span><span class="sxs-lookup"><span data-stu-id="2242d-102">3552 - MaxPendingMessagesPerChannelExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="2242d-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="2242d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2242d-104">ID</span><span class="sxs-lookup"><span data-stu-id="2242d-104">ID</span></span>|<span data-ttu-id="2242d-105">3552</span><span class="sxs-lookup"><span data-stu-id="2242d-105">3552</span></span>|  
|<span data-ttu-id="2242d-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="2242d-106">Keywords</span></span>|<span data-ttu-id="2242d-107">Quota, WFServices</span><span class="sxs-lookup"><span data-stu-id="2242d-107">Quota, WFServices</span></span>|  
|<span data-ttu-id="2242d-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="2242d-108">Level</span></span>|<span data-ttu-id="2242d-109">Avertissement</span><span class="sxs-lookup"><span data-stu-id="2242d-109">Warning</span></span>|  
|<span data-ttu-id="2242d-110">Canal</span><span class="sxs-lookup"><span data-stu-id="2242d-110">Channel</span></span>|<span data-ttu-id="2242d-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="2242d-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2242d-112">Description</span><span class="sxs-lookup"><span data-stu-id="2242d-112">Description</span></span>  
 <span data-ttu-id="2242d-113">Indique que la limitation « MaxPendingMessagesPerChannel » a été atteinte.</span><span class="sxs-lookup"><span data-stu-id="2242d-113">Indicates the throttle 'MaxPendingMessagesPerChannel' limit was hit.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2242d-114">Message</span><span class="sxs-lookup"><span data-stu-id="2242d-114">Message</span></span>  
 <span data-ttu-id="2242d-115">La limitation ' maxpendingmessagesperchannel ' de '%1' a été atteinte.</span><span class="sxs-lookup"><span data-stu-id="2242d-115">The throttle 'MaxPendingMessagesPerChannel' limit of  '%1' was hit.</span></span> <span data-ttu-id="2242d-116">Pour accroître cette limite, modifiez la propriété MaxPendingMessagesPerChannel sur BufferedReceiveServiceBehavior.</span><span class="sxs-lookup"><span data-stu-id="2242d-116">To increase this limit, adjust the MaxPendingMessagesPerChannel property on BufferedReceiveServiceBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2242d-117">Détails</span><span class="sxs-lookup"><span data-stu-id="2242d-117">Details</span></span>  
  
|<span data-ttu-id="2242d-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="2242d-118">Data Item Name</span></span>|<span data-ttu-id="2242d-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="2242d-119">Data Item Type</span></span>|<span data-ttu-id="2242d-120">Description</span><span class="sxs-lookup"><span data-stu-id="2242d-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2242d-121">Limitation</span><span class="sxs-lookup"><span data-stu-id="2242d-121">Limit</span></span>|<span data-ttu-id="2242d-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="2242d-122">xs:string</span></span>|<span data-ttu-id="2242d-123">La limite de MaxPendingMessagesPerChannel.</span><span class="sxs-lookup"><span data-stu-id="2242d-123">The limit of the MaxPendingMessagesPerChannel throttle.</span></span>|  
|<span data-ttu-id="2242d-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2242d-124">AppDomain</span></span>|<span data-ttu-id="2242d-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="2242d-125">xs:string</span></span>|<span data-ttu-id="2242d-126">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2242d-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
