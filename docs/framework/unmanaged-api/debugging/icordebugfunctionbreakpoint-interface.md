---
title: ICorDebugFunctionBreakpoint Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunctionBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunctionBreakpoint
helpviewer_keywords: ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: 9c149303-14b1-4138-83d7-e8c3e0fcd332
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 910317bea8af3a80ee66544651de2372808734bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunctionbreakpoint-interface1"></a><span data-ttu-id="f6c27-102">ICorDebugFunctionBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="f6c27-102">ICorDebugFunctionBreakpoint Interface1</span></span>
<span data-ttu-id="f6c27-103">Étend l’interface ICorDebugBreakpoint pour prendre en charge les points d’arrêt dans les fonctions.</span><span class="sxs-lookup"><span data-stu-id="f6c27-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f6c27-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f6c27-104">Methods</span></span>  
  
|<span data-ttu-id="f6c27-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="f6c27-105">Method</span></span>|<span data-ttu-id="f6c27-106">Description</span><span class="sxs-lookup"><span data-stu-id="f6c27-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f6c27-107">GetFunction, méthode</span><span class="sxs-lookup"><span data-stu-id="f6c27-107">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="f6c27-108">Obtient un pointeur d’interface ICorDebugFunction qui référence la fonction dans laquelle le point d’arrêt est défini.</span><span class="sxs-lookup"><span data-stu-id="f6c27-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="f6c27-109">GetOffset (méthode)</span><span class="sxs-lookup"><span data-stu-id="f6c27-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="f6c27-110">Obtient l’offset du point d’arrêt dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="f6c27-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6c27-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="f6c27-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6c27-112">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="f6c27-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6c27-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f6c27-113">Requirements</span></span>  
 <span data-ttu-id="f6c27-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6c27-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6c27-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f6c27-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6c27-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6c27-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6c27-117">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6c27-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6c27-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6c27-118">See Also</span></span>  
 [<span data-ttu-id="f6c27-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f6c27-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
