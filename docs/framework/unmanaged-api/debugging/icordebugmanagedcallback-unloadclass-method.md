---
title: "ICorDebugManagedCallback::UnloadClass, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.UnloadClass
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::UnloadClass
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadClass method [.NET Framework debugging]
- UnloadClass method [.NET Framework debugging]
ms.assetid: 66a59b18-ce9a-41f4-b23b-4dd6753d6d36
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e034f6950cc9d77ef4db350475379aa5c497f7f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a><span data-ttu-id="ed16f-102">ICorDebugManagedCallback::UnloadClass, méthode</span><span class="sxs-lookup"><span data-stu-id="ed16f-102">ICorDebugManagedCallback::UnloadClass Method</span></span>
<span data-ttu-id="ed16f-103">Notifie le débogueur qu’une classe est en cours de déchargement.</span><span class="sxs-lookup"><span data-stu-id="ed16f-103">Notifies the debugger that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed16f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed16f-104">Syntax</span></span>  
  
```  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ed16f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ed16f-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="ed16f-106">[in] Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant la classe.</span><span class="sxs-lookup"><span data-stu-id="ed16f-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the class.</span></span>  
  
 `c`  
 <span data-ttu-id="ed16f-107">[in] Pointeur vers un objet ICorDebugClass qui représente la classe.</span><span class="sxs-lookup"><span data-stu-id="ed16f-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed16f-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="ed16f-108">Remarks</span></span>  
 <span data-ttu-id="ed16f-109">La classe ne doit pas être référencée après cet appel.</span><span class="sxs-lookup"><span data-stu-id="ed16f-109">The class should not be referenced after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed16f-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ed16f-110">Requirements</span></span>  
 <span data-ttu-id="ed16f-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed16f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed16f-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ed16f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ed16f-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ed16f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed16f-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed16f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed16f-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed16f-115">See Also</span></span>  
 [<span data-ttu-id="ed16f-116">LoadClass (méthode)</span><span class="sxs-lookup"><span data-stu-id="ed16f-116">LoadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)  
 [<span data-ttu-id="ed16f-117">ICorDebugManagedCallback (Interface)</span><span class="sxs-lookup"><span data-stu-id="ed16f-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
