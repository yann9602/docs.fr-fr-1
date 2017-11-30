---
title: "ICorDebugDataTarget3::GetLoadedModules (méthode)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bc4820d2c71830b297ed690c440c90cfff1f9601
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a><span data-ttu-id="46b8e-102">ICorDebugDataTarget3::GetLoadedModules (méthode)</span><span class="sxs-lookup"><span data-stu-id="46b8e-102">ICorDebugDataTarget3::GetLoadedModules Method</span></span>
<span data-ttu-id="46b8e-103">Obtient la liste des modules qui ont été chargés jusqu'à présent.</span><span class="sxs-lookup"><span data-stu-id="46b8e-103">Gets a list of the modules that have been loaded so far.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46b8e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46b8e-104">Syntax</span></span>  
  
```  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="46b8e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="46b8e-105">Parameters</span></span>  
 `cRequestedModules`  
 <span data-ttu-id="46b8e-106">[in] Nombre de modules pour lesquels des informations sont demandées.</span><span class="sxs-lookup"><span data-stu-id="46b8e-106">[in] The number of modules for which information is requested.</span></span>  
  
 `pcFetchedModules`  
 <span data-ttu-id="46b8e-107">[out] Pointeur vers le nombre de modules à propos desquels des informations ont été retournées.</span><span class="sxs-lookup"><span data-stu-id="46b8e-107">[out] A pointer to the number of modules about which information was returned.</span></span>  
  
 `pLoadedModules`  
 <span data-ttu-id="46b8e-108">[out] Un pointeur vers un tableau de [ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) objets qui fournissent des informations sur les modules chargement.</span><span class="sxs-lookup"><span data-stu-id="46b8e-108">[out] A pointer to an array of [ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) objects that provide information about loaded modules.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46b8e-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="46b8e-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46b8e-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="46b8e-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46b8e-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="46b8e-111">Requirements</span></span>  
 <span data-ttu-id="46b8e-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46b8e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46b8e-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="46b8e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46b8e-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46b8e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46b8e-115">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46b8e-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46b8e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46b8e-116">See Also</span></span>  
 [<span data-ttu-id="46b8e-117">Icordebugdatatarget3, Interface</span><span class="sxs-lookup"><span data-stu-id="46b8e-117">ICorDebugDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)  
 [<span data-ttu-id="46b8e-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="46b8e-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
