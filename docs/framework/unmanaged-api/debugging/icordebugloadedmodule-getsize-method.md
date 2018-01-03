---
title: "ICorDebugLoadedModule::GetSize (méthode)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1fb340845afac0f5a13f7c4646d11ac057ebd054
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="ae4c7-102">ICorDebugLoadedModule::GetSize (méthode)</span><span class="sxs-lookup"><span data-stu-id="ae4c7-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="ae4c7-103">Obtient la taille en octets du module chargé.</span><span class="sxs-lookup"><span data-stu-id="ae4c7-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae4c7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae4c7-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ae4c7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ae4c7-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="ae4c7-106">[out] Pointeur vers le nombre d'octets dans le module chargé.</span><span class="sxs-lookup"><span data-stu-id="ae4c7-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae4c7-107">Notes</span><span class="sxs-lookup"><span data-stu-id="ae4c7-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ae4c7-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ae4c7-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae4c7-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ae4c7-109">Requirements</span></span>  
 <span data-ttu-id="ae4c7-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae4c7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae4c7-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ae4c7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae4c7-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae4c7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae4c7-113">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae4c7-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae4c7-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae4c7-114">See Also</span></span>  
 [<span data-ttu-id="ae4c7-115">ICorDebugLoadedModule, interface</span><span class="sxs-lookup"><span data-stu-id="ae4c7-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="ae4c7-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="ae4c7-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
