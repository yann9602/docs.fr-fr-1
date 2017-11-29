---
title: "ICorDebugDataTarget::ReadVirtual, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugDataTarget.ReadVirtual Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugDataTarget::ReadVirtual
helpviewer_keywords:
- ICorDebugDataTarget::ReadVirtual method [.NET Framework debugging]
- ReadVirtual method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: 55e57640-b3d2-413d-b4f4-fbc27fb8e37c
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b9b9f0399c05155a9925624e5c9d6bcb6a52f024
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatargetreadvirtual-method"></a><span data-ttu-id="3f3ba-102">ICorDebugDataTarget::ReadVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="3f3ba-102">ICorDebugDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="3f3ba-103">Obtient un bloc de mémoire contiguë, en commençant à l’adresse spécifiée et le retourne dans la mémoire tampon fournie.</span><span class="sxs-lookup"><span data-stu-id="3f3ba-103">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f3ba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f3ba-104">Syntax</span></span>  
  
```  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3f3ba-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3f3ba-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="3f3ba-106">[in] L’adresse de début de la mémoire demandée.</span><span class="sxs-lookup"><span data-stu-id="3f3ba-106">[in] The start address of requested memory.</span></span>  
  
 `pbuffer`  
 <span data-ttu-id="3f3ba-107">[out] La mémoire tampon où la mémoire sera stockée.</span><span class="sxs-lookup"><span data-stu-id="3f3ba-107">[out] The buffer where the memory will be stored.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="3f3ba-108">[in] Le nombre d’octets à obtenir à partir de l’adresse cible.</span><span class="sxs-lookup"><span data-stu-id="3f3ba-108">[in] The number of bytes to get from the target address.</span></span>  
  
 `pBytesRead`  
 <span data-ttu-id="3f3ba-109">[out] Le nombre d’octets lus réellement à partir de l’adresse cible.</span><span class="sxs-lookup"><span data-stu-id="3f3ba-109">[out] The number of bytes actually read from the target address.</span></span> <span data-ttu-id="3f3ba-110">Cela peut être inférieur à `bytesRequested`.</span><span class="sxs-lookup"><span data-stu-id="3f3ba-110">This can be fewer than `bytesRequested`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f3ba-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="3f3ba-111">Remarks</span></span>  
 <span data-ttu-id="3f3ba-112">Si le premier octet (à l’adresse de début spécifiée) peut être lu, l’appel doit retourner un succès (pour prendre en charge la lecture efficace des structures de données avec une longueur autodescriptive, comme les chaînes se terminant par null).</span><span class="sxs-lookup"><span data-stu-id="3f3ba-112">If the first byte (at the specified start address) can be read, the call should return success (to support efficient reading of data structures with self-describing length, like null-terminated strings).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f3ba-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3f3ba-113">Requirements</span></span>  
 <span data-ttu-id="3f3ba-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f3ba-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f3ba-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3f3ba-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3f3ba-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3f3ba-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f3ba-117">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f3ba-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f3ba-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f3ba-118">See Also</span></span>  
 [<span data-ttu-id="3f3ba-119">ICorDebugDataTarget (Interface)</span><span class="sxs-lookup"><span data-stu-id="3f3ba-119">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [<span data-ttu-id="3f3ba-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="3f3ba-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="3f3ba-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="3f3ba-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
