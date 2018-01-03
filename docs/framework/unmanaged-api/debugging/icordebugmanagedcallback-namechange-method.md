---
title: "ICorDebugManagedCallback::NameChange, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.NameChange
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::NameChange
helpviewer_keywords:
- ICorDebugManagedCallback::NameChange method [.NET Framework debugging]
- NameChange method [.NET Framework debugging]
ms.assetid: a7018a0e-880e-4b68-b52a-1cd22c7aad62
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 31539413597c65b553794f07b1eeecdf3943f908
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbacknamechange-method"></a><span data-ttu-id="fe5eb-102">ICorDebugManagedCallback::NameChange, méthode</span><span class="sxs-lookup"><span data-stu-id="fe5eb-102">ICorDebugManagedCallback::NameChange Method</span></span>
<span data-ttu-id="fe5eb-103">Notifie le débogueur que le nom d’un domaine d’application ou d’un thread a changé.</span><span class="sxs-lookup"><span data-stu-id="fe5eb-103">Notifies the debugger that the name of either an application domain or a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe5eb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe5eb-104">Syntax</span></span>  
  
```  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fe5eb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fe5eb-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="fe5eb-106">[in] Un pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application qui avait un changement de nom ou qui contient le thread qui a un changement de nom.</span><span class="sxs-lookup"><span data-stu-id="fe5eb-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that either had a name change or that contains the thread that had a name change.</span></span>  
  
 `pThread`  
 <span data-ttu-id="fe5eb-107">[in] Pointeur vers un objet ICorDebugThread qui représente le thread qui a un changement de nom.</span><span class="sxs-lookup"><span data-stu-id="fe5eb-107">[in] A pointer to an ICorDebugThread object that represents the thread that had a name change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe5eb-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fe5eb-108">Requirements</span></span>  
 <span data-ttu-id="fe5eb-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe5eb-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe5eb-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fe5eb-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe5eb-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe5eb-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe5eb-112">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe5eb-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe5eb-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe5eb-113">See Also</span></span>  
 [<span data-ttu-id="fe5eb-114">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="fe5eb-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
