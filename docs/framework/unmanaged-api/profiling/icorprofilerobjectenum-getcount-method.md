---
title: "ICorProfilerObjectEnum::GetCount, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerObjectEnum.GetCount
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerObjectEnum::GetCount
helpviewer_keywords:
- ICorProfilerObjectEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: 166b0761-ed80-4ccd-9973-dc20e61bf8fa
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0680921a64d8f8bf9cdc5b4137c56dd8dfb7878e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerobjectenumgetcount-method"></a><span data-ttu-id="57cd5-102">ICorProfilerObjectEnum::GetCount, méthode</span><span class="sxs-lookup"><span data-stu-id="57cd5-102">ICorProfilerObjectEnum::GetCount Method</span></span>
<span data-ttu-id="57cd5-103">Obtient le nombre total d’objets figés dans la collection.</span><span class="sxs-lookup"><span data-stu-id="57cd5-103">Gets the total number of frozen objects in the collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57cd5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57cd5-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="57cd5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="57cd5-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="57cd5-106">[out] Pointeur vers le nombre d’objets figés dans la collection.</span><span class="sxs-lookup"><span data-stu-id="57cd5-106">[out] A pointer to the number of frozen objects in the collection.</span></span>  
  
 <span data-ttu-id="57cd5-107">Cette méthode retourne toujours zéro dans le .NET Framework version 3.5 Service Pack 1 (SP1) et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="57cd5-107">This method will always return zero in the .NET Framework version 3.5 Service Pack 1 (SP1) and later versions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57cd5-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="57cd5-108">Requirements</span></span>  
 <span data-ttu-id="57cd5-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57cd5-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57cd5-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="57cd5-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="57cd5-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57cd5-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57cd5-112">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57cd5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57cd5-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57cd5-113">See Also</span></span>  
 [<span data-ttu-id="57cd5-114">ICorProfilerObjectEnum (Interface)</span><span class="sxs-lookup"><span data-stu-id="57cd5-114">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
