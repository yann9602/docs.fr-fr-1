---
title: 39456 - TrackingRecordDropped
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: da13d5bc-1736-47a4-b3fd-064ca8040326
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3e663cced42252112e1948f4907bc8c81ef941f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="39456---trackingrecorddropped"></a><span data-ttu-id="f6d79-102">39456 - TrackingRecordDropped</span><span class="sxs-lookup"><span data-stu-id="f6d79-102">39456 - TrackingRecordDropped</span></span>
## <a name="properties"></a><span data-ttu-id="f6d79-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="f6d79-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f6d79-104">ID</span><span class="sxs-lookup"><span data-stu-id="f6d79-104">ID</span></span>|<span data-ttu-id="f6d79-105">39456</span><span class="sxs-lookup"><span data-stu-id="f6d79-105">39456</span></span>|  
|<span data-ttu-id="f6d79-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="f6d79-106">Keywords</span></span>|<span data-ttu-id="f6d79-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="f6d79-107">WFTracking</span></span>|  
|<span data-ttu-id="f6d79-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="f6d79-108">Level</span></span>|<span data-ttu-id="f6d79-109">Avertissement</span><span class="sxs-lookup"><span data-stu-id="f6d79-109">Warning</span></span>|  
|<span data-ttu-id="f6d79-110">Canal</span><span class="sxs-lookup"><span data-stu-id="f6d79-110">Channel</span></span>|<span data-ttu-id="f6d79-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="f6d79-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f6d79-112">Description</span><span class="sxs-lookup"><span data-stu-id="f6d79-112">Description</span></span>  
 <span data-ttu-id="f6d79-113">Indique qu'un enregistrement de suivi a été supprimé, car sa taille dépasse la taille maximale autorisée par le fournisseur de session ETW.</span><span class="sxs-lookup"><span data-stu-id="f6d79-113">Indicates a tracking record has been dropped because its size exceeds maximum allowed by the ETW session provider.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f6d79-114">Message</span><span class="sxs-lookup"><span data-stu-id="f6d79-114">Message</span></span>  
 <span data-ttu-id="f6d79-115">La taille de l'enregistrement de suivi %1 dépasse la valeur maximale autorisée par la session ETW pour le fournisseur %2</span><span class="sxs-lookup"><span data-stu-id="f6d79-115">Size of tracking record %1 exceeds maximum allowed by the ETW session for provider %2</span></span>  
  
## <a name="details"></a><span data-ttu-id="f6d79-116">Détails</span><span class="sxs-lookup"><span data-stu-id="f6d79-116">Details</span></span>  
  
|<span data-ttu-id="f6d79-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="f6d79-117">Data Item Name</span></span>|<span data-ttu-id="f6d79-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="f6d79-118">Data Item Type</span></span>|<span data-ttu-id="f6d79-119">Description</span><span class="sxs-lookup"><span data-stu-id="f6d79-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f6d79-120">Exception</span><span class="sxs-lookup"><span data-stu-id="f6d79-120">Exception</span></span>|<span data-ttu-id="f6d79-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="f6d79-121">xs:string</span></span>|<span data-ttu-id="f6d79-122">Détails de l'exception</span><span class="sxs-lookup"><span data-stu-id="f6d79-122">The exception details for the exception</span></span>|  
|<span data-ttu-id="f6d79-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f6d79-123">AppDomain</span></span>|<span data-ttu-id="f6d79-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="f6d79-124">xs:string</span></span>|<span data-ttu-id="f6d79-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f6d79-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
