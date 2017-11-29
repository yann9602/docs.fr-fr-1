---
title: COR_GC_THREAD_STATS, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_GC_THREAD_STATS
api_location: mscoree.dll
api_type: COM
f1_keywords: COR_GC_THREAD_STATS
helpviewer_keywords: COR_GC_THREAD_STATS structure [.NET Framework hosting]
ms.assetid: 01f9a59b-7679-4d42-9ced-4a8981625c3d
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 10366d183ed7fd7386609e4c5726df0cea4e29a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="corgcthreadstats-structure"></a><span data-ttu-id="c20ee-102">COR_GC_THREAD_STATS, structure</span><span class="sxs-lookup"><span data-stu-id="c20ee-102">COR_GC_THREAD_STATS Structure</span></span>
<span data-ttu-id="c20ee-103">Contient des statistiques par thread concernant le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="c20ee-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c20ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c20ee-104">Syntax</span></span>  
  
```  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;   
    ULONG      Flags;   
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="c20ee-105">Membres</span><span class="sxs-lookup"><span data-stu-id="c20ee-105">Members</span></span>  
  
|<span data-ttu-id="c20ee-106">Membre</span><span class="sxs-lookup"><span data-stu-id="c20ee-106">Member</span></span>|<span data-ttu-id="c20ee-107">Description</span><span class="sxs-lookup"><span data-stu-id="c20ee-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="c20ee-108">Le nombre d’octets de mémoire alloués sur le thread qui est associé à l’actuel `COR_GC_THREAD_STATS` instance.</span><span class="sxs-lookup"><span data-stu-id="c20ee-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="c20ee-109">Ce nombre est remis à zéro chaque fois qu'un nettoyage de la génération zéro se produit.</span><span class="sxs-lookup"><span data-stu-id="c20ee-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="c20ee-110">Le nombre d’octets promus à une génération supérieure garbage collection le plus récent.</span><span class="sxs-lookup"><span data-stu-id="c20ee-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c20ee-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="c20ee-111">Remarks</span></span>  
 <span data-ttu-id="c20ee-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) prend un paramètre de sortie de type `COR_GC_THREAD_STATS`.</span><span class="sxs-lookup"><span data-stu-id="c20ee-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c20ee-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c20ee-113">Requirements</span></span>  
 <span data-ttu-id="c20ee-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c20ee-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c20ee-115">**En-tête :** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="c20ee-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="c20ee-116">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c20ee-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c20ee-117">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c20ee-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c20ee-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c20ee-118">See Also</span></span>  
 [<span data-ttu-id="c20ee-119">Structures d’hébergement</span><span class="sxs-lookup"><span data-stu-id="c20ee-119">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="c20ee-120">IHostTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="c20ee-120">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
