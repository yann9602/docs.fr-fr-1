---
title: "INotifySink2::OnSyncCallOut, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: INotifySink2.OnSyncCallOut
api_location: diasymreader.dll
api_type: COM
f1_keywords: INotifySink2::OnSyncCallOut
helpviewer_keywords:
- INotifySink2::OnSyncCallOut method [.NET Framework debugging]
- OnSyncCallOut method [.NET Framework debugging]
ms.assetid: 97f15656-8677-4079-8553-a1d8603355d6
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 484027fe0ab8e5e416059678d2603080ed730be3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="inotifysink2onsynccallout-method"></a><span data-ttu-id="00b0a-102">INotifySink2::OnSyncCallOut, méthode</span><span class="sxs-lookup"><span data-stu-id="00b0a-102">INotifySink2::OnSyncCallOut Method</span></span>
<span data-ttu-id="00b0a-103">Appelée lorsqu’un appel est sortant.</span><span class="sxs-lookup"><span data-stu-id="00b0a-103">Gets invoked when a call is out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00b0a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00b0a-104">Syntax</span></span>  
  
```  
HRESULT OnSyncCallOut  
(  
    [in]  CALL_ID  in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*   out_pBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="00b0a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="00b0a-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="00b0a-106">[in] ID de l’appel sortant. Consultez [call_id, Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="00b0a-106">[in] ID of the call that is out. See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="00b0a-107">[out] Mémoire tampon des appels.</span><span class="sxs-lookup"><span data-stu-id="00b0a-107">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="00b0a-108">[out] Taille de la mémoire tampon de l’appel, en octets.</span><span class="sxs-lookup"><span data-stu-id="00b0a-108">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00b0a-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="00b0a-109">Return Value</span></span>  
 <span data-ttu-id="00b0a-110">S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="00b0a-110">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00b0a-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="00b0a-111">Requirements</span></span>  
 <span data-ttu-id="00b0a-112">**En-tête :** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="00b0a-112">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00b0a-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00b0a-113">See Also</span></span>  
 [<span data-ttu-id="00b0a-114">INotifySink2, interface</span><span class="sxs-lookup"><span data-stu-id="00b0a-114">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="00b0a-115">INotifySource2, interface</span><span class="sxs-lookup"><span data-stu-id="00b0a-115">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="00b0a-116">INotifyConnection2, interface</span><span class="sxs-lookup"><span data-stu-id="00b0a-116">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
