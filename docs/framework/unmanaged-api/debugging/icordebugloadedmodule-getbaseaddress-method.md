---
title: "ICorDebugLoadedModule::GetBaseAddress (méthode)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d71b1db35a9e2747e7e14787f385f42f98305c61
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="52dd9-102">ICorDebugLoadedModule::GetBaseAddress (méthode)</span><span class="sxs-lookup"><span data-stu-id="52dd9-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="52dd9-103">Obtient l'adresse de base du module chargé.</span><span class="sxs-lookup"><span data-stu-id="52dd9-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52dd9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52dd9-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="52dd9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="52dd9-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="52dd9-106">[out] Pointeur vers l'adresse de base du module chargé.</span><span class="sxs-lookup"><span data-stu-id="52dd9-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52dd9-107">Notes</span><span class="sxs-lookup"><span data-stu-id="52dd9-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52dd9-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="52dd9-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52dd9-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="52dd9-109">Requirements</span></span>  
 <span data-ttu-id="52dd9-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52dd9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52dd9-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="52dd9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52dd9-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52dd9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52dd9-113">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52dd9-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52dd9-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52dd9-114">See Also</span></span>  
 [<span data-ttu-id="52dd9-115">ICorDebugLoadedModule, interface</span><span class="sxs-lookup"><span data-stu-id="52dd9-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="52dd9-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="52dd9-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
