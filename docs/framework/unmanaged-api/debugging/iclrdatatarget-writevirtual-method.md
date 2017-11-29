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
ms.openlocfilehash: ffce593824599e9f8f41c38966b69a9076924608
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdatatargetwritevirtual-method"></a><span data-ttu-id="15b80-102">ICLRDataTarget::WriteVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="15b80-102">ICLRDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="15b80-103">Écrit des données à partir de la mémoire tampon spécifiée à l’adresse de mémoire virtuelle spécifiée.</span><span class="sxs-lookup"><span data-stu-id="15b80-103">Writes data from the specified buffer to the specified virtual memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15b80-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15b80-104">Syntax</span></span>  
  
```  
HRESULT WriteVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [in, size_is(bytesRequested)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesWritten  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="15b80-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="15b80-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="15b80-106">[in] CLRDATA_ADDRESS qui stocke l’adresse de la mémoire virtuelle.</span><span class="sxs-lookup"><span data-stu-id="15b80-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="15b80-107">[in] Pointeur vers une mémoire tampon qui stocke les données doivent être écrites.</span><span class="sxs-lookup"><span data-stu-id="15b80-107">[in] A pointer to a buffer that stores the data to be written.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="15b80-108">[in] Le nombre d’octets à écrire.</span><span class="sxs-lookup"><span data-stu-id="15b80-108">[in] The number of bytes to be written.</span></span>  
  
 `bytesWritten`  
 <span data-ttu-id="15b80-109">[out] Pointeur vers le nombre réel d’octets qui ont été écrits.</span><span class="sxs-lookup"><span data-stu-id="15b80-109">[out] A pointer to the actual number of bytes that were written.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15b80-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="15b80-110">Requirements</span></span>  
 <span data-ttu-id="15b80-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15b80-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15b80-112">**En-tête :** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="15b80-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="15b80-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15b80-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15b80-114">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15b80-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15b80-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15b80-115">See Also</span></span>  
 [<span data-ttu-id="15b80-116">ICLRDataTarget (Interface)</span><span class="sxs-lookup"><span data-stu-id="15b80-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
