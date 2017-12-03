---
title: 3503 - DuplicateCorrelationQuery
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b857f8e6-ce4d-4da4-bc9d-6cd63fa558a4
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4b86289340c35d24552b1d524a3cceaacb2f0420
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="3503---duplicatecorrelationquery"></a><span data-ttu-id="af811-102">3503 - DuplicateCorrelationQuery</span><span class="sxs-lookup"><span data-stu-id="af811-102">3503 - DuplicateCorrelationQuery</span></span>
## <a name="properties"></a><span data-ttu-id="af811-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="af811-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="af811-104">ID</span><span class="sxs-lookup"><span data-stu-id="af811-104">ID</span></span>|<span data-ttu-id="af811-105">3503</span><span class="sxs-lookup"><span data-stu-id="af811-105">3503</span></span>|  
|<span data-ttu-id="af811-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="af811-106">Keywords</span></span>|<span data-ttu-id="af811-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="af811-107">WFServices</span></span>|  
|<span data-ttu-id="af811-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="af811-108">Level</span></span>|<span data-ttu-id="af811-109">Avertissement</span><span class="sxs-lookup"><span data-stu-id="af811-109">Warning</span></span>|  
|<span data-ttu-id="af811-110">Canal</span><span class="sxs-lookup"><span data-stu-id="af811-110">Channel</span></span>|<span data-ttu-id="af811-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="af811-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="af811-112">Description</span><span class="sxs-lookup"><span data-stu-id="af811-112">Description</span></span>  
 <span data-ttu-id="af811-113">Indique qu'un CorrelationQuery en double a été trouvé.</span><span class="sxs-lookup"><span data-stu-id="af811-113">Indicates a duplicate CorrelationQuery was found.</span></span> <span data-ttu-id="af811-114">Cette requête en double ne sera pas utilisée lors du calcul de la corrélation.</span><span class="sxs-lookup"><span data-stu-id="af811-114">The duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="af811-115">Message</span><span class="sxs-lookup"><span data-stu-id="af811-115">Message</span></span>  
 <span data-ttu-id="af811-116">CorrelationQuery en double trouvé avec Where='%1'.</span><span class="sxs-lookup"><span data-stu-id="af811-116">A duplicate CorrelationQuery was found with Where='%1'.</span></span> <span data-ttu-id="af811-117">Cette requête en double ne sera pas utilisée lors du calcul de la corrélation.</span><span class="sxs-lookup"><span data-stu-id="af811-117">This duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="af811-118">Détails</span><span class="sxs-lookup"><span data-stu-id="af811-118">Details</span></span>  
  
|<span data-ttu-id="af811-119">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="af811-119">Data Item Name</span></span>|<span data-ttu-id="af811-120">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="af811-120">Data Item Type</span></span>|<span data-ttu-id="af811-121">Description</span><span class="sxs-lookup"><span data-stu-id="af811-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="af811-122">Où</span><span class="sxs-lookup"><span data-stu-id="af811-122">Where</span></span>|<span data-ttu-id="af811-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="af811-123">xs:string</span></span>|<span data-ttu-id="af811-124">Partie Where de la requête de corrélation.</span><span class="sxs-lookup"><span data-stu-id="af811-124">The Where portion of the correlation query.</span></span>|  
|<span data-ttu-id="af811-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="af811-125">AppDomain</span></span>|<span data-ttu-id="af811-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="af811-126">xs:string</span></span>|<span data-ttu-id="af811-127">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="af811-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
