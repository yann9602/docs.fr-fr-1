---
title: "ICLRDataTarget3::GetExceptionThreadID, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICLRDataTarget3.GetExceptionThreadID
api_location: mscordbi.dll
api_type: COM
ms.assetid: 307d6ac7-4a86-45f3-999d-6b47004a68f2
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0f8b2e7c764eb5d7694633be7fb095b3d19be6e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget3getexceptionthreadid-method"></a><span data-ttu-id="63b8e-102">ICLRDataTarget3::GetExceptionThreadID, méthode</span><span class="sxs-lookup"><span data-stu-id="63b8e-102">ICLRDataTarget3::GetExceptionThreadID Method</span></span>
<span data-ttu-id="63b8e-103">Appelée par les services d'accès aux données de CLR (Common Language Runtime) pour obtenir l'ID du thread qui a levé l'exception.</span><span class="sxs-lookup"><span data-stu-id="63b8e-103">Called by the common language runtime (CLR) data access services to get the ID of the thread that threw the exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63b8e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63b8e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionThreadID(  
    [out] ULONG32* threadID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="63b8e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="63b8e-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="63b8e-106">[en sortie] L'ID du thread qui a levé l'exception.</span><span class="sxs-lookup"><span data-stu-id="63b8e-106">[out] The ID of the thread that threw the exception.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63b8e-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="63b8e-107">Return Value</span></span>  
 <span data-ttu-id="63b8e-108">La valeur de retour est `S_OK` en cas de réussite ou un code d'échec `HRESULT` en cas d'échec.</span><span class="sxs-lookup"><span data-stu-id="63b8e-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="63b8e-109">Les codes `HRESULT` peuvent comprendre, sans y être limités, ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="63b8e-109">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="63b8e-110">Code de retour</span><span class="sxs-lookup"><span data-stu-id="63b8e-110">Return code</span></span>|<span data-ttu-id="63b8e-111">Description</span><span class="sxs-lookup"><span data-stu-id="63b8e-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="63b8e-112">La méthode a réussi.</span><span class="sxs-lookup"><span data-stu-id="63b8e-112">Method succeeded.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="63b8e-113">Impossible de trouver un ID de thread valide pour l'exception.</span><span class="sxs-lookup"><span data-stu-id="63b8e-113">Could not find a valid thread ID for the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63b8e-114">Notes</span><span class="sxs-lookup"><span data-stu-id="63b8e-114">Remarks</span></span>  
 <span data-ttu-id="63b8e-115">Cette méthode est implémentée par le writer de l'application de débogage.</span><span class="sxs-lookup"><span data-stu-id="63b8e-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63b8e-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="63b8e-116">Requirements</span></span>  
 <span data-ttu-id="63b8e-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63b8e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63b8e-118">**En-tête :** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="63b8e-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="63b8e-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63b8e-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63b8e-120">**Versions du .NET framework :**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63b8e-120">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63b8e-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63b8e-121">See Also</span></span>  
 [<span data-ttu-id="63b8e-122">ICLRDataTarget3, interface</span><span class="sxs-lookup"><span data-stu-id="63b8e-122">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [<span data-ttu-id="63b8e-123">GetExceptionContextRecord, méthode</span><span class="sxs-lookup"><span data-stu-id="63b8e-123">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)  
 [<span data-ttu-id="63b8e-124">GetExceptionRecord, méthode</span><span class="sxs-lookup"><span data-stu-id="63b8e-124">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)
