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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 60367b33e1e57cce8646b4fcde79c7d4fd20a4cc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="3503---duplicatecorrelationquery"></a><span data-ttu-id="a5589-102">3503 - DuplicateCorrelationQuery</span><span class="sxs-lookup"><span data-stu-id="a5589-102">3503 - DuplicateCorrelationQuery</span></span>
## <a name="properties"></a><span data-ttu-id="a5589-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="a5589-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a5589-104">ID</span><span class="sxs-lookup"><span data-stu-id="a5589-104">ID</span></span>|<span data-ttu-id="a5589-105">3503</span><span class="sxs-lookup"><span data-stu-id="a5589-105">3503</span></span>|  
|<span data-ttu-id="a5589-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="a5589-106">Keywords</span></span>|<span data-ttu-id="a5589-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="a5589-107">WFServices</span></span>|  
|<span data-ttu-id="a5589-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="a5589-108">Level</span></span>|<span data-ttu-id="a5589-109">Avertissement</span><span class="sxs-lookup"><span data-stu-id="a5589-109">Warning</span></span>|  
|<span data-ttu-id="a5589-110">Canal</span><span class="sxs-lookup"><span data-stu-id="a5589-110">Channel</span></span>|<span data-ttu-id="a5589-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="a5589-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a5589-112">Description</span><span class="sxs-lookup"><span data-stu-id="a5589-112">Description</span></span>  
 <span data-ttu-id="a5589-113">Indique qu'un CorrelationQuery en double a été trouvé.</span><span class="sxs-lookup"><span data-stu-id="a5589-113">Indicates a duplicate CorrelationQuery was found.</span></span> <span data-ttu-id="a5589-114">Cette requête en double ne sera pas utilisée lors du calcul de la corrélation.</span><span class="sxs-lookup"><span data-stu-id="a5589-114">The duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a5589-115">Message</span><span class="sxs-lookup"><span data-stu-id="a5589-115">Message</span></span>  
 <span data-ttu-id="a5589-116">CorrelationQuery en double trouvé avec Where='%1'.</span><span class="sxs-lookup"><span data-stu-id="a5589-116">A duplicate CorrelationQuery was found with Where='%1'.</span></span> <span data-ttu-id="a5589-117">Cette requête en double ne sera pas utilisée lors du calcul de la corrélation.</span><span class="sxs-lookup"><span data-stu-id="a5589-117">This duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a5589-118">Détails</span><span class="sxs-lookup"><span data-stu-id="a5589-118">Details</span></span>  
  
|<span data-ttu-id="a5589-119">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="a5589-119">Data Item Name</span></span>|<span data-ttu-id="a5589-120">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="a5589-120">Data Item Type</span></span>|<span data-ttu-id="a5589-121">Description</span><span class="sxs-lookup"><span data-stu-id="a5589-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a5589-122">Où</span><span class="sxs-lookup"><span data-stu-id="a5589-122">Where</span></span>|<span data-ttu-id="a5589-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="a5589-123">xs:string</span></span>|<span data-ttu-id="a5589-124">Partie Where de la requête de corrélation.</span><span class="sxs-lookup"><span data-stu-id="a5589-124">The Where portion of the correlation query.</span></span>|  
|<span data-ttu-id="a5589-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a5589-125">AppDomain</span></span>|<span data-ttu-id="a5589-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="a5589-126">xs:string</span></span>|<span data-ttu-id="a5589-127">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="a5589-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
