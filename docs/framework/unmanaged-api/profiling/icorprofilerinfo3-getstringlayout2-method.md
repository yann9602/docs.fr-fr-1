---
title: "ICorProfilerInfo3::GetStringLayout2, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.GetStringLayout2 Method
api_location: Mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::GetStringLayout2
helpviewer_keywords:
- ICorProfilerInfo3::GetStringLayout2 method [.NET Framework profiling]
- GetStringLayout2 method [.NET Framework profiling]
ms.assetid: 1a268496-ee51-4d84-8700-ee56fd0c499d
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: de89776c6208ec7e3434fa747057edbf818ec013
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a><span data-ttu-id="7e559-102">ICorProfilerInfo3::GetStringLayout2, méthode</span><span class="sxs-lookup"><span data-stu-id="7e559-102">ICorProfilerInfo3::GetStringLayout2 Method</span></span>
<span data-ttu-id="7e559-103">Obtient des informations sur la disposition d'un objet string.</span><span class="sxs-lookup"><span data-stu-id="7e559-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="7e559-104">Cette méthode remplace la [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="7e559-104">This method supersedes the [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e559-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e559-105">Syntax</span></span>  
  
```  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7e559-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7e559-106">Parameters</span></span>  
 `pStringLengthOffset`  
 <span data-ttu-id="7e559-107">[out] Un pointeur vers l’offset de l’emplacement, relatif à la `ObjectID` pointeur, qui stocke la longueur de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="7e559-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="7e559-108">La longueur est stockée comme un `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="7e559-108">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="7e559-109">[out] Un pointeur vers l’offset de la mémoire tampon, relative à la `ObjectID` pointeur, qui stocke la chaîne de caractères larges.</span><span class="sxs-lookup"><span data-stu-id="7e559-109">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e559-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="7e559-110">Remarks</span></span>  
 <span data-ttu-id="7e559-111">Les chaînes peuvent ou ne peuvent pas être terminée par null.</span><span class="sxs-lookup"><span data-stu-id="7e559-111">Strings may or may not be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e559-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7e559-112">Requirements</span></span>  
 <span data-ttu-id="7e559-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e559-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e559-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7e559-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7e559-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e559-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e559-116">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e559-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e559-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e559-117">See Also</span></span>  
 [<span data-ttu-id="7e559-118">ICorProfilerInfo3 (Interface)</span><span class="sxs-lookup"><span data-stu-id="7e559-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="7e559-119">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="7e559-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
