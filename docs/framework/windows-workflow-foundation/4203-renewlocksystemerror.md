---
title: 4203 - RenewLockSystemError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9c2214ec48f0c1cba1e3aacad0eaa5a29625f9c4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="4203---renewlocksystemerror"></a><span data-ttu-id="d1351-102">4203 - RenewLockSystemError</span><span class="sxs-lookup"><span data-stu-id="d1351-102">4203 - RenewLockSystemError</span></span>
## <a name="properties"></a><span data-ttu-id="d1351-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="d1351-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d1351-104">ID</span><span class="sxs-lookup"><span data-stu-id="d1351-104">ID</span></span>|<span data-ttu-id="d1351-105">4203</span><span class="sxs-lookup"><span data-stu-id="d1351-105">4203</span></span>|  
|<span data-ttu-id="d1351-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="d1351-106">Keywords</span></span>|<span data-ttu-id="d1351-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="d1351-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="d1351-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="d1351-108">Level</span></span>|<span data-ttu-id="d1351-109">Erreur</span><span class="sxs-lookup"><span data-stu-id="d1351-109">Error</span></span>|  
|<span data-ttu-id="d1351-110">Canal</span><span class="sxs-lookup"><span data-stu-id="d1351-110">Channel</span></span>|<span data-ttu-id="d1351-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="d1351-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d1351-112">Description</span><span class="sxs-lookup"><span data-stu-id="d1351-112">Description</span></span>  
 <span data-ttu-id="d1351-113">Indique que le fournisseur SQL n'a pas pu étendre l'expiration du verrou, car l'expiration du verrou a déjà été passée ou le propriétaire de verrou a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="d1351-113">Indicates SQL provider has failed to extend lock expiration due to either lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="d1351-114">Le SqlWorkflowInstanceStore sera annulé.</span><span class="sxs-lookup"><span data-stu-id="d1351-114">The SqlWorkflowInstanceStore will be aborted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d1351-115">Message</span><span class="sxs-lookup"><span data-stu-id="d1351-115">Message</span></span>  
 <span data-ttu-id="d1351-116">Échec de l'extension de l'expiration du verrou ; l'expiration du verrou a déjà été passée ou le propriétaire de verrou a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="d1351-116">Failed to extend lock expiration, lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="d1351-117">Abandon de SqlWorkflowInstanceStore.</span><span class="sxs-lookup"><span data-stu-id="d1351-117">Aborting SqlWorkflowInstanceStore.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d1351-118">Détails</span><span class="sxs-lookup"><span data-stu-id="d1351-118">Details</span></span>  
  
|<span data-ttu-id="d1351-119">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="d1351-119">Data Item Name</span></span>|<span data-ttu-id="d1351-120">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="d1351-120">Data Item Type</span></span>|<span data-ttu-id="d1351-121">Description</span><span class="sxs-lookup"><span data-stu-id="d1351-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d1351-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d1351-122">AppDomain</span></span>|<span data-ttu-id="d1351-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="d1351-123">xs:string</span></span>|<span data-ttu-id="d1351-124">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d1351-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
