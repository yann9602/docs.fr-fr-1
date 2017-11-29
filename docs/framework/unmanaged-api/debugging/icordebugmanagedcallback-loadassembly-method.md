---
title: "ICorDebugManagedCallback::LoadAssembly, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.LoadAssembly
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::LoadAssembly
helpviewer_keywords:
- LoadAssembly method [.NET Framework debugging]
- ICorDebugManagedCallback::LoadAssembly method [.NET Framework debugging]
ms.assetid: 55cb673a-e240-43a6-a406-6912e7c0fe66
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1e59853f8f0ac61f89fc0efe0fb63f4ad7e6e0e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallbackloadassembly-method"></a><span data-ttu-id="7ef07-102">ICorDebugManagedCallback::LoadAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="7ef07-102">ICorDebugManagedCallback::LoadAssembly Method</span></span>
<span data-ttu-id="7ef07-103">Notifie le débogueur qu’un assembly du common language runtime (CLR) a été chargé avec succès.</span><span class="sxs-lookup"><span data-stu-id="7ef07-103">Notifies the debugger that a common language runtime (CLR) assembly has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ef07-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ef07-104">Syntax</span></span>  
  
```  
HRESULT LoadAssembly (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugAssembly  *pAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7ef07-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7ef07-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="7ef07-106">[in] Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application dans lequel l’assembly a été chargé.</span><span class="sxs-lookup"><span data-stu-id="7ef07-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the assembly has been loaded.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="7ef07-107">[in] Pointeur vers un objet ICorDebugAssembly qui représente l’assembly.</span><span class="sxs-lookup"><span data-stu-id="7ef07-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ef07-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7ef07-108">Requirements</span></span>  
 <span data-ttu-id="7ef07-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ef07-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ef07-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7ef07-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7ef07-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ef07-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ef07-112">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ef07-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ef07-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ef07-113">See Also</span></span>  
 [<span data-ttu-id="7ef07-114">UnloadAssembly (méthode)</span><span class="sxs-lookup"><span data-stu-id="7ef07-114">UnloadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadassembly-method.md)  
 [<span data-ttu-id="7ef07-115">ICorDebugManagedCallback (Interface)</span><span class="sxs-lookup"><span data-stu-id="7ef07-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
