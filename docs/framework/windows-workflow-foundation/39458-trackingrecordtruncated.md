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
ms.openlocfilehash: 1d2bc07cff75fce7ddb50da9f54d161d7f235cab
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="39458---trackingrecordtruncated"></a><span data-ttu-id="a8390-102">39458 - TrackingRecordTruncated</span><span class="sxs-lookup"><span data-stu-id="a8390-102">39458 - TrackingRecordTruncated</span></span>
## <a name="properties"></a><span data-ttu-id="a8390-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="a8390-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a8390-104">ID</span><span class="sxs-lookup"><span data-stu-id="a8390-104">ID</span></span>|<span data-ttu-id="a8390-105">39458</span><span class="sxs-lookup"><span data-stu-id="a8390-105">39458</span></span>|  
|<span data-ttu-id="a8390-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="a8390-106">Keywords</span></span>|<span data-ttu-id="a8390-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="a8390-107">WFTracking</span></span>|  
|<span data-ttu-id="a8390-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="a8390-108">Level</span></span>|<span data-ttu-id="a8390-109">Avertissement</span><span class="sxs-lookup"><span data-stu-id="a8390-109">Warning</span></span>|  
|<span data-ttu-id="a8390-110">Canal</span><span class="sxs-lookup"><span data-stu-id="a8390-110">Channel</span></span>|<span data-ttu-id="a8390-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="a8390-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a8390-112">Description</span><span class="sxs-lookup"><span data-stu-id="a8390-112">Description</span></span>  
 <span data-ttu-id="a8390-113">Indique qu'un enregistrement de suivi a été tronqué.</span><span class="sxs-lookup"><span data-stu-id="a8390-113">Indicates a tracking record has been truncated.</span></span> <span data-ttu-id="a8390-114">Les données de variables/annotations/utilisateur ont été supprimées.</span><span class="sxs-lookup"><span data-stu-id="a8390-114">Variables/annotations/user data have been removed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a8390-115">Message</span><span class="sxs-lookup"><span data-stu-id="a8390-115">Message</span></span>  
 <span data-ttu-id="a8390-116">Enregistrement de suivi %1 tronqué écrit dans la session ETW avec le fournisseur %2.</span><span class="sxs-lookup"><span data-stu-id="a8390-116">Truncated tracking record %1 written to ETW session with provider %2.</span></span> <span data-ttu-id="a8390-117">Les données de variables/annotations/utilisateur ont été supprimées</span><span class="sxs-lookup"><span data-stu-id="a8390-117">Variables/annotations/user data have been removed</span></span>  
  
## <a name="details"></a><span data-ttu-id="a8390-118">Détails</span><span class="sxs-lookup"><span data-stu-id="a8390-118">Details</span></span>  
  
|<span data-ttu-id="a8390-119">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="a8390-119">Data Item Name</span></span>|<span data-ttu-id="a8390-120">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="a8390-120">Data Item Type</span></span>|<span data-ttu-id="a8390-121">Description</span><span class="sxs-lookup"><span data-stu-id="a8390-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a8390-122">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="a8390-122">RecordNumber</span></span>|<span data-ttu-id="a8390-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="a8390-123">xs:string</span></span>|<span data-ttu-id="a8390-124">Numéro d'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="a8390-124">The tracking record number.</span></span>|  
|<span data-ttu-id="a8390-125">ProviderId</span><span class="sxs-lookup"><span data-stu-id="a8390-125">ProviderId</span></span>|<span data-ttu-id="a8390-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="a8390-126">xs:string</span></span>|<span data-ttu-id="a8390-127">ID du fournisseur ETW.</span><span class="sxs-lookup"><span data-stu-id="a8390-127">The ETW provider id.</span></span>|  
|<span data-ttu-id="a8390-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a8390-128">AppDomain</span></span>|<span data-ttu-id="a8390-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="a8390-129">xs:string</span></span>|<span data-ttu-id="a8390-130">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="a8390-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
