---
title: "ICLRDataTarget::ReadVirtual, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.ReadVirtual
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::ReadVirtual
helpviewer_keywords:
- ReadVirtual method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::ReadVirtual method [.NET Framework debugging]
ms.assetid: da3769eb-1828-4aa1-b9ed-db4842136a43
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 84d1a8c37bf9d065317688f42bd554108fd92974
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatargetreadvirtual-method"></a><span data-ttu-id="68134-102">ICLRDataTarget::ReadVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="68134-102">ICLRDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="68134-103">Lit les données à partir de l’adresse de mémoire virtuelle spécifiée dans la mémoire tampon spécifiée.</span><span class="sxs-lookup"><span data-stu-id="68134-103">Reads data from the specified virtual memory address into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68134-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68134-104">Syntax</span></span>  
  
```  
HRESULT ReadVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [out, size_is(bytesRequested), length_is(*bytesRead)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesRead  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="68134-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="68134-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="68134-106">[in] CLRDATA_ADDRESS qui stocke l’adresse de la mémoire virtuelle.</span><span class="sxs-lookup"><span data-stu-id="68134-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="68134-107">[out] Pointeur vers une mémoire tampon qui reçoit les données.</span><span class="sxs-lookup"><span data-stu-id="68134-107">[out] A pointer to a buffer that receives the data.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="68134-108">[in] La longueur de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="68134-108">[in] The length of the buffer.</span></span>  
  
 `bytesRead`  
 <span data-ttu-id="68134-109">[out] Pointeur vers le nombre d’octets retourné.</span><span class="sxs-lookup"><span data-stu-id="68134-109">[out] A pointer to the number of bytes returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68134-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="68134-110">Requirements</span></span>  
 <span data-ttu-id="68134-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68134-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68134-112">**En-tête :** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="68134-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="68134-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68134-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68134-114">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68134-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68134-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68134-115">See Also</span></span>  
 [<span data-ttu-id="68134-116">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="68134-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
