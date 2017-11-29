---
title: 4210 - SqlExceptionCaught
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0ce8af3-eb4c-48c8-b3d9-dd2f94b5574b
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a3fb3c780b80172db8770e717f517b97608fcb7c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="4210---sqlexceptioncaught"></a><span data-ttu-id="770ab-102">4210 - SqlExceptionCaught</span><span class="sxs-lookup"><span data-stu-id="770ab-102">4210 - SqlExceptionCaught</span></span>
## <a name="properties"></a><span data-ttu-id="770ab-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="770ab-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="770ab-104">ID</span><span class="sxs-lookup"><span data-stu-id="770ab-104">ID</span></span>|<span data-ttu-id="770ab-105">4210</span><span class="sxs-lookup"><span data-stu-id="770ab-105">4210</span></span>|  
|<span data-ttu-id="770ab-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="770ab-106">Keywords</span></span>|<span data-ttu-id="770ab-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="770ab-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="770ab-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="770ab-108">Level</span></span>|<span data-ttu-id="770ab-109">Avertissement</span><span class="sxs-lookup"><span data-stu-id="770ab-109">Warning</span></span>|  
|<span data-ttu-id="770ab-110">Canal</span><span class="sxs-lookup"><span data-stu-id="770ab-110">Channel</span></span>|<span data-ttu-id="770ab-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="770ab-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="770ab-112">Description</span><span class="sxs-lookup"><span data-stu-id="770ab-112">Description</span></span>  
 <span data-ttu-id="770ab-113">Indique qu'une exception SQL a été interceptée.</span><span class="sxs-lookup"><span data-stu-id="770ab-113">Indicates a SQL exception was caught.</span></span>  
  
## <a name="message"></a><span data-ttu-id="770ab-114">Message</span><span class="sxs-lookup"><span data-stu-id="770ab-114">Message</span></span>  
 <span data-ttu-id="770ab-115">Message %2 avec numéro d'exception SQL %1 intercepté.</span><span class="sxs-lookup"><span data-stu-id="770ab-115">Caught SQL Exception number %1 message %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="770ab-116">Détails</span><span class="sxs-lookup"><span data-stu-id="770ab-116">Details</span></span>  
  
|<span data-ttu-id="770ab-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="770ab-117">Data Item Name</span></span>|<span data-ttu-id="770ab-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="770ab-118">Data Item Type</span></span>|<span data-ttu-id="770ab-119">Description</span><span class="sxs-lookup"><span data-stu-id="770ab-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="770ab-120">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="770ab-120">ErrorNumber</span></span>|<span data-ttu-id="770ab-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="770ab-121">xs:string</span></span>|<span data-ttu-id="770ab-122">Numéro d'erreur SQL.</span><span class="sxs-lookup"><span data-stu-id="770ab-122">The SQL error number.</span></span>|  
|<span data-ttu-id="770ab-123">ExceptionMessage</span><span class="sxs-lookup"><span data-stu-id="770ab-123">ExceptionMessage</span></span>|<span data-ttu-id="770ab-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="770ab-124">xs:string</span></span>|<span data-ttu-id="770ab-125">Message de l'exception SQL.</span><span class="sxs-lookup"><span data-stu-id="770ab-125">The message from the SQL exception.</span></span>|  
|<span data-ttu-id="770ab-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="770ab-126">AppDomain</span></span>|<span data-ttu-id="770ab-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="770ab-127">xs:string</span></span>|<span data-ttu-id="770ab-128">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="770ab-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
