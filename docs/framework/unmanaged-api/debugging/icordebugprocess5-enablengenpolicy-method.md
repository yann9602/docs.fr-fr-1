---
title: "ICorDebugProcess5::EnableNGENPolicy, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5::EnableNGenPolicy
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::EnableNGENPolicy
helpviewer_keywords:
- ICorDebugProcess5::EnableNGENPolicy method [.NET Framework debugging]
- EnableNGENPolicy method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 3b8e15ca-3c72-4685-a937-da4c739cb9e9
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dca0df7b0be643d53bb5b9a03bd3abbb186d69dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5enablengenpolicy-method"></a><span data-ttu-id="1ed06-102">ICorDebugProcess5::EnableNGENPolicy, méthode</span><span class="sxs-lookup"><span data-stu-id="1ed06-102">ICorDebugProcess5::EnableNGENPolicy Method</span></span>
<span data-ttu-id="1ed06-103">Définit une valeur qui détermine comment une application charge les images natives lors de son exécution sous un débogueur managé.</span><span class="sxs-lookup"><span data-stu-id="1ed06-103">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ed06-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ed06-104">Syntax</span></span>  
  
```  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ed06-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1ed06-105">Parameters</span></span>  
 `ePolicy`  
 <span data-ttu-id="1ed06-106">[in] A [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md) constante qui détermine la façon dont une application charge les images natives lors de son exécution sous un débogueur managé.</span><span class="sxs-lookup"><span data-stu-id="1ed06-106">[in] A [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md) constant that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ed06-107">Notes</span><span class="sxs-lookup"><span data-stu-id="1ed06-107">Remarks</span></span>  
 <span data-ttu-id="1ed06-108">Si la stratégie est définie avec succès, la méthode retourne `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="1ed06-108">If the policy is set successfully, the method returns `S_OK`.</span></span> <span data-ttu-id="1ed06-109">Si `ePolicy` est en dehors de la plage des valeurs énumérées définies par [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md), la méthode retourne `E_INVALIDARG` et l’appel de méthode n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="1ed06-109">If `ePolicy` is outside the range of the enumerated values defined by [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md), the method returns `E_INVALIDARG` and the method call has no effect.</span></span> <span data-ttu-id="1ed06-110">Si la stratégie du Générateur d’images natives (Ngen.exe) ne peut pas être mis à jour, la méthode retourne `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="1ed06-110">If the policy of the Native Image Generator (Ngen.exe) cannot be updated, the method returns `E_FAIL`.</span></span>  
  
 <span data-ttu-id="1ed06-111">Le `ICorDebugProcess5::EnableNGenPolicy` méthode peut être appelée à tout moment pendant la durée de vie du processus.</span><span class="sxs-lookup"><span data-stu-id="1ed06-111">The `ICorDebugProcess5::EnableNGenPolicy` method can be called at any time during the lifetime of the process.</span></span> <span data-ttu-id="1ed06-112">La stratégie est appliquée pour tous les modules qui sont chargés après que la stratégie est définie.</span><span class="sxs-lookup"><span data-stu-id="1ed06-112">The policy is in effect for any modules that are loaded after the policy is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ed06-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1ed06-113">Requirements</span></span>  
 <span data-ttu-id="1ed06-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ed06-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ed06-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ed06-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ed06-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ed06-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ed06-117">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ed06-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ed06-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ed06-118">See Also</span></span>  
 [<span data-ttu-id="1ed06-119">ICorDebugProcess5, interface</span><span class="sxs-lookup"><span data-stu-id="1ed06-119">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="1ed06-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="1ed06-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="1ed06-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="1ed06-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
