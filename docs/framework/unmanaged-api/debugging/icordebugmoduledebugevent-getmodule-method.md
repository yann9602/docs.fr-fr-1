---
title: "ICorDebugModuleDebugEvent::GetModule, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 64564b1af76ae3ce578155c7c40f0c4a4bd2c890
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="13506-102">ICorDebugModuleDebugEvent::GetModule, méthode</span><span class="sxs-lookup"><span data-stu-id="13506-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>
<span data-ttu-id="13506-103">Obtient le module fusionné qui vient d’être chargé ou déchargé.</span><span class="sxs-lookup"><span data-stu-id="13506-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13506-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13506-104">Syntax</span></span>  
  
```  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="13506-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="13506-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="13506-106">[out] Pointeur vers l’adresse d’un objet ICorDebugModule qui représente le module fusionné qui vient d’être chargé ou déchargé.</span><span class="sxs-lookup"><span data-stu-id="13506-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13506-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="13506-107">Remarks</span></span>  
 <span data-ttu-id="13506-108">Vous pouvez appeler la [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) méthode pour déterminer si le module a été chargé ou déchargé.</span><span class="sxs-lookup"><span data-stu-id="13506-108">You can call the [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="13506-109">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="13506-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13506-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="13506-110">Requirements</span></span>  
 <span data-ttu-id="13506-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13506-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13506-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="13506-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="13506-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13506-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13506-114">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13506-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13506-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13506-115">See Also</span></span>  
 [<span data-ttu-id="13506-116">Icordebugmoduledebugevent, Interface</span><span class="sxs-lookup"><span data-stu-id="13506-116">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
 [<span data-ttu-id="13506-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="13506-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
