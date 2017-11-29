---
title: "ICorDebugSymbolProvider::GetAssemblyImageMetadata, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 48e5e9daf191cb2f4112dd2a957f29c0a7521398
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="a0a3c-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata, méthode</span><span class="sxs-lookup"><span data-stu-id="a0a3c-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>
<span data-ttu-id="a0a3c-103">Retourne les métadonnées d’un assembly fusionné.</span><span class="sxs-lookup"><span data-stu-id="a0a3c-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0a3c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0a3c-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0a3c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a0a3c-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="a0a3c-106">[out] Un pointeur vers l’adresse d’un [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) objet qui contient des informations sur la taille et l’adresse des métadonnées de l’assembly fusionné.</span><span class="sxs-lookup"><span data-stu-id="a0a3c-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0a3c-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="a0a3c-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0a3c-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a0a3c-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0a3c-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a0a3c-109">Requirements</span></span>  
 <span data-ttu-id="a0a3c-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0a3c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0a3c-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a0a3c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a0a3c-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0a3c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0a3c-113">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0a3c-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0a3c-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0a3c-114">See Also</span></span>  
 [<span data-ttu-id="a0a3c-115">Icordebugsymbolprovider, Interface</span><span class="sxs-lookup"><span data-stu-id="a0a3c-115">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="a0a3c-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="a0a3c-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
