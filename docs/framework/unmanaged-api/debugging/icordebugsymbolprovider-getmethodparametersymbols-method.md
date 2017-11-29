---
title: "ICorDebugSymbolProvider::GetMethodParameterSymbols, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 58b7c0b9-f6ad-4b49-b92d-0e421cfd0ec6
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4b0b55caec333bc1e69dae9eee59ba30b6671737
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovidergetmethodparametersymbols-method"></a><span data-ttu-id="d35bf-102">ICorDebugSymbolProvider::GetMethodParameterSymbols, méthode</span><span class="sxs-lookup"><span data-stu-id="d35bf-102">ICorDebugSymbolProvider::GetMethodParameterSymbols Method</span></span>
<span data-ttu-id="d35bf-103">Obtient les symboles de paramètre d'une méthode en fonction de l'adresse virtuelle relative (RVA) de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="d35bf-103">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d35bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d35bf-104">Syntax</span></span>  
  
```  
HRESULT GetMethodParameterSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d35bf-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d35bf-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="d35bf-106">[in] Adresse virtuelle relative native de la méthode.</span><span class="sxs-lookup"><span data-stu-id="d35bf-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="d35bf-107">[in] Nombre de symboles locaux demandés.</span><span class="sxs-lookup"><span data-stu-id="d35bf-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="d35bf-108">[out] Pointeur vers le nombre de symboles récupérés par la méthode.</span><span class="sxs-lookup"><span data-stu-id="d35bf-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="d35bf-109">[out] Un pointeur vers un [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) tableau qui contient les symboles locaux de la méthode.</span><span class="sxs-lookup"><span data-stu-id="d35bf-109">[out] A pointer to an [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d35bf-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="d35bf-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d35bf-111">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d35bf-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d35bf-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d35bf-112">Requirements</span></span>  
 <span data-ttu-id="d35bf-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d35bf-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d35bf-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d35bf-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d35bf-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d35bf-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d35bf-116">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d35bf-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d35bf-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d35bf-117">See Also</span></span>  
 [<span data-ttu-id="d35bf-118">GetMethodLocalSymbols (méthode)</span><span class="sxs-lookup"><span data-stu-id="d35bf-118">GetMethodLocalSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)  
 [<span data-ttu-id="d35bf-119">Icordebugsymbolprovider, Interface</span><span class="sxs-lookup"><span data-stu-id="d35bf-119">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="d35bf-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="d35bf-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
