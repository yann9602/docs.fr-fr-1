---
title: "ICorDebugILFrame4::GetCodeEx, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugILFrame4.GetLocalVariableEx
api_location: mscordbi.dll
api_type: COM
ms.assetid: aeda0e42-29ee-4ca8-9f21-ac4641677a62
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fc80882353bd7a9861f4db79b83493d1cef7bfee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugilframe4getcodeex-method"></a><span data-ttu-id="f2b4b-102">ICorDebugILFrame4::GetCodeEx, méthode</span><span class="sxs-lookup"><span data-stu-id="f2b4b-102">ICorDebugILFrame4::GetCodeEx Method</span></span>
<span data-ttu-id="f2b4b-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="f2b4b-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="f2b4b-104">Obtient un pointeur vers le code exécuté par ce frame de pile.</span><span class="sxs-lookup"><span data-stu-id="f2b4b-104">Gets a pointer to the code that this stack frame is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2b4b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2b4b-105">Syntax</span></span>  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f2b4b-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f2b4b-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="f2b4b-107">[in] Un [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) membre d’énumération qui spécifie si le langage intermédiaire (IL) défini par la demande de ReJIT du profileur est inclus dans le frame.</span><span class="sxs-lookup"><span data-stu-id="f2b4b-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether the intermediate language (IL) defined by the profiler's ReJIT request is included in the frame.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="f2b4b-108">[out] Pointeur vers l’adresse d’un objet « ICorDebugCode » qui représente le code de ce frame de pile en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="f2b4b-108">[out] A pointer to the address of an "ICorDebugCode" object that represents the code that this stack frame is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2b4b-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="f2b4b-109">Remarks</span></span>  
 <span data-ttu-id="f2b4b-110">Cette méthode est similaire à la [ICorDebugFrame::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) (méthode), à ceci près qu’elle peut éventuellement accéder au code défini par la demande de ReJIT du profileur.</span><span class="sxs-lookup"><span data-stu-id="f2b4b-110">This method is similar to the [ICorDebugFrame::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) method, except that it optionally accesses code defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="f2b4b-111">Appel de cette méthode avec un `flags` valeur `ILCODE_ORIGINAL_IL` équivaut à appeler la méthode [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); si la méthode est instrumentée, son langage intermédiaire ne sera pas accessible.</span><span class="sxs-lookup"><span data-stu-id="f2b4b-111">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); if the method is instrumented, its IL will not be accessible.</span></span> <span data-ttu-id="f2b4b-112">`ILCODE_REJIT_IL` permet au débogueur d'accéder au langage intermédiaire défini par la demande ReJIT du profileur.</span><span class="sxs-lookup"><span data-stu-id="f2b4b-112">`ILCODE_REJIT_IL` allows the debugger to access the IL defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="f2b4b-113">Si le langage intermédiaire n’est pas instrumenté, `ppCode` est **null**, et la méthode retourne `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="f2b4b-113">If the IL is not instrumented, `ppCode` is **null**, and the method returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2b4b-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f2b4b-114">Requirements</span></span>  
 <span data-ttu-id="f2b4b-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2b4b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2b4b-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2b4b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2b4b-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2b4b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2b4b-118">**Versions du .NET framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2b4b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2b4b-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2b4b-119">See Also</span></span>  
 [<span data-ttu-id="f2b4b-120">Icordebugilframe4, Interface</span><span class="sxs-lookup"><span data-stu-id="f2b4b-120">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [<span data-ttu-id="f2b4b-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f2b4b-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="f2b4b-122">ReJIT : Un Guide de procédures relatives</span><span class="sxs-lookup"><span data-stu-id="f2b4b-122">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
