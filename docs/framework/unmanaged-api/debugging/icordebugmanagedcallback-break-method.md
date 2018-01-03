---
title: "ICorDebugManagedCallback::Break, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.Break
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::Break
helpviewer_keywords:
- Break method [.NET Framework debugging]
- ICorDebugManagedCallback::Break method [.NET Framework debugging]
ms.assetid: 7d78a301-82b3-43b2-9d65-3cda3285ae97
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f9d3a39859d4e44bef2622d456ae0fbac233e7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackbreak-method"></a><span data-ttu-id="fa010-102">ICorDebugManagedCallback::Break, méthode</span><span class="sxs-lookup"><span data-stu-id="fa010-102">ICorDebugManagedCallback::Break Method</span></span>
<span data-ttu-id="fa010-103">Notifie le débogueur lorsqu’une <xref:System.Reflection.Emit.OpCodes.Break> instruction dans le flux du code est exécutée.</span><span class="sxs-lookup"><span data-stu-id="fa010-103">Notifies the debugger when a <xref:System.Reflection.Emit.OpCodes.Break> instruction in the code stream is executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa010-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fa010-104">Syntax</span></span>  
  
```  
HRESULT Break (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fa010-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fa010-105">Parameters</span></span>  
 `pAppDOmain`  
 <span data-ttu-id="fa010-106">[in] Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application qui contient l’instruction d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="fa010-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the break instruction.</span></span>  
  
 `thread`  
 <span data-ttu-id="fa010-107">[in] Pointeur vers un objet ICorDebugThread qui représente le thread qui contient l’instruction d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="fa010-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the break instruction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa010-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fa010-108">Requirements</span></span>  
 <span data-ttu-id="fa010-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa010-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa010-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa010-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa010-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa010-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa010-112">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa010-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa010-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa010-113">See Also</span></span>  
 [<span data-ttu-id="fa010-114">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="fa010-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
