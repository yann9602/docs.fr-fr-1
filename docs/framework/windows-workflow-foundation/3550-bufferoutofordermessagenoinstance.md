---
title: 3550 - BufferOutOfOrderMessageNoInstance
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eabc6a6915560d8c49e695d5d681f1544689cb07
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="3550---bufferoutofordermessagenoinstance"></a><span data-ttu-id="17412-102">3550 - BufferOutOfOrderMessageNoInstance</span><span class="sxs-lookup"><span data-stu-id="17412-102">3550 - BufferOutOfOrderMessageNoInstance</span></span>
## <a name="properties"></a><span data-ttu-id="17412-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="17412-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="17412-104">ID</span><span class="sxs-lookup"><span data-stu-id="17412-104">ID</span></span>|<span data-ttu-id="17412-105">3550</span><span class="sxs-lookup"><span data-stu-id="17412-105">3550</span></span>|  
|<span data-ttu-id="17412-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="17412-106">Keywords</span></span>|<span data-ttu-id="17412-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="17412-107">WFServices</span></span>|  
|<span data-ttu-id="17412-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="17412-108">Level</span></span>|<span data-ttu-id="17412-109">Information</span><span class="sxs-lookup"><span data-stu-id="17412-109">Information</span></span>|  
|<span data-ttu-id="17412-110">Canal</span><span class="sxs-lookup"><span data-stu-id="17412-110">Channel</span></span>|<span data-ttu-id="17412-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="17412-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="17412-112">Description</span><span class="sxs-lookup"><span data-stu-id="17412-112">Description</span></span>  
 <span data-ttu-id="17412-113">Indique qu'une réception mise en mémoire tampon a échoué.</span><span class="sxs-lookup"><span data-stu-id="17412-113">Indicates a buffered receive has failed.</span></span> <span data-ttu-id="17412-114">Une autre tentative d'opération sera faite lorsque l'instance de service sera prête à traiter cette opération.</span><span class="sxs-lookup"><span data-stu-id="17412-114">The operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="17412-115">Message</span><span class="sxs-lookup"><span data-stu-id="17412-115">Message</span></span>  
 <span data-ttu-id="17412-116">Impossible d'effectuer l'opération « %1 » actuellement.</span><span class="sxs-lookup"><span data-stu-id="17412-116">Operation '%1' cannot be performed at this time.</span></span> <span data-ttu-id="17412-117">Une autre tentative sera faite lorsque l'instance de service sera prête à traiter cette opération.</span><span class="sxs-lookup"><span data-stu-id="17412-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="17412-118">Détails</span><span class="sxs-lookup"><span data-stu-id="17412-118">Details</span></span>  
  
|<span data-ttu-id="17412-119">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="17412-119">Data Item Name</span></span>|<span data-ttu-id="17412-120">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="17412-120">Data Item Type</span></span>|<span data-ttu-id="17412-121">Description</span><span class="sxs-lookup"><span data-stu-id="17412-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="17412-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="17412-122">OperationName</span></span>|<span data-ttu-id="17412-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="17412-123">xs:string</span></span>|<span data-ttu-id="17412-124">Nom de l'opération.</span><span class="sxs-lookup"><span data-stu-id="17412-124">The name of the operation.</span></span>|  
|<span data-ttu-id="17412-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="17412-125">AppDomain</span></span>|<span data-ttu-id="17412-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="17412-126">xs:string</span></span>|<span data-ttu-id="17412-127">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="17412-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
