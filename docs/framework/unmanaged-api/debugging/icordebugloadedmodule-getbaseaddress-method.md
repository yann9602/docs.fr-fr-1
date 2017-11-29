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
ms.openlocfilehash: b192c606697896371202e98945f83623bbb99bb9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="2fa44-102">ICorDebugLoadedModule::GetBaseAddress (méthode)</span><span class="sxs-lookup"><span data-stu-id="2fa44-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="2fa44-103">Obtient l'adresse de base du module chargé.</span><span class="sxs-lookup"><span data-stu-id="2fa44-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fa44-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fa44-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2fa44-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2fa44-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="2fa44-106">[out] Pointeur vers l'adresse de base du module chargé.</span><span class="sxs-lookup"><span data-stu-id="2fa44-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2fa44-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="2fa44-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2fa44-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2fa44-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fa44-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2fa44-109">Requirements</span></span>  
 <span data-ttu-id="2fa44-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fa44-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fa44-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2fa44-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2fa44-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2fa44-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2fa44-113">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fa44-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fa44-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2fa44-114">See Also</span></span>  
 [<span data-ttu-id="2fa44-115">Icordebugloadedmodule, Interface</span><span class="sxs-lookup"><span data-stu-id="2fa44-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="2fa44-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="2fa44-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
