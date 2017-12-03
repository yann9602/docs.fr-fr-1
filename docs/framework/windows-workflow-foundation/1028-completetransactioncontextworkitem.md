---
title: 1028 - CompleteTransactionContextWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95423f9d-d29a-460e-bcd8-096e80af5bd0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8770c0d41537ec1ce48dd0038aecc220f0e6ab32
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="1028---completetransactioncontextworkitem"></a><span data-ttu-id="e2c9f-102">1028 - CompleteTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="e2c9f-102">1028 - CompleteTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="e2c9f-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="e2c9f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e2c9f-104">ID</span><span class="sxs-lookup"><span data-stu-id="e2c9f-104">ID</span></span>|<span data-ttu-id="e2c9f-105">1028</span><span class="sxs-lookup"><span data-stu-id="e2c9f-105">1028</span></span>|  
|<span data-ttu-id="e2c9f-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="e2c9f-106">Keywords</span></span>|<span data-ttu-id="e2c9f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e2c9f-107">WFRuntime</span></span>|  
|<span data-ttu-id="e2c9f-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="e2c9f-108">Level</span></span>|<span data-ttu-id="e2c9f-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="e2c9f-109">Verbose</span></span>|  
|<span data-ttu-id="e2c9f-110">Canal</span><span class="sxs-lookup"><span data-stu-id="e2c9f-110">Channel</span></span>|<span data-ttu-id="e2c9f-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="e2c9f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e2c9f-112">Description</span><span class="sxs-lookup"><span data-stu-id="e2c9f-112">Description</span></span>  
 <span data-ttu-id="e2c9f-113">Indique qu'un TransactionContextWorkItem est terminé.</span><span class="sxs-lookup"><span data-stu-id="e2c9f-113">Indicates a TransactionContextWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e2c9f-114">Message</span><span class="sxs-lookup"><span data-stu-id="e2c9f-114">Message</span></span>  
 <span data-ttu-id="e2c9f-115">TransactionContextWorkItem est terminé pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="e2c9f-115">A TransactionContextWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e2c9f-116">Détails</span><span class="sxs-lookup"><span data-stu-id="e2c9f-116">Details</span></span>  
  
|<span data-ttu-id="e2c9f-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="e2c9f-117">Data Item Name</span></span>|<span data-ttu-id="e2c9f-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="e2c9f-118">Data Item Type</span></span>|<span data-ttu-id="e2c9f-119">Description</span><span class="sxs-lookup"><span data-stu-id="e2c9f-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e2c9f-120">Activité</span><span class="sxs-lookup"><span data-stu-id="e2c9f-120">Activity</span></span>|<span data-ttu-id="e2c9f-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2c9f-121">xs:string</span></span>|<span data-ttu-id="e2c9f-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="e2c9f-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="e2c9f-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="e2c9f-123">DisplayName</span></span>|<span data-ttu-id="e2c9f-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2c9f-124">xs:string</span></span>|<span data-ttu-id="e2c9f-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="e2c9f-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="e2c9f-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="e2c9f-126">InstanceId</span></span>|<span data-ttu-id="e2c9f-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2c9f-127">xs:string</span></span>|<span data-ttu-id="e2c9f-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="e2c9f-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="e2c9f-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e2c9f-129">AppDomain</span></span>|<span data-ttu-id="e2c9f-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2c9f-130">xs:string</span></span>|<span data-ttu-id="e2c9f-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e2c9f-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
