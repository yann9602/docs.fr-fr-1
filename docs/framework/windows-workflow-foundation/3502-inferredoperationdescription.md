---
title: 3502 - InferredOperationDescription
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e2c2464cd8c6f0c16946847a5503270453d5b019
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="3502---inferredoperationdescription"></a><span data-ttu-id="21918-102">3502 - InferredOperationDescription</span><span class="sxs-lookup"><span data-stu-id="21918-102">3502 - InferredOperationDescription</span></span>
## <a name="properties"></a><span data-ttu-id="21918-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="21918-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="21918-104">ID</span><span class="sxs-lookup"><span data-stu-id="21918-104">ID</span></span>|<span data-ttu-id="21918-105">3502</span><span class="sxs-lookup"><span data-stu-id="21918-105">3502</span></span>|  
|<span data-ttu-id="21918-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="21918-106">Keywords</span></span>|<span data-ttu-id="21918-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="21918-107">WFServices</span></span>|  
|<span data-ttu-id="21918-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="21918-108">Level</span></span>|<span data-ttu-id="21918-109">Information</span><span class="sxs-lookup"><span data-stu-id="21918-109">Information</span></span>|  
|<span data-ttu-id="21918-110">Canal</span><span class="sxs-lookup"><span data-stu-id="21918-110">Channel</span></span>|<span data-ttu-id="21918-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="21918-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="21918-112">Description</span><span class="sxs-lookup"><span data-stu-id="21918-112">Description</span></span>  
 <span data-ttu-id="21918-113">Indique qu'un OperationDescription a été déduit de WorkflowService.</span><span class="sxs-lookup"><span data-stu-id="21918-113">Indicates an OperationDescription has been inferred from WorkflowService.</span></span>  
  
## <a name="message"></a><span data-ttu-id="21918-114">Message</span><span class="sxs-lookup"><span data-stu-id="21918-114">Message</span></span>  
 <span data-ttu-id="21918-115">OperationDescription avec Name='%1' dans le contrat « %2 » a été déduit de WorkflowService.</span><span class="sxs-lookup"><span data-stu-id="21918-115">OperationDescription with Name='%1' in contract '%2' has been inferred from WorkflowService.</span></span> <span data-ttu-id="21918-116">IsOneWay=%3.</span><span class="sxs-lookup"><span data-stu-id="21918-116">IsOneWay=%3.</span></span>  
  
## <a name="details"></a><span data-ttu-id="21918-117">Détails</span><span class="sxs-lookup"><span data-stu-id="21918-117">Details</span></span>  
  
|<span data-ttu-id="21918-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="21918-118">Data Item Name</span></span>|<span data-ttu-id="21918-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="21918-119">Data Item Type</span></span>|<span data-ttu-id="21918-120">Description</span><span class="sxs-lookup"><span data-stu-id="21918-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="21918-121">OperationName</span><span class="sxs-lookup"><span data-stu-id="21918-121">OperationName</span></span>|<span data-ttu-id="21918-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="21918-122">xs:string</span></span>|<span data-ttu-id="21918-123">Nom de l'opération.</span><span class="sxs-lookup"><span data-stu-id="21918-123">The name of the operation.</span></span>|  
|<span data-ttu-id="21918-124">ContractName</span><span class="sxs-lookup"><span data-stu-id="21918-124">ContractName</span></span>|<span data-ttu-id="21918-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="21918-125">xs:string</span></span>|<span data-ttu-id="21918-126">Nom du contrat.</span><span class="sxs-lookup"><span data-stu-id="21918-126">The name of the contract.</span></span>|  
|<span data-ttu-id="21918-127">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="21918-127">IsOneWay</span></span>|<span data-ttu-id="21918-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="21918-128">xs:string</span></span>|<span data-ttu-id="21918-129">True ou False indiquant si le contrat est unidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="21918-129">True or False indicating if the contract is one-way.</span></span>|  
|<span data-ttu-id="21918-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="21918-130">AppDomain</span></span>|<span data-ttu-id="21918-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="21918-131">xs:string</span></span>|<span data-ttu-id="21918-132">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="21918-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
