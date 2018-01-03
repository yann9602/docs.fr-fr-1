---
title: "ICorDebugStaticFieldSymbol::GetSize, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b67cbe6858e91e089c36047d6ed83743e45e1d1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="f5fe7-102">ICorDebugStaticFieldSymbol::GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="f5fe7-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="f5fe7-103">Obtient la taille en octets du champ static.</span><span class="sxs-lookup"><span data-stu-id="f5fe7-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5fe7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5fe7-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f5fe7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f5fe7-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="f5fe7-106">[out] Pointeur vers la longueur du champ.</span><span class="sxs-lookup"><span data-stu-id="f5fe7-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5fe7-107">Notes</span><span class="sxs-lookup"><span data-stu-id="f5fe7-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f5fe7-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f5fe7-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5fe7-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f5fe7-109">Requirements</span></span>  
 <span data-ttu-id="f5fe7-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5fe7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5fe7-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f5fe7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5fe7-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5fe7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5fe7-113">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5fe7-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5fe7-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5fe7-114">See Also</span></span>  
 [<span data-ttu-id="f5fe7-115">ICorDebugStaticFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="f5fe7-115">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="f5fe7-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f5fe7-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
