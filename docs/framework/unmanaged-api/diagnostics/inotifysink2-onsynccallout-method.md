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
ms.openlocfilehash: 427b54a66b92ef23572739d6c9e0dfd5731eb638
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="inotifysink2onsynccallout-method"></a><span data-ttu-id="1bacb-102">INotifySink2::OnSyncCallOut, méthode</span><span class="sxs-lookup"><span data-stu-id="1bacb-102">INotifySink2::OnSyncCallOut Method</span></span>
<span data-ttu-id="1bacb-103">Appelée lorsqu’un appel est sortant.</span><span class="sxs-lookup"><span data-stu-id="1bacb-103">Gets invoked when a call is out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bacb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1bacb-104">Syntax</span></span>  
  
```  
HRESULT OnSyncCallOut  
(  
    [in]  CALL_ID  in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*   out_pBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1bacb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1bacb-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="1bacb-106">[in] ID de l’appel sortant. Consultez [call_id, Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="1bacb-106">[in] ID of the call that is out. See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="1bacb-107">[out] Mémoire tampon des appels.</span><span class="sxs-lookup"><span data-stu-id="1bacb-107">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="1bacb-108">[out] Taille de la mémoire tampon de l’appel, en octets.</span><span class="sxs-lookup"><span data-stu-id="1bacb-108">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1bacb-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1bacb-109">Return Value</span></span>  
 <span data-ttu-id="1bacb-110">S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="1bacb-110">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bacb-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1bacb-111">Requirements</span></span>  
 <span data-ttu-id="1bacb-112">**En-tête :** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="1bacb-112">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bacb-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1bacb-113">See Also</span></span>  
 [<span data-ttu-id="1bacb-114">INotifySink2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="1bacb-114">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="1bacb-115">INotifySource2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="1bacb-115">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="1bacb-116">INotifyConnection2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="1bacb-116">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
