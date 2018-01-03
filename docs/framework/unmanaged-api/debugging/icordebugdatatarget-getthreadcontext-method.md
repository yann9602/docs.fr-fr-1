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
ms.workload: dotnet
ms.openlocfilehash: 44543ca3546827b38643cab0e047032a96be9ea6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a><span data-ttu-id="a04b9-102">ICorDebugDataTarget::GetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="a04b9-102">ICorDebugDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="a04b9-103">Retourne le contexte actuel du thread pour le thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="a04b9-103">Returns the current thread context for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a04b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a04b9-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a04b9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a04b9-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="a04b9-106">[in] L’identificateur du thread dont le contexte doit être récupéré.</span><span class="sxs-lookup"><span data-stu-id="a04b9-106">[in] The identifier of the thread whose context is to be retrieved.</span></span> <span data-ttu-id="a04b9-107">L’identificateur est défini par le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="a04b9-107">The identifier is defined by the operating system.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="a04b9-108">[in] Combinaison de bits d’indicateurs dépend de la plateforme qui indiquent les parties du contexte doivent être lue.</span><span class="sxs-lookup"><span data-stu-id="a04b9-108">[in] A bitwise combination of platform-dependent flags that indicate which portions of the context should be read.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="a04b9-109">[in] Taille de `pContext`.</span><span class="sxs-lookup"><span data-stu-id="a04b9-109">[in] The size of `pContext`.</span></span>  
  
 `pContext`  
 <span data-ttu-id="a04b9-110">[out] La mémoire tampon où sera stocké le contexte du thread.</span><span class="sxs-lookup"><span data-stu-id="a04b9-110">[out] The buffer where the thread context will be stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a04b9-111">Notes</span><span class="sxs-lookup"><span data-stu-id="a04b9-111">Remarks</span></span>  
 <span data-ttu-id="a04b9-112">Sur les plateformes Windows, `pContext` doit être un `CONTEXT` structure (définie dans WinNT.h) qui est appropriée pour le type d’ordinateur spécifié par le [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="a04b9-112">On Windows platforms, `pContext` must be a `CONTEXT` structure (defined in WinNT.h) that is appropriate for the machine type specified by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="a04b9-113">`contextFlags`doit avoir les mêmes valeurs que le `ContextFlags` champ le `CONTEXT` structure.</span><span class="sxs-lookup"><span data-stu-id="a04b9-113">`contextFlags` must have the same values as the `ContextFlags` field of the `CONTEXT` structure.</span></span> <span data-ttu-id="a04b9-114">Le `CONTEXT` structure est spécifique au processeur ; consultez le fichier WinNT.h pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="a04b9-114">The `CONTEXT` structure is processor-specific; refer to the WinNT.h file for details.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a04b9-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a04b9-115">Requirements</span></span>  
 <span data-ttu-id="a04b9-116">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a04b9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a04b9-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a04b9-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a04b9-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a04b9-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a04b9-119">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a04b9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a04b9-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a04b9-120">See Also</span></span>  
 [<span data-ttu-id="a04b9-121">ICorDebugDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="a04b9-121">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [<span data-ttu-id="a04b9-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="a04b9-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="a04b9-123">Débogage</span><span class="sxs-lookup"><span data-stu-id="a04b9-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
