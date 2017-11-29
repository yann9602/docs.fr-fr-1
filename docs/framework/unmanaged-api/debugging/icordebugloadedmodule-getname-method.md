---
title: "ICorDebugLoadedModule::GetName (méthode)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: aee475dfc425eea32ce4a1e5b4a081593574ba64
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="697b3-102">ICorDebugLoadedModule::GetName (méthode)</span><span class="sxs-lookup"><span data-stu-id="697b3-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="697b3-103">Obtient le nom du module chargé.</span><span class="sxs-lookup"><span data-stu-id="697b3-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="697b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="697b3-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="697b3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="697b3-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="697b3-106">[in] Nombre de caractères dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="697b3-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="697b3-107">[out] Pointeur vers le nombre de caractères réellement écrits dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="697b3-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="697b3-108">[out] Tableau de caractères contenant le nom du module chargé.</span><span class="sxs-lookup"><span data-stu-id="697b3-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="697b3-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="697b3-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="697b3-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="697b3-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="697b3-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="697b3-111">Requirements</span></span>  
 <span data-ttu-id="697b3-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="697b3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="697b3-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="697b3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="697b3-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="697b3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="697b3-115">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="697b3-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="697b3-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="697b3-116">See Also</span></span>  
 [<span data-ttu-id="697b3-117">Icordebugloadedmodule, Interface</span><span class="sxs-lookup"><span data-stu-id="697b3-117">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="697b3-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="697b3-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
