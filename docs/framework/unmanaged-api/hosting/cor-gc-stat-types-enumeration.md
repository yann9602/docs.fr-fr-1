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
ms.openlocfilehash: 4cf66026ecf92d0158a1010e82c078478c280f9b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="corgcstattypes-enumeration"></a><span data-ttu-id="045f0-102">COR_GC_STAT_TYPES (énumération)</span><span class="sxs-lookup"><span data-stu-id="045f0-102">COR_GC_STAT_TYPES Enumeration</span></span>
<span data-ttu-id="045f0-103">Spécifie les statistiques à enregistrer pour un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="045f0-103">Specifies the statistics to be recorded for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="045f0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="045f0-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a><span data-ttu-id="045f0-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="045f0-105">Remarks</span></span>  
 <span data-ttu-id="045f0-106">Cette énumération spécifie les statistiques de la [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure doivent être définies par [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="045f0-106">This enumeration specifies which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set by [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method.</span></span>  
  
## <a name="members"></a><span data-ttu-id="045f0-107">Membres</span><span class="sxs-lookup"><span data-stu-id="045f0-107">Members</span></span>  
  
|<span data-ttu-id="045f0-108">Membre</span><span class="sxs-lookup"><span data-stu-id="045f0-108">Member</span></span>|<span data-ttu-id="045f0-109">Description</span><span class="sxs-lookup"><span data-stu-id="045f0-109">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_COUNTS`|<span data-ttu-id="045f0-110">Enregistre le nombre de garbage collections effectués pour chaque génération.</span><span class="sxs-lookup"><span data-stu-id="045f0-110">Records the number of garbage collections performed for each generation.</span></span>|  
|`COR_GC_MEMORYUSAGE`|<span data-ttu-id="045f0-111">Enregistrements d’utilisation et l’opération garbage collection taille statistiques de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="045f0-111">Records memory usage and garbage collection size statistics.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="045f0-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="045f0-112">Requirements</span></span>  
 <span data-ttu-id="045f0-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="045f0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="045f0-114">**En-tête :** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="045f0-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="045f0-115">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="045f0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="045f0-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="045f0-116">See Also</span></span>  
 [<span data-ttu-id="045f0-117">COR_GC_STATS (Structure)</span><span class="sxs-lookup"><span data-stu-id="045f0-117">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [<span data-ttu-id="045f0-118">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="045f0-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
