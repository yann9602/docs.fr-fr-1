---
title: "ICorDebugModule::EnableClassLoadCallbacks, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.EnableClassLoadCallbacks
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::EnableClassLoadCallbacks
helpviewer_keywords:
- ICorDebugModule::EnableClassLoadCallbacks method [.NET Framework debugging]
- EnableClassLoadCallbacks method [.NET Framework debugging]
ms.assetid: 78dad5e4-8e2e-400f-bec3-92ff0205cd82
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d9045cceda54e6fe89c8c1baa8d4b9fa63105607
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="19faa-102">ICorDebugModule::EnableClassLoadCallbacks, méthode</span><span class="sxs-lookup"><span data-stu-id="19faa-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>
<span data-ttu-id="19faa-103">Contrôle si le [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) et [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) sont appelés pour ce module.</span><span class="sxs-lookup"><span data-stu-id="19faa-103">Controls whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19faa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19faa-104">Syntax</span></span>  
  
```  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="19faa-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="19faa-105">Parameters</span></span>  
 `bClassLoadCallbacks`  
 <span data-ttu-id="19faa-106">[in] Définissez cette valeur sur `true` pour activer le common language runtime (CLR) pour appeler le `ICorDebugManagedCallback::LoadClass` et `ICorDebugManagedCallback::UnloadClass` méthodes lorsque leurs événements associés se produisent.</span><span class="sxs-lookup"><span data-stu-id="19faa-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="19faa-107">La valeur par défaut est `false` pour les modules non dynamiques.</span><span class="sxs-lookup"><span data-stu-id="19faa-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="19faa-108">La valeur est toujours `true` pour les modules dynamiques et ne peut pas être modifié.</span><span class="sxs-lookup"><span data-stu-id="19faa-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19faa-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="19faa-109">Remarks</span></span>  
 <span data-ttu-id="19faa-110">Le `ICorDebugManagedCallback::LoadClass` et `ICorDebugManagedCallback::UnloadClass` rappels sont toujours activées pour les modules dynamiques et ne peut pas être désactivées.</span><span class="sxs-lookup"><span data-stu-id="19faa-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19faa-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="19faa-111">Requirements</span></span>  
 <span data-ttu-id="19faa-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19faa-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19faa-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="19faa-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="19faa-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19faa-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19faa-115">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19faa-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19faa-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19faa-116">See Also</span></span>  
    
 
