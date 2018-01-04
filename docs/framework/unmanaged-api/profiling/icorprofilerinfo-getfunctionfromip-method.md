---
title: "ICorProfilerInfo::GetFunctionFromIP, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetFunctionFromIP
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetFunctionFromIP
helpviewer_keywords:
- GetFunctionFromIP method [.NET Framework profiling]
- ICorProfilerInfo::GetFunctionFromIP method [.NET Framework profiling]
ms.assetid: f069802a-198f-46dd-9f09-4f77adffc9ba
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 144d80bb0e4111e319427d6a265d199b04b7f863
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetfunctionfromip-method"></a><span data-ttu-id="9c0de-102">ICorProfilerInfo::GetFunctionFromIP, méthode</span><span class="sxs-lookup"><span data-stu-id="9c0de-102">ICorProfilerInfo::GetFunctionFromIP Method</span></span>
<span data-ttu-id="9c0de-103">Mappe un pointeur d’instruction de code managé à un `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="9c0de-103">Maps a managed code instruction pointer to a `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c0de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c0de-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromIP(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9c0de-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9c0de-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="9c0de-106">[in] Le pointeur d’instruction dans le code managé.</span><span class="sxs-lookup"><span data-stu-id="9c0de-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="9c0de-107">[out] L’ID de fonction retourné.</span><span class="sxs-lookup"><span data-stu-id="9c0de-107">[out] The returned function ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c0de-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9c0de-108">Requirements</span></span>  
 <span data-ttu-id="9c0de-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c0de-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c0de-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9c0de-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9c0de-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c0de-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c0de-112">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c0de-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c0de-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c0de-113">See Also</span></span>  
 [<span data-ttu-id="9c0de-114">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="9c0de-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
