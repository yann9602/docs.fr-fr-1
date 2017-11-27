---
title: "ICorProfilerObjectEnum::Skip, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerObjectEnum.Skip
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerObjectEnum::Skip
helpviewer_keywords:
- ICorProfilerObjectEnum::Skip method [.NET Framework profiling]
- Skip method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: f8e498f8-f93a-4b82-bd22-55bdbf5e8d45
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 84960af6e128f3a6aa9e3b45187e282ac7228e0f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="ad27f-102">ICorProfilerObjectEnum::Skip, méthode</span><span class="sxs-lookup"><span data-stu-id="ad27f-102">ICorProfilerObjectEnum::Skip Method</span></span>
<span data-ttu-id="ad27f-103">Avance le curseur de cet énumérateur depuis sa position actuelle afin que le nombre spécifié d’éléments soit ignoré.</span><span class="sxs-lookup"><span data-stu-id="ad27f-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad27f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad27f-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad27f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ad27f-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="ad27f-106">[in] Le nombre d’éléments à ignorer.</span><span class="sxs-lookup"><span data-stu-id="ad27f-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad27f-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="ad27f-107">Remarks</span></span>  
 <span data-ttu-id="ad27f-108">La nouvelle position du curseur de cet énumérateur est : (position actuelle) + `celt` .</span><span class="sxs-lookup"><span data-stu-id="ad27f-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad27f-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ad27f-109">Requirements</span></span>  
 <span data-ttu-id="ad27f-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad27f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad27f-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ad27f-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ad27f-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad27f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad27f-113">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad27f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad27f-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad27f-114">See Also</span></span>  
 [<span data-ttu-id="ad27f-115">ICorProfilerObjectEnum (Interface)</span><span class="sxs-lookup"><span data-stu-id="ad27f-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
