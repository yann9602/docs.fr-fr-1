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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c1f9f1066f1948411d584a2dee1af2129aa3a103
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a><span data-ttu-id="0c408-102">3557 - TransactedReceiveScopeEndCommitFailed</span><span class="sxs-lookup"><span data-stu-id="0c408-102">3557 - TransactedReceiveScopeEndCommitFailed</span></span>
## <a name="properties"></a><span data-ttu-id="0c408-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="0c408-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0c408-104">ID</span><span class="sxs-lookup"><span data-stu-id="0c408-104">ID</span></span>|<span data-ttu-id="0c408-105">3557</span><span class="sxs-lookup"><span data-stu-id="0c408-105">3557</span></span>|  
|<span data-ttu-id="0c408-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="0c408-106">Keywords</span></span>|<span data-ttu-id="0c408-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="0c408-107">WFServices</span></span>|  
|<span data-ttu-id="0c408-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="0c408-108">Level</span></span>|<span data-ttu-id="0c408-109">Information</span><span class="sxs-lookup"><span data-stu-id="0c408-109">Information</span></span>|  
|<span data-ttu-id="0c408-110">Canal</span><span class="sxs-lookup"><span data-stu-id="0c408-110">Channel</span></span>|<span data-ttu-id="0c408-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="0c408-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0c408-112">Description</span><span class="sxs-lookup"><span data-stu-id="0c408-112">Description</span></span>  
 <span data-ttu-id="0c408-113">Indique que l'appel à EndCommit sur un CommittableTransaction a levé une exception TransactionException.</span><span class="sxs-lookup"><span data-stu-id="0c408-113">Indicates the call to EndCommit on a CommittableTransaction threw a TransactionException.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0c408-114">Message</span><span class="sxs-lookup"><span data-stu-id="0c408-114">Message</span></span>  
 <span data-ttu-id="0c408-115">L'appel à EndCommit sur le CommittableTransaction avec l'ID = « %1 » a levé un TransactionException avec le message suivant : « %2 ».</span><span class="sxs-lookup"><span data-stu-id="0c408-115">The call to EndCommit on the CommittableTransaction with id = '%1' threw a TransactionException with the following message: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0c408-116">Détails</span><span class="sxs-lookup"><span data-stu-id="0c408-116">Details</span></span>  
  
|<span data-ttu-id="0c408-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="0c408-117">Data Item Name</span></span>|<span data-ttu-id="0c408-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="0c408-118">Data Item Type</span></span>|<span data-ttu-id="0c408-119">Description</span><span class="sxs-lookup"><span data-stu-id="0c408-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0c408-120">TransactionId</span><span class="sxs-lookup"><span data-stu-id="0c408-120">TransactionId</span></span>|<span data-ttu-id="0c408-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="0c408-121">xs:string</span></span>|<span data-ttu-id="0c408-122">ID de CommittableTransaction.</span><span class="sxs-lookup"><span data-stu-id="0c408-122">The id of the CommittableTransaction.</span></span>|  
|<span data-ttu-id="0c408-123">Exception</span><span class="sxs-lookup"><span data-stu-id="0c408-123">Exception</span></span>|<span data-ttu-id="0c408-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="0c408-124">xs:string</span></span>|<span data-ttu-id="0c408-125">Détails de l'exception</span><span class="sxs-lookup"><span data-stu-id="0c408-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="0c408-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0c408-126">AppDomain</span></span>|<span data-ttu-id="0c408-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="0c408-127">xs:string</span></span>|<span data-ttu-id="0c408-128">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="0c408-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
