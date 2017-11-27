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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 044d67bc2b721451ade04947484899266d288d8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="3502---inferredoperationdescription"></a><span data-ttu-id="a1fa2-102">3502 - InferredOperationDescription</span><span class="sxs-lookup"><span data-stu-id="a1fa2-102">3502 - InferredOperationDescription</span></span>
## <a name="properties"></a><span data-ttu-id="a1fa2-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="a1fa2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a1fa2-104">ID</span><span class="sxs-lookup"><span data-stu-id="a1fa2-104">ID</span></span>|<span data-ttu-id="a1fa2-105">3502</span><span class="sxs-lookup"><span data-stu-id="a1fa2-105">3502</span></span>|  
|<span data-ttu-id="a1fa2-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="a1fa2-106">Keywords</span></span>|<span data-ttu-id="a1fa2-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="a1fa2-107">WFServices</span></span>|  
|<span data-ttu-id="a1fa2-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="a1fa2-108">Level</span></span>|<span data-ttu-id="a1fa2-109">Information</span><span class="sxs-lookup"><span data-stu-id="a1fa2-109">Information</span></span>|  
|<span data-ttu-id="a1fa2-110">Canal</span><span class="sxs-lookup"><span data-stu-id="a1fa2-110">Channel</span></span>|<span data-ttu-id="a1fa2-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="a1fa2-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a1fa2-112">Description</span><span class="sxs-lookup"><span data-stu-id="a1fa2-112">Description</span></span>  
 <span data-ttu-id="a1fa2-113">Indique qu'un OperationDescription a été déduit de WorkflowService.</span><span class="sxs-lookup"><span data-stu-id="a1fa2-113">Indicates an OperationDescription has been inferred from WorkflowService.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a1fa2-114">Message</span><span class="sxs-lookup"><span data-stu-id="a1fa2-114">Message</span></span>  
 <span data-ttu-id="a1fa2-115">OperationDescription avec Name='%1' dans le contrat « %2 » a été déduit de WorkflowService.</span><span class="sxs-lookup"><span data-stu-id="a1fa2-115">OperationDescription with Name='%1' in contract '%2' has been inferred from WorkflowService.</span></span> <span data-ttu-id="a1fa2-116">IsOneWay=%3.</span><span class="sxs-lookup"><span data-stu-id="a1fa2-116">IsOneWay=%3.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a1fa2-117">Détails</span><span class="sxs-lookup"><span data-stu-id="a1fa2-117">Details</span></span>  
  
|<span data-ttu-id="a1fa2-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="a1fa2-118">Data Item Name</span></span>|<span data-ttu-id="a1fa2-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="a1fa2-119">Data Item Type</span></span>|<span data-ttu-id="a1fa2-120">Description</span><span class="sxs-lookup"><span data-stu-id="a1fa2-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a1fa2-121">OperationName</span><span class="sxs-lookup"><span data-stu-id="a1fa2-121">OperationName</span></span>|<span data-ttu-id="a1fa2-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="a1fa2-122">xs:string</span></span>|<span data-ttu-id="a1fa2-123">Nom de l'opération.</span><span class="sxs-lookup"><span data-stu-id="a1fa2-123">The name of the operation.</span></span>|  
|<span data-ttu-id="a1fa2-124">ContractName</span><span class="sxs-lookup"><span data-stu-id="a1fa2-124">ContractName</span></span>|<span data-ttu-id="a1fa2-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="a1fa2-125">xs:string</span></span>|<span data-ttu-id="a1fa2-126">Nom du contrat.</span><span class="sxs-lookup"><span data-stu-id="a1fa2-126">The name of the contract.</span></span>|  
|<span data-ttu-id="a1fa2-127">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="a1fa2-127">IsOneWay</span></span>|<span data-ttu-id="a1fa2-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="a1fa2-128">xs:string</span></span>|<span data-ttu-id="a1fa2-129">True ou False indiquant si le contrat est unidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="a1fa2-129">True or False indicating if the contract is one-way.</span></span>|  
|<span data-ttu-id="a1fa2-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a1fa2-130">AppDomain</span></span>|<span data-ttu-id="a1fa2-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="a1fa2-131">xs:string</span></span>|<span data-ttu-id="a1fa2-132">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="a1fa2-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
