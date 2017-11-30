---
title: "Méthode ICorDebugVariableSymbol::SetValue"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 12c13259d20301b0f485a6041fa884b0996cbbdc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablesymbolsetvalue-method"></a><span data-ttu-id="f5ec3-102">Méthode ICorDebugVariableSymbol::SetValue</span><span class="sxs-lookup"><span data-stu-id="f5ec3-102">ICorDebugVariableSymbol::SetValue Method</span></span>
<span data-ttu-id="f5ec3-103">Affecte la valeur d'un tableau d'octets à une variable.</span><span class="sxs-lookup"><span data-stu-id="f5ec3-103">Assigns the value of a byte array to a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5ec3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5ec3-104">Syntax</span></span>  
  
```  
HRESULT SetValue(  
   [in] ULONG32 offset,  
   [in] DWORD threadID,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [in, size_is(cbValue)] BYTE pValue[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f5ec3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f5ec3-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="f5ec3-106">[in] Offset de démarrage dans la variable au niveau duquel définir la valeur.</span><span class="sxs-lookup"><span data-stu-id="f5ec3-106">[in] The starting offset in the variable at which to set the value.</span></span> <span data-ttu-id="f5ec3-107">Ce paramètre est utilisé lors de l'écriture dans des champs membres d'un objet.</span><span class="sxs-lookup"><span data-stu-id="f5ec3-107">This parameter is used when writing to member fields in an object.</span></span>  
  
 `threadID`  
 <span data-ttu-id="f5ec3-108">[in] Identificateur du thread dont le contexte doit être mis à jour pour refléter la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="f5ec3-108">[in] The thread identifier of the thread whose context must be updated to reflect the new value.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="f5ec3-109">[in] Taille en octets du contexte de thread.</span><span class="sxs-lookup"><span data-stu-id="f5ec3-109">[in] The size in bytes of the thread context.</span></span>  
  
 `context`  
 <span data-ttu-id="f5ec3-110">[in] Contexte de thread utilisé pour écrire la valeur.</span><span class="sxs-lookup"><span data-stu-id="f5ec3-110">[in] The thread context used to write the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="f5ec3-111">[in] Taille en octets de la mémoire tampon `pValue`.</span><span class="sxs-lookup"><span data-stu-id="f5ec3-111">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="f5ec3-112">[in] Mémoire tampon contenant la valeur à définir.</span><span class="sxs-lookup"><span data-stu-id="f5ec3-112">[in] The buffer that contains the value to set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5ec3-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="f5ec3-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f5ec3-114">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f5ec3-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5ec3-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f5ec3-115">Requirements</span></span>  
 <span data-ttu-id="f5ec3-116">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5ec3-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5ec3-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f5ec3-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5ec3-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5ec3-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5ec3-119">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5ec3-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5ec3-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5ec3-120">See Also</span></span>  
 [<span data-ttu-id="f5ec3-121">Icordebugvariablesymbol, Interface</span><span class="sxs-lookup"><span data-stu-id="f5ec3-121">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="f5ec3-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f5ec3-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
