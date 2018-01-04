---
title: 3557 - TransactedReceiveScopeEndCommitFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 079f0188-8146-49ee-b6ae-a08f4e4d2b9b
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 85e9456f6b4c1884b2e28671b304728135b6b1d5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a><span data-ttu-id="73b7c-102">3557 - TransactedReceiveScopeEndCommitFailed</span><span class="sxs-lookup"><span data-stu-id="73b7c-102">3557 - TransactedReceiveScopeEndCommitFailed</span></span>
## <a name="properties"></a><span data-ttu-id="73b7c-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="73b7c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="73b7c-104">ID</span><span class="sxs-lookup"><span data-stu-id="73b7c-104">ID</span></span>|<span data-ttu-id="73b7c-105">3557</span><span class="sxs-lookup"><span data-stu-id="73b7c-105">3557</span></span>|  
|<span data-ttu-id="73b7c-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="73b7c-106">Keywords</span></span>|<span data-ttu-id="73b7c-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="73b7c-107">WFServices</span></span>|  
|<span data-ttu-id="73b7c-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="73b7c-108">Level</span></span>|<span data-ttu-id="73b7c-109">Information</span><span class="sxs-lookup"><span data-stu-id="73b7c-109">Information</span></span>|  
|<span data-ttu-id="73b7c-110">Canal</span><span class="sxs-lookup"><span data-stu-id="73b7c-110">Channel</span></span>|<span data-ttu-id="73b7c-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="73b7c-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="73b7c-112">Description</span><span class="sxs-lookup"><span data-stu-id="73b7c-112">Description</span></span>  
 <span data-ttu-id="73b7c-113">Indique que l'appel à EndCommit sur un CommittableTransaction a levé une exception TransactionException.</span><span class="sxs-lookup"><span data-stu-id="73b7c-113">Indicates the call to EndCommit on a CommittableTransaction threw a TransactionException.</span></span>  
  
## <a name="message"></a><span data-ttu-id="73b7c-114">Message</span><span class="sxs-lookup"><span data-stu-id="73b7c-114">Message</span></span>  
 <span data-ttu-id="73b7c-115">L'appel à EndCommit sur le CommittableTransaction avec l'ID = « %1 » a levé un TransactionException avec le message suivant : « %2 ».</span><span class="sxs-lookup"><span data-stu-id="73b7c-115">The call to EndCommit on the CommittableTransaction with id = '%1' threw a TransactionException with the following message: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="73b7c-116">Détails</span><span class="sxs-lookup"><span data-stu-id="73b7c-116">Details</span></span>  
  
|<span data-ttu-id="73b7c-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="73b7c-117">Data Item Name</span></span>|<span data-ttu-id="73b7c-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="73b7c-118">Data Item Type</span></span>|<span data-ttu-id="73b7c-119">Description</span><span class="sxs-lookup"><span data-stu-id="73b7c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="73b7c-120">TransactionId</span><span class="sxs-lookup"><span data-stu-id="73b7c-120">TransactionId</span></span>|<span data-ttu-id="73b7c-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="73b7c-121">xs:string</span></span>|<span data-ttu-id="73b7c-122">ID de CommittableTransaction.</span><span class="sxs-lookup"><span data-stu-id="73b7c-122">The id of the CommittableTransaction.</span></span>|  
|<span data-ttu-id="73b7c-123">Exception</span><span class="sxs-lookup"><span data-stu-id="73b7c-123">Exception</span></span>|<span data-ttu-id="73b7c-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="73b7c-124">xs:string</span></span>|<span data-ttu-id="73b7c-125">Détails de l'exception</span><span class="sxs-lookup"><span data-stu-id="73b7c-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="73b7c-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="73b7c-126">AppDomain</span></span>|<span data-ttu-id="73b7c-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="73b7c-127">xs:string</span></span>|<span data-ttu-id="73b7c-128">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="73b7c-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
