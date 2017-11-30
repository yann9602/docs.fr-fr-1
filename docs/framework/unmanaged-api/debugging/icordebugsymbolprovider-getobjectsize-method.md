---
title: "ICorDebugSymbolProvider::GetObjectSize, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ea9e0fcae9f98869884ad887a6c24de342512b87
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="dc92b-102">ICorDebugSymbolProvider::GetObjectSize, méthode</span><span class="sxs-lookup"><span data-stu-id="dc92b-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>
<span data-ttu-id="dc92b-103">Retourne la taille d'un objet en fonction de sa signature typespec.</span><span class="sxs-lookup"><span data-stu-id="dc92b-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc92b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc92b-104">Syntax</span></span>  
  
```  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc92b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dc92b-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="dc92b-106">[in] Nombre d'octets dans la signature typespec.</span><span class="sxs-lookup"><span data-stu-id="dc92b-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="dc92b-107">typeSig</span><span class="sxs-lookup"><span data-stu-id="dc92b-107">typeSig</span></span>  
 <span data-ttu-id="dc92b-108">[in] Signature typespec.</span><span class="sxs-lookup"><span data-stu-id="dc92b-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="dc92b-109">[out] Pointeur vers la taille de l'objet.</span><span class="sxs-lookup"><span data-stu-id="dc92b-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc92b-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="dc92b-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc92b-111">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="dc92b-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc92b-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="dc92b-112">Requirements</span></span>  
 <span data-ttu-id="dc92b-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc92b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc92b-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dc92b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc92b-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc92b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc92b-116">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc92b-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc92b-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc92b-117">See Also</span></span>  
 [<span data-ttu-id="dc92b-118">Icordebugsymbolprovider, Interface</span><span class="sxs-lookup"><span data-stu-id="dc92b-118">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="dc92b-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="dc92b-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
