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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 06d4695eb125475f41a94c7f2266df6d2c3f400d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="4203---renewlocksystemerror"></a><span data-ttu-id="ec392-102">4203 - RenewLockSystemError</span><span class="sxs-lookup"><span data-stu-id="ec392-102">4203 - RenewLockSystemError</span></span>
## <a name="properties"></a><span data-ttu-id="ec392-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="ec392-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ec392-104">ID</span><span class="sxs-lookup"><span data-stu-id="ec392-104">ID</span></span>|<span data-ttu-id="ec392-105">4203</span><span class="sxs-lookup"><span data-stu-id="ec392-105">4203</span></span>|  
|<span data-ttu-id="ec392-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="ec392-106">Keywords</span></span>|<span data-ttu-id="ec392-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="ec392-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="ec392-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="ec392-108">Level</span></span>|<span data-ttu-id="ec392-109">Erreur</span><span class="sxs-lookup"><span data-stu-id="ec392-109">Error</span></span>|  
|<span data-ttu-id="ec392-110">Canal</span><span class="sxs-lookup"><span data-stu-id="ec392-110">Channel</span></span>|<span data-ttu-id="ec392-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="ec392-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ec392-112">Description</span><span class="sxs-lookup"><span data-stu-id="ec392-112">Description</span></span>  
 <span data-ttu-id="ec392-113">Indique que le fournisseur SQL n'a pas pu étendre l'expiration du verrou, car l'expiration du verrou a déjà été passée ou le propriétaire de verrou a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="ec392-113">Indicates SQL provider has failed to extend lock expiration due to either lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="ec392-114">Le SqlWorkflowInstanceStore sera annulé.</span><span class="sxs-lookup"><span data-stu-id="ec392-114">The SqlWorkflowInstanceStore will be aborted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ec392-115">Message</span><span class="sxs-lookup"><span data-stu-id="ec392-115">Message</span></span>  
 <span data-ttu-id="ec392-116">Échec de l'extension de l'expiration du verrou ; l'expiration du verrou a déjà été passée ou le propriétaire de verrou a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="ec392-116">Failed to extend lock expiration, lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="ec392-117">Abandon de SqlWorkflowInstanceStore.</span><span class="sxs-lookup"><span data-stu-id="ec392-117">Aborting SqlWorkflowInstanceStore.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ec392-118">Détails</span><span class="sxs-lookup"><span data-stu-id="ec392-118">Details</span></span>  
  
|<span data-ttu-id="ec392-119">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="ec392-119">Data Item Name</span></span>|<span data-ttu-id="ec392-120">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="ec392-120">Data Item Type</span></span>|<span data-ttu-id="ec392-121">Description</span><span class="sxs-lookup"><span data-stu-id="ec392-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ec392-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ec392-122">AppDomain</span></span>|<span data-ttu-id="ec392-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="ec392-123">xs:string</span></span>|<span data-ttu-id="ec392-124">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ec392-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
