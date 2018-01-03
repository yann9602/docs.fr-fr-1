---
title: "ICLRDataTarget::WriteVirtual, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.WriteVirtual
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::WriteVirtual
helpviewer_keywords:
- ICLRDataTarget::WriteVirtual method [.NET Framework debugging]
- WriteVirtual method [.NET Framework debugging]
ms.assetid: d627e8b7-a605-40ac-b9bb-da9a3f1b66d9
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 77c47ff90ff9d225eaa8e1f26a70463ea7d5dd5c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatargetwritevirtual-method"></a><span data-ttu-id="d9e0c-102">ICLRDataTarget::WriteVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="d9e0c-102">ICLRDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="d9e0c-103">Écrit des données à partir de la mémoire tampon spécifiée à l’adresse de mémoire virtuelle spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d9e0c-103">Writes data from the specified buffer to the specified virtual memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9e0c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9e0c-104">Syntax</span></span>  
  
```  
HRESULT WriteVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [in, size_is(bytesRequested)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesWritten  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d9e0c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d9e0c-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="d9e0c-106">[in] CLRDATA_ADDRESS qui stocke l’adresse de la mémoire virtuelle.</span><span class="sxs-lookup"><span data-stu-id="d9e0c-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="d9e0c-107">[in] Pointeur vers une mémoire tampon qui stocke les données doivent être écrites.</span><span class="sxs-lookup"><span data-stu-id="d9e0c-107">[in] A pointer to a buffer that stores the data to be written.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="d9e0c-108">[in] Le nombre d’octets à écrire.</span><span class="sxs-lookup"><span data-stu-id="d9e0c-108">[in] The number of bytes to be written.</span></span>  
  
 `bytesWritten`  
 <span data-ttu-id="d9e0c-109">[out] Pointeur vers le nombre réel d’octets qui ont été écrits.</span><span class="sxs-lookup"><span data-stu-id="d9e0c-109">[out] A pointer to the actual number of bytes that were written.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9e0c-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d9e0c-110">Requirements</span></span>  
 <span data-ttu-id="d9e0c-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9e0c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9e0c-112">**En-tête :** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="d9e0c-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="d9e0c-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9e0c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9e0c-114">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9e0c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9e0c-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d9e0c-115">See Also</span></span>  
 [<span data-ttu-id="d9e0c-116">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="d9e0c-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
