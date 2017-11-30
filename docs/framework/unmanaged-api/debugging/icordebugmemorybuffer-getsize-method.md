---
title: "ICorDebugMemoryBuffer::GetSize, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a21198c70512af703e106870d1bc3f7882d62fe9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="f66b7-102">ICorDebugMemoryBuffer::GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="f66b7-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="f66b7-103">Obtient la taille de la mémoire tampon en octets.</span><span class="sxs-lookup"><span data-stu-id="f66b7-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f66b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f66b7-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f66b7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f66b7-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="f66b7-106">[out] Pointeur vers la taille de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="f66b7-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f66b7-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="f66b7-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f66b7-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f66b7-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f66b7-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f66b7-109">Requirements</span></span>  
 <span data-ttu-id="f66b7-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f66b7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f66b7-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f66b7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f66b7-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f66b7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f66b7-113">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f66b7-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f66b7-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f66b7-114">See Also</span></span>  
 [<span data-ttu-id="f66b7-115">Icordebugmemorybuffer, Interface</span><span class="sxs-lookup"><span data-stu-id="f66b7-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="f66b7-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f66b7-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
