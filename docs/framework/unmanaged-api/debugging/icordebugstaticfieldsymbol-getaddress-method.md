---
title: "ICorDebugStaticFieldSymbol::GetAddress, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5382a0b04a8a4d5adf9745d21b5bbcf629da1df3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="6a8fc-102">ICorDebugStaticFieldSymbol::GetAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="6a8fc-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="6a8fc-103">Obtient l’adresse d’un champ static.</span><span class="sxs-lookup"><span data-stu-id="6a8fc-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a8fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a8fc-104">Syntax</span></span>  
  
```  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6a8fc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6a8fc-105">Parameters</span></span>  
 <span data-ttu-id="6a8fc-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="6a8fc-106">pRVA</span></span>  
 <span data-ttu-id="6a8fc-107">[out] Pointeur vers l’adresse virtuelle relative (RVA) du champ static.</span><span class="sxs-lookup"><span data-stu-id="6a8fc-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a8fc-108">Notes</span><span class="sxs-lookup"><span data-stu-id="6a8fc-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6a8fc-109">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6a8fc-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a8fc-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6a8fc-110">Requirements</span></span>  
 <span data-ttu-id="6a8fc-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a8fc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a8fc-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6a8fc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a8fc-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a8fc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a8fc-114">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a8fc-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a8fc-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a8fc-115">See Also</span></span>  
 [<span data-ttu-id="6a8fc-116">ICorDebugStaticFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="6a8fc-116">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="6a8fc-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="6a8fc-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
