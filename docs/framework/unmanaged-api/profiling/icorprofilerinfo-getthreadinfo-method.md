---
title: "ICorProfilerInfo::GetThreadInfo, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetThreadInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetThreadInfo
helpviewer_keywords:
- ICorProfilerInfo::GetThreadInfo method [.NET Framework profiling]
- GetThreadInfo method [.NET Framework profiling]
ms.assetid: fc994fef-65c9-432a-84cb-66c8141147e7
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4c4657279e145dbb923c339ed0114723620e7aa7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetthreadinfo-method"></a><span data-ttu-id="0a226-102">ICorProfilerInfo::GetThreadInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="0a226-102">ICorProfilerInfo::GetThreadInfo Method</span></span>
<span data-ttu-id="0a226-103">Obtient l’identité de thread Win32 actuelle pour le thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="0a226-103">Gets the current Win32 thread identity for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a226-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a226-104">Syntax</span></span>  
  
```  
HRESULT GetThreadInfo(  
    [in]  ThreadID threadId,  
    [out] DWORD    *pdwWin32ThreadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0a226-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0a226-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="0a226-106">[in] L’ID du thread pour lequel obtenir l’ID Win32 actuel.</span><span class="sxs-lookup"><span data-stu-id="0a226-106">[in] The ID of the thread for which to get the current Win32 ID.</span></span>  
  
 `pdwWin32ThreadId`  
 <span data-ttu-id="0a226-107">[out] ID un pointeur vers le thread de Win32 actuel du thread spécifié d'.</span><span class="sxs-lookup"><span data-stu-id="0a226-107">[out] A pointer to the specified thread's current Win32 thread ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a226-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0a226-108">Requirements</span></span>  
 <span data-ttu-id="0a226-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a226-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a226-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0a226-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0a226-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a226-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a226-112">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a226-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a226-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a226-113">See Also</span></span>  
 [<span data-ttu-id="0a226-114">ICorProfilerInfo (Interface)</span><span class="sxs-lookup"><span data-stu-id="0a226-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
