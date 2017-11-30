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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 779aabf5ec9b1bca7151eaf781c6dd6f2631b58f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="servicethrottlingbehavior"></a><span data-ttu-id="29439-102">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="29439-102">ServiceThrottlingBehavior</span></span>
<span data-ttu-id="29439-103">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="29439-103">ServiceThrottlingBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29439-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29439-104">Syntax</span></span>  
  
```  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="29439-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="29439-105">Methods</span></span>  
 <span data-ttu-id="29439-106">La classe ServiceThrottlingBehavior ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="29439-106">The ServiceThrottlingBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="29439-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="29439-107">Properties</span></span>  
 <span data-ttu-id="29439-108">La classe ServiceThrottlingBehavior a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="29439-108">The ServiceThrottlingBehavior class has the following properties:</span></span>  
  
### <a name="maxconcurrentcalls"></a><span data-ttu-id="29439-109">MaxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="29439-109">MaxConcurrentCalls</span></span>  
 <span data-ttu-id="29439-110">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="29439-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="29439-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="29439-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="29439-112">Nombre maximal de messages en cours de traitement actif sur tous les objets de répartiteur dans un ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="29439-112">The maximum number of messages actively processing across all dispatcher objects in a ServiceHost.</span></span>  
  
### <a name="maxconcurrentinstances"></a><span data-ttu-id="29439-113">MaxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="29439-113">MaxConcurrentInstances</span></span>  
 <span data-ttu-id="29439-114">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="29439-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="29439-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="29439-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="29439-116">Nombre maximal d'objets de service simultanément exécutables.</span><span class="sxs-lookup"><span data-stu-id="29439-116">The maximum number of service objects that can execute at one time.</span></span>  
  
### <a name="maxconcurrentsessions"></a><span data-ttu-id="29439-117">MaxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="29439-117">MaxConcurrentSessions</span></span>  
 <span data-ttu-id="29439-118">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="29439-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="29439-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="29439-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="29439-120">Nombre maximal de sessions qu'un hôte peut accepter à la fois.</span><span class="sxs-lookup"><span data-stu-id="29439-120">The maximum number of sessions a host can accept at one time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29439-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="29439-121">Requirements</span></span>  
  
|<span data-ttu-id="29439-122">MOF</span><span class="sxs-lookup"><span data-stu-id="29439-122">MOF</span></span>|<span data-ttu-id="29439-123">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="29439-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="29439-124">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="29439-124">Namespace</span></span>|<span data-ttu-id="29439-125">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="29439-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="29439-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29439-126">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
