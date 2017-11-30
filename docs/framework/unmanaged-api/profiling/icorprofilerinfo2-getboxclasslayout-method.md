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
ms.openlocfilehash: c11013781a4fc8f627dac97894ff9ef02bfda51c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getboxclasslayout-method"></a><span data-ttu-id="3a36e-102">ICorProfilerInfo2::GetBoxClassLayout, méthode</span><span class="sxs-lookup"><span data-stu-id="3a36e-102">ICorProfilerInfo2::GetBoxClassLayout Method</span></span>
<span data-ttu-id="3a36e-103">Obtient des informations sur l’emplacement du type valeur spécifié lorsqu’elle est convertie (boxed).</span><span class="sxs-lookup"><span data-stu-id="3a36e-103">Gets information about where the specified value type is located when it is boxed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a36e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a36e-104">Syntax</span></span>  
  
```  
HRESULT GetBoxClassLayout(  
    [in] ClassID classId,  
    [out] ULONG32 *pBufferOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3a36e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3a36e-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="3a36e-106">[in] L’ID de la classe qui décrit le type valeur boxed.</span><span class="sxs-lookup"><span data-stu-id="3a36e-106">[in] The ID of the class that describes the value type that is boxed.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="3a36e-107">[out] Entier qui est l’offset par rapport à l’objet boxed pointeur d’ID le type de valeur.</span><span class="sxs-lookup"><span data-stu-id="3a36e-107">[out] An integer that is the offset, relative to the boxed object ID pointer, of the value type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a36e-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="3a36e-108">Remarks</span></span>  
 <span data-ttu-id="3a36e-109">Le `pBufferOffset` valeur est l’emplacement d’un type valeur dans une zone.</span><span class="sxs-lookup"><span data-stu-id="3a36e-109">The `pBufferOffset` value is the location of the value type within a box.</span></span> <span data-ttu-id="3a36e-110">Après avoir `pBufferOffset` est appliqué à un objet boxed, la présentation de classe de la valeur du type peut être utilisée pour interpréter la valeur de l’objet.</span><span class="sxs-lookup"><span data-stu-id="3a36e-110">After `pBufferOffset` is applied to a boxed object, the value type's class layout can be used to interpret the object's value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a36e-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3a36e-111">Requirements</span></span>  
 <span data-ttu-id="3a36e-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a36e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a36e-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3a36e-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3a36e-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a36e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a36e-115">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a36e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a36e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a36e-116">See Also</span></span>  
 [<span data-ttu-id="3a36e-117">ICorProfilerInfo (Interface)</span><span class="sxs-lookup"><span data-stu-id="3a36e-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="3a36e-118">ICorProfilerInfo2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="3a36e-118">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
