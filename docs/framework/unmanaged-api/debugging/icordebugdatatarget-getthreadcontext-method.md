---
title: "ICorDebugDataTarget::GetThreadContext, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugDataTarget.GetThreadContext Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugDataTarget::GetThreadContext
helpviewer_keywords:
- ICorDebugDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: c8954268-1821-4b23-b665-dbb55f2af31b
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 543956bb42d7477456426d7327f14b059b23d759
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a><span data-ttu-id="85558-102">ICorDebugDataTarget::GetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="85558-102">ICorDebugDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="85558-103">Retourne le contexte actuel du thread pour le thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="85558-103">Returns the current thread context for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85558-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85558-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="85558-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="85558-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="85558-106">[in] L’identificateur du thread dont le contexte doit être récupéré.</span><span class="sxs-lookup"><span data-stu-id="85558-106">[in] The identifier of the thread whose context is to be retrieved.</span></span> <span data-ttu-id="85558-107">L’identificateur est défini par le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="85558-107">The identifier is defined by the operating system.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="85558-108">[in] Combinaison de bits d’indicateurs dépend de la plateforme qui indiquent les parties du contexte doivent être lue.</span><span class="sxs-lookup"><span data-stu-id="85558-108">[in] A bitwise combination of platform-dependent flags that indicate which portions of the context should be read.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="85558-109">[in] Taille de `pContext`.</span><span class="sxs-lookup"><span data-stu-id="85558-109">[in] The size of `pContext`.</span></span>  
  
 `pContext`  
 <span data-ttu-id="85558-110">[out] La mémoire tampon où sera stocké le contexte du thread.</span><span class="sxs-lookup"><span data-stu-id="85558-110">[out] The buffer where the thread context will be stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85558-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="85558-111">Remarks</span></span>  
 <span data-ttu-id="85558-112">Sur les plateformes Windows, `pContext` doit être un `CONTEXT` structure (définie dans WinNT.h) qui est appropriée pour le type d’ordinateur spécifié par le [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="85558-112">On Windows platforms, `pContext` must be a `CONTEXT` structure (defined in WinNT.h) that is appropriate for the machine type specified by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="85558-113">`contextFlags`doit avoir les mêmes valeurs que le `ContextFlags` champ le `CONTEXT` structure.</span><span class="sxs-lookup"><span data-stu-id="85558-113">`contextFlags` must have the same values as the `ContextFlags` field of the `CONTEXT` structure.</span></span> <span data-ttu-id="85558-114">Le `CONTEXT` structure est spécifique au processeur ; consultez le fichier WinNT.h pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="85558-114">The `CONTEXT` structure is processor-specific; refer to the WinNT.h file for details.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85558-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="85558-115">Requirements</span></span>  
 <span data-ttu-id="85558-116">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85558-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85558-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="85558-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85558-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85558-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85558-119">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85558-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85558-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85558-120">See Also</span></span>  
 [<span data-ttu-id="85558-121">ICorDebugDataTarget (Interface)</span><span class="sxs-lookup"><span data-stu-id="85558-121">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [<span data-ttu-id="85558-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="85558-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="85558-123">Débogage</span><span class="sxs-lookup"><span data-stu-id="85558-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
