---
title: "ICorDebugMemoryBuffer::GetStartAddress, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5519b9dd0d85114e08311e1263c2f2e4ab095ae6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="ce1d6-102">ICorDebugMemoryBuffer::GetStartAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="ce1d6-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="ce1d6-103">Obtient l'adresse de départ de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="ce1d6-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce1d6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce1d6-104">Syntax</span></span>  
  
```  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ce1d6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ce1d6-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="ce1d6-106">[out] Pointeur vers l'adresse de départ de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="ce1d6-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce1d6-107">Notes</span><span class="sxs-lookup"><span data-stu-id="ce1d6-107">Remarks</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="ce1d6-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ce1d6-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce1d6-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ce1d6-109">Requirements</span></span>  
 <span data-ttu-id="ce1d6-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce1d6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce1d6-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ce1d6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce1d6-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce1d6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce1d6-113">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce1d6-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce1d6-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce1d6-114">See Also</span></span>  
 [<span data-ttu-id="ce1d6-115">ICorDebugMemoryBuffer, interface</span><span class="sxs-lookup"><span data-stu-id="ce1d6-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="ce1d6-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="ce1d6-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
