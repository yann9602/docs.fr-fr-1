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
ms.openlocfilehash: 29adc45df57c5f31c299dc28b611bcf0599d4aac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="3602f-102">ICorDebugLoadedModule::GetSize (méthode)</span><span class="sxs-lookup"><span data-stu-id="3602f-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="3602f-103">Obtient la taille en octets du module chargé.</span><span class="sxs-lookup"><span data-stu-id="3602f-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3602f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3602f-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3602f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3602f-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="3602f-106">[out] Pointeur vers le nombre d'octets dans le module chargé.</span><span class="sxs-lookup"><span data-stu-id="3602f-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3602f-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="3602f-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3602f-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3602f-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3602f-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3602f-109">Requirements</span></span>  
 <span data-ttu-id="3602f-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3602f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3602f-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3602f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3602f-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3602f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3602f-113">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3602f-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3602f-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3602f-114">See Also</span></span>  
 [<span data-ttu-id="3602f-115">Icordebugloadedmodule, Interface</span><span class="sxs-lookup"><span data-stu-id="3602f-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="3602f-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="3602f-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
