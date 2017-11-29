---
title: ICorDebugModule3, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule3
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugModule3
helpviewer_keywords: ICorDebugModule3 interface [.NET Framework debugging]
ms.assetid: 0b69f945-263a-4e11-8512-89d27f6ea296
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f6ef8314329aba60d8c23c6f00725192d83961ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmodule3-interface"></a><span data-ttu-id="d2061-102">ICorDebugModule3, interface</span><span class="sxs-lookup"><span data-stu-id="d2061-102">ICorDebugModule3 Interface</span></span>
<span data-ttu-id="d2061-103">Crée un lecteur de symboles pour un module dynamique.</span><span class="sxs-lookup"><span data-stu-id="d2061-103">Creates a symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2061-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2061-104">Syntax</span></span>  
  
```  
interface ICorDebugModule3 : IUnknown  
{  
    HRESULT CreateReaderForInMemorySymbols  
      (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **  ppObj  
      );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d2061-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d2061-105">Methods</span></span>  
  
|<span data-ttu-id="d2061-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="d2061-106">Method</span></span>|<span data-ttu-id="d2061-107">Description</span><span class="sxs-lookup"><span data-stu-id="d2061-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d2061-108">ICorDebugModule3::CreateReaderForInMemorySymbols (méthode)</span><span class="sxs-lookup"><span data-stu-id="d2061-108">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-createreaderforinmemorysymbols-method.md)|<span data-ttu-id="d2061-109">Crée un lecteur de symboles (généralement [ISymUnmanagedReader (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) pour un module dynamique.</span><span class="sxs-lookup"><span data-stu-id="d2061-109">Creates a symbol reader (typically [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) for a dynamic module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2061-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="d2061-110">Remarks</span></span>  
 <span data-ttu-id="d2061-111">Cette interface étend logiquement les interfaces « ICorDebugModule » et « ICorDebugModule2 ».</span><span class="sxs-lookup"><span data-stu-id="d2061-111">This interface logically extends the "ICorDebugModule" and "ICorDebugModule2" interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2061-112">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="d2061-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2061-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d2061-113">Requirements</span></span>  
 <span data-ttu-id="d2061-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2061-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2061-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d2061-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d2061-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2061-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2061-117">**Versions du .NET framework :**4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="d2061-117">**.NET Framework Versions:**4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2061-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2061-118">See Also</span></span>  
 [<span data-ttu-id="d2061-119">ICorDebugRemoteTarget (Interface)</span><span class="sxs-lookup"><span data-stu-id="d2061-119">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [<span data-ttu-id="d2061-120">ICorDebug (Interface)</span><span class="sxs-lookup"><span data-stu-id="d2061-120">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="d2061-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="d2061-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
