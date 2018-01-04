---
title: 39458 - TrackingRecordTruncated
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d12549d201ac621361bd6a517df6c6b53ab7aec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="39458---trackingrecordtruncated"></a><span data-ttu-id="2a597-102">39458 - TrackingRecordTruncated</span><span class="sxs-lookup"><span data-stu-id="2a597-102">39458 - TrackingRecordTruncated</span></span>
## <a name="properties"></a><span data-ttu-id="2a597-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="2a597-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2a597-104">ID</span><span class="sxs-lookup"><span data-stu-id="2a597-104">ID</span></span>|<span data-ttu-id="2a597-105">39458</span><span class="sxs-lookup"><span data-stu-id="2a597-105">39458</span></span>|  
|<span data-ttu-id="2a597-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="2a597-106">Keywords</span></span>|<span data-ttu-id="2a597-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="2a597-107">WFTracking</span></span>|  
|<span data-ttu-id="2a597-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="2a597-108">Level</span></span>|<span data-ttu-id="2a597-109">Avertissement</span><span class="sxs-lookup"><span data-stu-id="2a597-109">Warning</span></span>|  
|<span data-ttu-id="2a597-110">Canal</span><span class="sxs-lookup"><span data-stu-id="2a597-110">Channel</span></span>|<span data-ttu-id="2a597-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="2a597-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2a597-112">Description</span><span class="sxs-lookup"><span data-stu-id="2a597-112">Description</span></span>  
 <span data-ttu-id="2a597-113">Indique qu'un enregistrement de suivi a été tronqué.</span><span class="sxs-lookup"><span data-stu-id="2a597-113">Indicates a tracking record has been truncated.</span></span> <span data-ttu-id="2a597-114">Les données de variables/annotations/utilisateur ont été supprimées.</span><span class="sxs-lookup"><span data-stu-id="2a597-114">Variables/annotations/user data have been removed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2a597-115">Message</span><span class="sxs-lookup"><span data-stu-id="2a597-115">Message</span></span>  
 <span data-ttu-id="2a597-116">Enregistrement de suivi %1 tronqué écrit dans la session ETW avec le fournisseur %2.</span><span class="sxs-lookup"><span data-stu-id="2a597-116">Truncated tracking record %1 written to ETW session with provider %2.</span></span> <span data-ttu-id="2a597-117">Les données de variables/annotations/utilisateur ont été supprimées</span><span class="sxs-lookup"><span data-stu-id="2a597-117">Variables/annotations/user data have been removed</span></span>  
  
## <a name="details"></a><span data-ttu-id="2a597-118">Détails</span><span class="sxs-lookup"><span data-stu-id="2a597-118">Details</span></span>  
  
|<span data-ttu-id="2a597-119">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="2a597-119">Data Item Name</span></span>|<span data-ttu-id="2a597-120">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="2a597-120">Data Item Type</span></span>|<span data-ttu-id="2a597-121">Description</span><span class="sxs-lookup"><span data-stu-id="2a597-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2a597-122">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="2a597-122">RecordNumber</span></span>|<span data-ttu-id="2a597-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="2a597-123">xs:string</span></span>|<span data-ttu-id="2a597-124">Numéro d'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="2a597-124">The tracking record number.</span></span>|  
|<span data-ttu-id="2a597-125">ProviderId</span><span class="sxs-lookup"><span data-stu-id="2a597-125">ProviderId</span></span>|<span data-ttu-id="2a597-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="2a597-126">xs:string</span></span>|<span data-ttu-id="2a597-127">ID du fournisseur ETW.</span><span class="sxs-lookup"><span data-stu-id="2a597-127">The ETW provider id.</span></span>|  
|<span data-ttu-id="2a597-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2a597-128">AppDomain</span></span>|<span data-ttu-id="2a597-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="2a597-129">xs:string</span></span>|<span data-ttu-id="2a597-130">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2a597-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
