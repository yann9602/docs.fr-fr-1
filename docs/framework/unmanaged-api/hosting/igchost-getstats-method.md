---
title: "IGCHost::GetStats, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHost.GetStats
api_location: mscoree.dll
api_type: COM
f1_keywords: GetStats
helpviewer_keywords:
- GetStats method, IGCHost interface [.NET Framework hosting]
- IGCHost::GetStats method [.NET Framework hosting]
ms.assetid: c4ae022c-46ac-4f19-9ddd-09b955f19412
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6c8db4f854b73d04e7260457c978a7a644677559
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="igchostgetstats-method"></a><span data-ttu-id="f6457-102">IGCHost::GetStats, méthode</span><span class="sxs-lookup"><span data-stu-id="f6457-102">IGCHost::GetStats Method</span></span>
<span data-ttu-id="f6457-103">Obtient les statistiques de l’état actuel du système de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="f6457-103">Gets the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6457-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6457-104">Syntax</span></span>  
  
```  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f6457-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f6457-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="f6457-106">[dans, out] Un pointeur vers un [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure qui contient les statistiques de l’état actuel du système de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="f6457-106">[in, out] A pointer to a [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure that contains the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6457-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="f6457-107">Remarks</span></span>  
 <span data-ttu-id="f6457-108">Les statistiques peuvent être utilisées par un système intelligent d’allocation pour utiliser le système de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="f6457-108">The statistics can be used by a smart allocation system to help the garbage collection system operate.</span></span> <span data-ttu-id="f6457-109">Par exemple, le système d’allocation peut déterminer, après avoir examiné les statistiques, il doit ajouter davantage de mémoire ou forcer une collection.</span><span class="sxs-lookup"><span data-stu-id="f6457-109">For example, the allocation system may determine, after reviewing the statistics, that it needs to add more memory or force a collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6457-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f6457-110">Requirements</span></span>  
 <span data-ttu-id="f6457-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6457-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6457-112">**En-tête :** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="f6457-112">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="f6457-113">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f6457-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f6457-114">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6457-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6457-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6457-115">See Also</span></span>  
 [<span data-ttu-id="f6457-116">IGCHost (Interface)</span><span class="sxs-lookup"><span data-stu-id="f6457-116">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
