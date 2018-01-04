---
title: "ICorProfilerInfo2::GetBoxClassLayout, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetBoxClassLayout
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetBoxClassLayout
helpviewer_keywords:
- GetBoxClassLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetBoxClassLayout method [.NET Framework profiling]
ms.assetid: 624672b5-1189-488a-85d2-3e12b49617c1
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9ef6df997a4ba4369b87789e47ac7ead2206162e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getboxclasslayout-method"></a><span data-ttu-id="e09c4-102">ICorProfilerInfo2::GetBoxClassLayout, méthode</span><span class="sxs-lookup"><span data-stu-id="e09c4-102">ICorProfilerInfo2::GetBoxClassLayout Method</span></span>
<span data-ttu-id="e09c4-103">Obtient des informations sur l’emplacement du type valeur spécifié lorsqu’elle est convertie (boxed).</span><span class="sxs-lookup"><span data-stu-id="e09c4-103">Gets information about where the specified value type is located when it is boxed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e09c4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e09c4-104">Syntax</span></span>  
  
```  
HRESULT GetBoxClassLayout(  
    [in] ClassID classId,  
    [out] ULONG32 *pBufferOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e09c4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e09c4-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="e09c4-106">[in] L’ID de la classe qui décrit le type valeur boxed.</span><span class="sxs-lookup"><span data-stu-id="e09c4-106">[in] The ID of the class that describes the value type that is boxed.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="e09c4-107">[out] Entier qui est l’offset par rapport à l’objet boxed pointeur d’ID le type de valeur.</span><span class="sxs-lookup"><span data-stu-id="e09c4-107">[out] An integer that is the offset, relative to the boxed object ID pointer, of the value type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e09c4-108">Notes</span><span class="sxs-lookup"><span data-stu-id="e09c4-108">Remarks</span></span>  
 <span data-ttu-id="e09c4-109">Le `pBufferOffset` valeur est l’emplacement d’un type valeur dans une zone.</span><span class="sxs-lookup"><span data-stu-id="e09c4-109">The `pBufferOffset` value is the location of the value type within a box.</span></span> <span data-ttu-id="e09c4-110">Après avoir `pBufferOffset` est appliqué à un objet boxed, la présentation de classe de la valeur du type peut être utilisée pour interpréter la valeur de l’objet.</span><span class="sxs-lookup"><span data-stu-id="e09c4-110">After `pBufferOffset` is applied to a boxed object, the value type's class layout can be used to interpret the object's value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e09c4-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e09c4-111">Requirements</span></span>  
 <span data-ttu-id="e09c4-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e09c4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e09c4-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e09c4-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e09c4-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e09c4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e09c4-115">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e09c4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e09c4-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e09c4-116">See Also</span></span>  
 [<span data-ttu-id="e09c4-117">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="e09c4-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="e09c4-118">ICorProfilerInfo2, interface</span><span class="sxs-lookup"><span data-stu-id="e09c4-118">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
