---
title: "COR_GC_STAT_TYPES (énumération)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_GC_STAT_TYPES
api_location: mscoree.dll
api_type: COM
f1_keywords: COR_GC_STAT_TYPES
helpviewer_keywords: COR_GC_STAT_TYPES enumeration [.NET Framework hosting]
ms.assetid: fc51d6db-f7f8-408b-b93d-c166fc712c99
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 86d0ce931518fa50dbd3b0d6d7f2755d19042eca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corgcstattypes-enumeration"></a><span data-ttu-id="70f39-102">COR_GC_STAT_TYPES (énumération)</span><span class="sxs-lookup"><span data-stu-id="70f39-102">COR_GC_STAT_TYPES Enumeration</span></span>
<span data-ttu-id="70f39-103">Spécifie les statistiques à enregistrer pour un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="70f39-103">Specifies the statistics to be recorded for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70f39-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70f39-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a><span data-ttu-id="70f39-105">Notes</span><span class="sxs-lookup"><span data-stu-id="70f39-105">Remarks</span></span>  
 <span data-ttu-id="70f39-106">Cette énumération spécifie les statistiques de la [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure doivent être définies par [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="70f39-106">This enumeration specifies which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set by [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method.</span></span>  
  
## <a name="members"></a><span data-ttu-id="70f39-107">Membres</span><span class="sxs-lookup"><span data-stu-id="70f39-107">Members</span></span>  
  
|<span data-ttu-id="70f39-108">Membre</span><span class="sxs-lookup"><span data-stu-id="70f39-108">Member</span></span>|<span data-ttu-id="70f39-109">Description</span><span class="sxs-lookup"><span data-stu-id="70f39-109">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_COUNTS`|<span data-ttu-id="70f39-110">Enregistre le nombre de garbage collections effectués pour chaque génération.</span><span class="sxs-lookup"><span data-stu-id="70f39-110">Records the number of garbage collections performed for each generation.</span></span>|  
|`COR_GC_MEMORYUSAGE`|<span data-ttu-id="70f39-111">Enregistrements d’utilisation et l’opération garbage collection taille statistiques de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="70f39-111">Records memory usage and garbage collection size statistics.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="70f39-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="70f39-112">Requirements</span></span>  
 <span data-ttu-id="70f39-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70f39-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70f39-114">**En-tête :** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="70f39-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="70f39-115">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70f39-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70f39-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70f39-116">See Also</span></span>  
 [<span data-ttu-id="70f39-117">COR_GC_STATS, structure</span><span class="sxs-lookup"><span data-stu-id="70f39-117">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [<span data-ttu-id="70f39-118">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="70f39-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
