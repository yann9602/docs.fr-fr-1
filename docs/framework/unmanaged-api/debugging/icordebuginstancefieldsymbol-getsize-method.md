---
title: "ICorDebugInstanceFieldSymbol::GetSize, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ad13dbe8148d4d9507c6a450d2833da049e0e13a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="cdf20-102">ICorDebugInstanceFieldSymbol::GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="cdf20-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="cdf20-103">Obtient la taille en octets du champ d'instance.</span><span class="sxs-lookup"><span data-stu-id="cdf20-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdf20-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cdf20-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cdf20-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cdf20-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="cdf20-106">[out] Pointeur vers la longueur du champ.</span><span class="sxs-lookup"><span data-stu-id="cdf20-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cdf20-107">Notes</span><span class="sxs-lookup"><span data-stu-id="cdf20-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cdf20-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="cdf20-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdf20-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cdf20-109">Requirements</span></span>  
 <span data-ttu-id="cdf20-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cdf20-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdf20-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cdf20-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cdf20-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cdf20-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cdf20-113">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdf20-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdf20-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cdf20-114">See Also</span></span>  
 [<span data-ttu-id="cdf20-115">ICorDebugInstanceFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="cdf20-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="cdf20-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="cdf20-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
