---
title: "ICLRDataTarget::GetCurrentThreadID, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.GetCurrentThreadID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::GetCurrentThreadID method [.NET Framework debugging]
ms.assetid: dc9a0a6c-d592-4fb7-86ed-62684da3b0e1
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2fd2c39b20b823e18232081d1655a6770bafccc5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a><span data-ttu-id="448fc-102">ICLRDataTarget::GetCurrentThreadID, méthode</span><span class="sxs-lookup"><span data-stu-id="448fc-102">ICLRDataTarget::GetCurrentThreadID Method</span></span>
<span data-ttu-id="448fc-103">Obtient l’identificateur de système d’exploitation pour le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="448fc-103">Gets the operating system identifier for the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="448fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="448fc-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="448fc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="448fc-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="448fc-106">[out] Pointeur vers l’identificateur de système d’exploitation du thread actuel pour le processus cible.</span><span class="sxs-lookup"><span data-stu-id="448fc-106">[out] A pointer to the operating system identifier of the current thread for the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="448fc-107">Notes</span><span class="sxs-lookup"><span data-stu-id="448fc-107">Remarks</span></span>  
 <span data-ttu-id="448fc-108">S’il n’existe aucun thread actuel pour le processus cible, le `GetCurrentThreadID` méthode risque d’échouer.</span><span class="sxs-lookup"><span data-stu-id="448fc-108">If there is no current thread for the target process, the `GetCurrentThreadID` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="448fc-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="448fc-109">Requirements</span></span>  
 <span data-ttu-id="448fc-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="448fc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="448fc-111">**En-tête :** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="448fc-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="448fc-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="448fc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="448fc-113">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="448fc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="448fc-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="448fc-114">See Also</span></span>  
 [<span data-ttu-id="448fc-115">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="448fc-115">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
