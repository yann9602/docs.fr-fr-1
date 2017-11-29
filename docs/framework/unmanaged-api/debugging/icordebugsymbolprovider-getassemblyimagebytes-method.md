---
title: "ICorDebugSymbolProvider::GetAssemblyImageBytes, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 127ebe82c32e9bf3d06c171d6cbf426d508eacaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="8d6d5-102">ICorDebugSymbolProvider::GetAssemblyImageBytes, méthode</span><span class="sxs-lookup"><span data-stu-id="8d6d5-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>
<span data-ttu-id="8d6d5-103">Lit les données d’un assembly fusionné pour une adresse virtuelle relative (RVA) donnée dans l’assembly fusionné.</span><span class="sxs-lookup"><span data-stu-id="8d6d5-103">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d6d5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d6d5-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,   
   [in] ULONG32 length,   
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8d6d5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8d6d5-105">Parameters</span></span>  
 `rva`  
 <span data-ttu-id="8d6d5-106">[in] Adresse virtuelle relative (RVA) dans un assembly fusionné.</span><span class="sxs-lookup"><span data-stu-id="8d6d5-106">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="8d6d5-107">Nombre d’octets à lire à partir de l’assembly fusionné.</span><span class="sxs-lookup"><span data-stu-id="8d6d5-107">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="8d6d5-108">Un pointeur vers l’adresse d’un [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) objet qui contient des informations sur la mémoire tampon avec des métadonnées de l’assembly fusionné.</span><span class="sxs-lookup"><span data-stu-id="8d6d5-108">A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d6d5-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="8d6d5-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d6d5-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8d6d5-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d6d5-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8d6d5-111">Requirements</span></span>  
 <span data-ttu-id="8d6d5-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d6d5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d6d5-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8d6d5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d6d5-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d6d5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d6d5-115">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d6d5-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d6d5-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d6d5-116">See Also</span></span>  
 [<span data-ttu-id="8d6d5-117">Icordebugsymbolprovider, Interface</span><span class="sxs-lookup"><span data-stu-id="8d6d5-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="8d6d5-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="8d6d5-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
