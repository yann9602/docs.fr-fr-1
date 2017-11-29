---
title: "ICorDebugILFrame4::GetLocalVariableEx, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugILFrame4.GetCodeEx
api_location: mscordbi.dll
api_type: COM
ms.assetid: 0c8676f8-ca0d-4998-b64d-fefac7e38912
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: eca9919555d0ee7c4398ecff51f9a6ee3936a41b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugilframe4getlocalvariableex-method"></a><span data-ttu-id="865c1-102">ICorDebugILFrame4::GetLocalVariableEx, méthode</span><span class="sxs-lookup"><span data-stu-id="865c1-102">ICorDebugILFrame4::GetLocalVariableEx Method</span></span>
<span data-ttu-id="865c1-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="865c1-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="865c1-104">Extrait la valeur de la variable locale spécifiée dans ce frame de pile de langage intermédiaire, et peut aussi accéder à une variable ajoutée dans l'instrumentation ReJIT du profileur.</span><span class="sxs-lookup"><span data-stu-id="865c1-104">Gets the value of the specified local variable in this intermediate language (IL) stack frame, and optionally accesses a variable added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="865c1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="865c1-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,   
   [in] DWORD dwIndex,   
   [out] ICorDebugValue **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="865c1-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="865c1-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="865c1-107">[in] Un [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) membre d’énumération qui spécifie si une variable ajoutée dans l’instrumentation ReJIT du profileur est incluse dans le frame.</span><span class="sxs-lookup"><span data-stu-id="865c1-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether a variable added in profiler ReJIT instrumentation is included in the frame.</span></span>  
  
 `dwIndex`  
 <span data-ttu-id="865c1-108">[en entrée] L'index de la variable locale dans le frame de pile de langage intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="865c1-108">[in] The index of the local variable in the IL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="865c1-109">[out] Pointeur vers l’adresse d’un objet « ICorDebugValue » qui représente la valeur récupérée.</span><span class="sxs-lookup"><span data-stu-id="865c1-109">[out] A pointer to the address of an "ICorDebugValue" object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="865c1-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="865c1-110">Remarks</span></span>  
 <span data-ttu-id="865c1-111">Cette méthode est similaire à la [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) (méthode), à ceci près qu’elle peut aussi accéder à une variable ajoutée dans l’instrumentation ReJIT du profileur.</span><span class="sxs-lookup"><span data-stu-id="865c1-111">This method is similar to the [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) method, except that it optionally accesses a variable added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="865c1-112">Appel de cette méthode avec un `flags` valeur `ILCODE_ORIGINAL_IL` équivaut à appeler la méthode [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); si la méthode est instrumentée avec des variables locales supplémentaires, ces variables ne sont pas accessibles.</span><span class="sxs-lookup"><span data-stu-id="865c1-112">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); if the method is instrumented with additional local variables, those variables cannot be accessed.</span></span> <span data-ttu-id="865c1-113">`ILCODE_REJIT_IL` autorise le débogueur à accéder aux variables locales ajoutées dans l'instrumentation ReJIT du profileur.</span><span class="sxs-lookup"><span data-stu-id="865c1-113">`ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="865c1-114">Si le langage intermédiaire n'est pas instrumenté, la méthode retourne `E_INVALIDARG`.</span><span class="sxs-lookup"><span data-stu-id="865c1-114">If the IL is not instrumented, the method returns `E_INVALIDARG`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="865c1-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="865c1-115">Requirements</span></span>  
 <span data-ttu-id="865c1-116">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="865c1-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="865c1-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="865c1-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="865c1-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="865c1-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="865c1-119">**Versions du .NET framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="865c1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="865c1-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="865c1-120">See Also</span></span>  
 [<span data-ttu-id="865c1-121">Icordebugilframe4, Interface</span><span class="sxs-lookup"><span data-stu-id="865c1-121">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [<span data-ttu-id="865c1-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="865c1-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="865c1-123">ReJIT : Un Guide de procédures relatives</span><span class="sxs-lookup"><span data-stu-id="865c1-123">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
