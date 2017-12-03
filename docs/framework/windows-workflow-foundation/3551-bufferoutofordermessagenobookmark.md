---
title: 3551 - BufferOutOfOrderMessageNoBookmark
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7930d6c4-c843-4a83-933a-cecd71b80d1e
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6dc505a4e0e79b37f9adff41b80dcba55215576f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="3551---bufferoutofordermessagenobookmark"></a><span data-ttu-id="2547c-102">3551 - BufferOutOfOrderMessageNoBookmark</span><span class="sxs-lookup"><span data-stu-id="2547c-102">3551 - BufferOutOfOrderMessageNoBookmark</span></span>
## <a name="properties"></a><span data-ttu-id="2547c-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="2547c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2547c-104">ID</span><span class="sxs-lookup"><span data-stu-id="2547c-104">ID</span></span>|<span data-ttu-id="2547c-105">3551</span><span class="sxs-lookup"><span data-stu-id="2547c-105">3551</span></span>|  
|<span data-ttu-id="2547c-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="2547c-106">Keywords</span></span>|<span data-ttu-id="2547c-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="2547c-107">WFServices</span></span>|  
|<span data-ttu-id="2547c-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="2547c-108">Level</span></span>|<span data-ttu-id="2547c-109">Information</span><span class="sxs-lookup"><span data-stu-id="2547c-109">Information</span></span>|  
|<span data-ttu-id="2547c-110">Canal</span><span class="sxs-lookup"><span data-stu-id="2547c-110">Channel</span></span>|<span data-ttu-id="2547c-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="2547c-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2547c-112">Description</span><span class="sxs-lookup"><span data-stu-id="2547c-112">Description</span></span>  
 <span data-ttu-id="2547c-113">Indique qu'une reprise de signet a échoué.</span><span class="sxs-lookup"><span data-stu-id="2547c-113">Indicates a bookmark resumption has failed.</span></span> <span data-ttu-id="2547c-114">Une autre tentative d'opération de réception en mémoire tampon sera faite lorsque l'instance de service sera prête à traiter cette opération.</span><span class="sxs-lookup"><span data-stu-id="2547c-114">The buffered receive operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2547c-115">Message</span><span class="sxs-lookup"><span data-stu-id="2547c-115">Message</span></span>  
 <span data-ttu-id="2547c-116">Impossible d'effectuer actuellement l'opération « %2 » sur l'instance de service « %1 ».</span><span class="sxs-lookup"><span data-stu-id="2547c-116">Operation '%2' on service instance '%1' cannot be performed at this time.</span></span> <span data-ttu-id="2547c-117">Une autre tentative sera faite lorsque l'instance de service sera prête à traiter cette opération.</span><span class="sxs-lookup"><span data-stu-id="2547c-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2547c-118">Détails</span><span class="sxs-lookup"><span data-stu-id="2547c-118">Details</span></span>  
  
|<span data-ttu-id="2547c-119">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="2547c-119">Data Item Name</span></span>|<span data-ttu-id="2547c-120">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="2547c-120">Data Item Type</span></span>|<span data-ttu-id="2547c-121">Description</span><span class="sxs-lookup"><span data-stu-id="2547c-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2547c-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="2547c-122">OperationName</span></span>|<span data-ttu-id="2547c-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="2547c-123">xs:string</span></span>|<span data-ttu-id="2547c-124">Nom de l'opération.</span><span class="sxs-lookup"><span data-stu-id="2547c-124">The name of the operation.</span></span>|  
|<span data-ttu-id="2547c-125">ServiceInstanceId</span><span class="sxs-lookup"><span data-stu-id="2547c-125">ServiceInstanceId</span></span>|<span data-ttu-id="2547c-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="2547c-126">xs:string</span></span>|<span data-ttu-id="2547c-127">ID de l'instance du service.</span><span class="sxs-lookup"><span data-stu-id="2547c-127">The id of the service instance.</span></span>|  
|<span data-ttu-id="2547c-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2547c-128">AppDomain</span></span>|<span data-ttu-id="2547c-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="2547c-129">xs:string</span></span>|<span data-ttu-id="2547c-130">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2547c-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
