---
title: ServiceThrottlingBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 59f85a148d6707876a4df512d5cfbd07ca0e54b7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="servicethrottlingbehavior"></a><span data-ttu-id="c3455-102">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="c3455-102">ServiceThrottlingBehavior</span></span>
<span data-ttu-id="c3455-103">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="c3455-103">ServiceThrottlingBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3455-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3455-104">Syntax</span></span>  
  
```  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c3455-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="c3455-105">Methods</span></span>  
 <span data-ttu-id="c3455-106">La classe ServiceThrottlingBehavior ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="c3455-106">The ServiceThrottlingBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c3455-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="c3455-107">Properties</span></span>  
 <span data-ttu-id="c3455-108">La classe ServiceThrottlingBehavior a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="c3455-108">The ServiceThrottlingBehavior class has the following properties:</span></span>  
  
### <a name="maxconcurrentcalls"></a><span data-ttu-id="c3455-109">MaxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="c3455-109">MaxConcurrentCalls</span></span>  
 <span data-ttu-id="c3455-110">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="c3455-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="c3455-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="c3455-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c3455-112">Nombre maximal de messages en cours de traitement actif sur tous les objets de répartiteur dans un ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="c3455-112">The maximum number of messages actively processing across all dispatcher objects in a ServiceHost.</span></span>  
  
### <a name="maxconcurrentinstances"></a><span data-ttu-id="c3455-113">MaxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="c3455-113">MaxConcurrentInstances</span></span>  
 <span data-ttu-id="c3455-114">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="c3455-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="c3455-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="c3455-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c3455-116">Nombre maximal d'objets de service simultanément exécutables.</span><span class="sxs-lookup"><span data-stu-id="c3455-116">The maximum number of service objects that can execute at one time.</span></span>  
  
### <a name="maxconcurrentsessions"></a><span data-ttu-id="c3455-117">MaxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="c3455-117">MaxConcurrentSessions</span></span>  
 <span data-ttu-id="c3455-118">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="c3455-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="c3455-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="c3455-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c3455-120">Nombre maximal de sessions qu'un hôte peut accepter à la fois.</span><span class="sxs-lookup"><span data-stu-id="c3455-120">The maximum number of sessions a host can accept at one time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3455-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c3455-121">Requirements</span></span>  
  
|<span data-ttu-id="c3455-122">MOF</span><span class="sxs-lookup"><span data-stu-id="c3455-122">MOF</span></span>|<span data-ttu-id="c3455-123">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="c3455-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c3455-124">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="c3455-124">Namespace</span></span>|<span data-ttu-id="c3455-125">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c3455-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c3455-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3455-126">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
