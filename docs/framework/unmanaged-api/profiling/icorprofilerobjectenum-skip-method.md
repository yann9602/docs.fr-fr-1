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
ms.workload: dotnet
ms.openlocfilehash: 607db61b25bafed841a81e8578438f4f70d4ee03
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="23d83-102">ICorProfilerObjectEnum::Skip, méthode</span><span class="sxs-lookup"><span data-stu-id="23d83-102">ICorProfilerObjectEnum::Skip Method</span></span>
<span data-ttu-id="23d83-103">Avance le curseur de cet énumérateur depuis sa position actuelle afin que le nombre spécifié d’éléments soit ignoré.</span><span class="sxs-lookup"><span data-stu-id="23d83-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23d83-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23d83-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="23d83-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="23d83-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="23d83-106">[in] Le nombre d’éléments à ignorer.</span><span class="sxs-lookup"><span data-stu-id="23d83-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23d83-107">Notes</span><span class="sxs-lookup"><span data-stu-id="23d83-107">Remarks</span></span>  
 <span data-ttu-id="23d83-108">La nouvelle position du curseur de cet énumérateur est : (position actuelle) + `celt` .</span><span class="sxs-lookup"><span data-stu-id="23d83-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23d83-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="23d83-109">Requirements</span></span>  
 <span data-ttu-id="23d83-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23d83-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23d83-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="23d83-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="23d83-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23d83-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23d83-113">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23d83-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23d83-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23d83-114">See Also</span></span>  
 [<span data-ttu-id="23d83-115">ICorProfilerObjectEnum, interface</span><span class="sxs-lookup"><span data-stu-id="23d83-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
