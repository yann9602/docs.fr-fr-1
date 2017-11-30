---
title: "ICorDebugVirtualUnwinder::GetContext, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45a914005e84d33b39d72fce96679e275b921d3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvirtualunwindergetcontext-method"></a><span data-ttu-id="5cfe0-102">ICorDebugVirtualUnwinder::GetContext, méthode</span><span class="sxs-lookup"><span data-stu-id="5cfe0-102">ICorDebugVirtualUnwinder::GetContext Method</span></span>
<span data-ttu-id="5cfe0-103">Obtient le contexte actuel de ce dérouleur.</span><span class="sxs-lookup"><span data-stu-id="5cfe0-103">Gets the current context of this unwinder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cfe0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5cfe0-104">Syntax</span></span>  
  
```  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5cfe0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5cfe0-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="5cfe0-106">[in] Indicateurs spécifiant les parties du contexte à retourner (définition contenue dans WinNT.h).</span><span class="sxs-lookup"><span data-stu-id="5cfe0-106">[in] Flags that specify which parts of the context to return (defined in WinNT.h).</span></span>  
  
 `cbContextBuf`  
 <span data-ttu-id="5cfe0-107">[in] Nombre d'octets dans `contextBuf`.</span><span class="sxs-lookup"><span data-stu-id="5cfe0-107">[in] The number of bytes in `contextBuf`.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="5cfe0-108">[out] Pointeur vers le nombre d'octets réellement écrits dans `contextBuf`.</span><span class="sxs-lookup"><span data-stu-id="5cfe0-108">[out] A pointer to the number of bytes actually written to `contextBuf`.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="5cfe0-109">[out] Tableau d'octets contenant le contexte actuel de ce dérouleur.</span><span class="sxs-lookup"><span data-stu-id="5cfe0-109">[out] A byte array that contains the current context of this unwinder.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5cfe0-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="5cfe0-110">Return Value</span></span>  
 <span data-ttu-id="5cfe0-111">Toute valeur HRESULT indiquant un échec reçue par mscordbi est considérée comme irrécupérable et forcent les API ICorDebug à retourner `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="5cfe0-111">Any failing HRESULT value received by mscordbi is considered fatal and will cause ICorDebug APIs to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5cfe0-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="5cfe0-112">Remarks</span></span>  
 <span data-ttu-id="5cfe0-113">Vous affectez la valeur initiale de la `contextBuf` l’argument de la mémoire tampon de contexte retournée en appelant le [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="5cfe0-113">You set the initial value of the `contextBuf` argument to the context buffer returned by calling the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5cfe0-114">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5cfe0-114">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="5cfe0-115">Le déroulement ne pouvant restaurer qu'un sous-ensemble des registres, par exemple les registres non volatiles, le contexte peut différer de l'état du registre au moment de l'appel de la méthode.</span><span class="sxs-lookup"><span data-stu-id="5cfe0-115">Because unwinding may only restore a subset of the registers, such as the non-volatile registers only, the context may not exactly match the register state at the time of the actual method call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cfe0-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5cfe0-116">Requirements</span></span>  
 <span data-ttu-id="5cfe0-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cfe0-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cfe0-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5cfe0-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5cfe0-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5cfe0-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5cfe0-120">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cfe0-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cfe0-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5cfe0-121">See Also</span></span>  
 [<span data-ttu-id="5cfe0-122">Icordebugmemorybuffer, Interface</span><span class="sxs-lookup"><span data-stu-id="5cfe0-122">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="5cfe0-123">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="5cfe0-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
