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
ms.workload: dotnet
ms.openlocfilehash: 5e785e40afcb91620940f952022eda4c4b799f4a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="3551---bufferoutofordermessagenobookmark"></a><span data-ttu-id="9a65d-102">3551 - BufferOutOfOrderMessageNoBookmark</span><span class="sxs-lookup"><span data-stu-id="9a65d-102">3551 - BufferOutOfOrderMessageNoBookmark</span></span>
## <a name="properties"></a><span data-ttu-id="9a65d-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="9a65d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9a65d-104">ID</span><span class="sxs-lookup"><span data-stu-id="9a65d-104">ID</span></span>|<span data-ttu-id="9a65d-105">3551</span><span class="sxs-lookup"><span data-stu-id="9a65d-105">3551</span></span>|  
|<span data-ttu-id="9a65d-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="9a65d-106">Keywords</span></span>|<span data-ttu-id="9a65d-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="9a65d-107">WFServices</span></span>|  
|<span data-ttu-id="9a65d-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="9a65d-108">Level</span></span>|<span data-ttu-id="9a65d-109">Information</span><span class="sxs-lookup"><span data-stu-id="9a65d-109">Information</span></span>|  
|<span data-ttu-id="9a65d-110">Canal</span><span class="sxs-lookup"><span data-stu-id="9a65d-110">Channel</span></span>|<span data-ttu-id="9a65d-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="9a65d-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9a65d-112">Description</span><span class="sxs-lookup"><span data-stu-id="9a65d-112">Description</span></span>  
 <span data-ttu-id="9a65d-113">Indique qu'une reprise de signet a échoué.</span><span class="sxs-lookup"><span data-stu-id="9a65d-113">Indicates a bookmark resumption has failed.</span></span> <span data-ttu-id="9a65d-114">Une autre tentative d'opération de réception en mémoire tampon sera faite lorsque l'instance de service sera prête à traiter cette opération.</span><span class="sxs-lookup"><span data-stu-id="9a65d-114">The buffered receive operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9a65d-115">Message</span><span class="sxs-lookup"><span data-stu-id="9a65d-115">Message</span></span>  
 <span data-ttu-id="9a65d-116">Impossible d'effectuer actuellement l'opération « %2 » sur l'instance de service « %1 ».</span><span class="sxs-lookup"><span data-stu-id="9a65d-116">Operation '%2' on service instance '%1' cannot be performed at this time.</span></span> <span data-ttu-id="9a65d-117">Une autre tentative sera faite lorsque l'instance de service sera prête à traiter cette opération.</span><span class="sxs-lookup"><span data-stu-id="9a65d-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9a65d-118">Détails</span><span class="sxs-lookup"><span data-stu-id="9a65d-118">Details</span></span>  
  
|<span data-ttu-id="9a65d-119">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="9a65d-119">Data Item Name</span></span>|<span data-ttu-id="9a65d-120">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="9a65d-120">Data Item Type</span></span>|<span data-ttu-id="9a65d-121">Description</span><span class="sxs-lookup"><span data-stu-id="9a65d-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9a65d-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="9a65d-122">OperationName</span></span>|<span data-ttu-id="9a65d-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="9a65d-123">xs:string</span></span>|<span data-ttu-id="9a65d-124">Nom de l'opération.</span><span class="sxs-lookup"><span data-stu-id="9a65d-124">The name of the operation.</span></span>|  
|<span data-ttu-id="9a65d-125">ServiceInstanceId</span><span class="sxs-lookup"><span data-stu-id="9a65d-125">ServiceInstanceId</span></span>|<span data-ttu-id="9a65d-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="9a65d-126">xs:string</span></span>|<span data-ttu-id="9a65d-127">ID de l'instance du service.</span><span class="sxs-lookup"><span data-stu-id="9a65d-127">The id of the service instance.</span></span>|  
|<span data-ttu-id="9a65d-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9a65d-128">AppDomain</span></span>|<span data-ttu-id="9a65d-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="9a65d-129">xs:string</span></span>|<span data-ttu-id="9a65d-130">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9a65d-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
