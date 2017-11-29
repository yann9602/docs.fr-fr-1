---
title: "ICorDebugManagedCallback::UnloadAssembly, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.UnloadAssembly
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::UnloadAssembly
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadAssembly method [.NET Framework debugging]
- UnloadAssembly method [.NET Framework debugging]
ms.assetid: 6734321c-c8a9-401f-a558-cad715ec4a77
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 29400e5bda2a17c731cb33e67c0123cffc89c48b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="18396-102">ICorDebugManagedCallback::UnloadAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="18396-102">ICorDebugManagedCallback::UnloadAssembly Method</span></span>
<span data-ttu-id="18396-103">Notifie le débogueur qu’un assembly du common language runtime a été déchargé.</span><span class="sxs-lookup"><span data-stu-id="18396-103">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18396-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18396-104">Syntax</span></span>  
  
```  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="18396-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="18396-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="18396-106">[in] Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application qui contenait l’assembly.</span><span class="sxs-lookup"><span data-stu-id="18396-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="18396-107">[in] Pointeur vers un objet ICorDebugAssembly qui représente l’assembly.</span><span class="sxs-lookup"><span data-stu-id="18396-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18396-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="18396-108">Remarks</span></span>  
 <span data-ttu-id="18396-109">L’assembly ne doit pas être utilisé après ce rappel.</span><span class="sxs-lookup"><span data-stu-id="18396-109">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18396-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="18396-110">Requirements</span></span>  
 <span data-ttu-id="18396-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18396-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18396-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="18396-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="18396-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="18396-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18396-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18396-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18396-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18396-115">See Also</span></span>  
 [<span data-ttu-id="18396-116">LoadAssembly (méthode)</span><span class="sxs-lookup"><span data-stu-id="18396-116">LoadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)  
 [<span data-ttu-id="18396-117">ICorDebugManagedCallback (Interface)</span><span class="sxs-lookup"><span data-stu-id="18396-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
