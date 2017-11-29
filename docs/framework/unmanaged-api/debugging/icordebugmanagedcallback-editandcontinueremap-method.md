---
title: "ICorDebugManagedCallback::EditAndContinueRemap, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.EditAndContinueRemap
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::EditAndContinueRemap
helpviewer_keywords:
- EditAndContinueRemap method [.NET Framework debugging]
- ICorDebugManagedCallback::EditAndContinueRemap method [.NET Framework debugging]
ms.assetid: 24a8fcce-317e-48ff-aefc-d86123ada935
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e45cf5376f0c8b4fbe76f56e3adcce22b1ef5c88
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a><span data-ttu-id="c81cc-102">ICorDebugManagedCallback::EditAndContinueRemap, méthode</span><span class="sxs-lookup"><span data-stu-id="c81cc-102">ICorDebugManagedCallback::EditAndContinueRemap Method</span></span>
<span data-ttu-id="c81cc-103">Cette méthode est dépréciée.</span><span class="sxs-lookup"><span data-stu-id="c81cc-103">This method has been deprecated.</span></span> <span data-ttu-id="c81cc-104">Informe le débogueur qu’un événement de remappage a été envoyé à l’environnement de développement intégré (IDE).</span><span class="sxs-lookup"><span data-stu-id="c81cc-104">It notifies the debugger that a remap event has been sent to the integrated development environment (IDE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c81cc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c81cc-105">Syntax</span></span>  
  
```  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="c81cc-106">Remarques</span><span class="sxs-lookup"><span data-stu-id="c81cc-106">Remarks</span></span>  
 <span data-ttu-id="c81cc-107">Le `EditAndContinueRemap` méthode est appelée lorsque l’exécution du code dans une ancienne version d’une fonction de mise à jour a été tentée.</span><span class="sxs-lookup"><span data-stu-id="c81cc-107">The `EditAndContinueRemap` method is called when the execution of the code in an old version of an updated function has been attempted.</span></span> <span data-ttu-id="c81cc-108">Le common language runtime appelle la `EditAndContinueRemap` méthode pour envoyer un événement de remappage à l’IDE.</span><span class="sxs-lookup"><span data-stu-id="c81cc-108">The common language runtime calls the `EditAndContinueRemap` method to send a remap event to the IDE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c81cc-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c81cc-109">Requirements</span></span>  
 <span data-ttu-id="c81cc-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c81cc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c81cc-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c81cc-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c81cc-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c81cc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c81cc-113">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c81cc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c81cc-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c81cc-114">See Also</span></span>  
 [<span data-ttu-id="c81cc-115">ICorDebugManagedCallback (Interface)</span><span class="sxs-lookup"><span data-stu-id="c81cc-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
