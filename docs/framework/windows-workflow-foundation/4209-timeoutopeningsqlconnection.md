---
title: 4209 - TimeoutOpeningSqlConnection
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 86d971a2e5f1257281c453e7eb0c2dc1755098d8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="4209---timeoutopeningsqlconnection"></a><span data-ttu-id="29d63-102">4209 - TimeoutOpeningSqlConnection</span><span class="sxs-lookup"><span data-stu-id="29d63-102">4209 - TimeoutOpeningSqlConnection</span></span>
## <a name="properties"></a><span data-ttu-id="29d63-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="29d63-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="29d63-104">ID</span><span class="sxs-lookup"><span data-stu-id="29d63-104">ID</span></span>|<span data-ttu-id="29d63-105">4209</span><span class="sxs-lookup"><span data-stu-id="29d63-105">4209</span></span>|  
|<span data-ttu-id="29d63-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="29d63-106">Keywords</span></span>|<span data-ttu-id="29d63-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="29d63-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="29d63-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="29d63-108">Level</span></span>|<span data-ttu-id="29d63-109">Erreur</span><span class="sxs-lookup"><span data-stu-id="29d63-109">Error</span></span>|  
|<span data-ttu-id="29d63-110">Canal</span><span class="sxs-lookup"><span data-stu-id="29d63-110">Channel</span></span>|<span data-ttu-id="29d63-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="29d63-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="29d63-112">Description</span><span class="sxs-lookup"><span data-stu-id="29d63-112">Description</span></span>  
 <span data-ttu-id="29d63-113">Indique qu'une expiration de délai d'attente s'est produite lors de la tentative d'ouverture d'une connexion SQL.</span><span class="sxs-lookup"><span data-stu-id="29d63-113">Indicates a timeout was encountered when trying to open a SQL connection.</span></span>  
  
## <a name="message"></a><span data-ttu-id="29d63-114">Message</span><span class="sxs-lookup"><span data-stu-id="29d63-114">Message</span></span>  
 <span data-ttu-id="29d63-115">Expiration du délai d'attente lors de la tentative d'ouverture d'une connexion SQL.</span><span class="sxs-lookup"><span data-stu-id="29d63-115">Timeout trying to open a SQL connection.</span></span> <span data-ttu-id="29d63-116">L'opération ne s'est pas terminée dans le délai imparti de %1.</span><span class="sxs-lookup"><span data-stu-id="29d63-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="29d63-117">Le temps alloué à cette opération peut avoir été une partie d'un délai d'expiration plus long.</span><span class="sxs-lookup"><span data-stu-id="29d63-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="29d63-118">Détails</span><span class="sxs-lookup"><span data-stu-id="29d63-118">Details</span></span>  
  
|<span data-ttu-id="29d63-119">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="29d63-119">Data Item Name</span></span>|<span data-ttu-id="29d63-120">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="29d63-120">Data Item Type</span></span>|<span data-ttu-id="29d63-121">Description</span><span class="sxs-lookup"><span data-stu-id="29d63-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="29d63-122">Délai d'expiration</span><span class="sxs-lookup"><span data-stu-id="29d63-122">Timeout</span></span>|<span data-ttu-id="29d63-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="29d63-123">xs:string</span></span>|<span data-ttu-id="29d63-124">Valeur de délai d'attente pour ouvrir la connexion SQL.</span><span class="sxs-lookup"><span data-stu-id="29d63-124">The timeout value for opening the SQL connection.</span></span>|  
|<span data-ttu-id="29d63-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="29d63-125">AppDomain</span></span>|<span data-ttu-id="29d63-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="29d63-126">xs:string</span></span>|<span data-ttu-id="29d63-127">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="29d63-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
