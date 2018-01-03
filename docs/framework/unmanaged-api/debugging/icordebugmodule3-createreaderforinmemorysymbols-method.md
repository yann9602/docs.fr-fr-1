---
title: "ICorDebugModule3::CreateReaderForInMemorySymbols, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule3.CreateReaderForInMemorySymbols
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugModule3::CreateReaderForInMemorySymbols
helpviewer_keywords:
- CreateReaderForInMemorySymbols method, ICorDebugModule3 interface [.NET Framework debugging]
- ICorDebugModule3::CreateReaderForInMemorySymbols method [.NET Framework debugging]
ms.assetid: af317171-d66d-4114-89eb-063554c74940
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2838c6c1fe8641e343fac1a3efa82a39ee177abc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a><span data-ttu-id="091a8-102">ICorDebugModule3::CreateReaderForInMemorySymbols, méthode</span><span class="sxs-lookup"><span data-stu-id="091a8-102">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>
<span data-ttu-id="091a8-103">Crée un lecteur de symboles de débogage pour un module dynamique.</span><span class="sxs-lookup"><span data-stu-id="091a8-103">Creates a debug symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="091a8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="091a8-104">Syntax</span></span>  
  
```  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
#### <a name="parameters"></a><span data-ttu-id="091a8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="091a8-105">Parameters</span></span>  
 <span data-ttu-id="091a8-106">riid</span><span class="sxs-lookup"><span data-stu-id="091a8-106">riid</span></span>  
 <span data-ttu-id="091a8-107">[in] IID de l’interface COM à retourner.</span><span class="sxs-lookup"><span data-stu-id="091a8-107">[in] The IID of the COM interface to return.</span></span> <span data-ttu-id="091a8-108">En règle générale, il s’agit d’un [ISymUnmanagedReader (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).</span><span class="sxs-lookup"><span data-stu-id="091a8-108">Typically, this is an [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).</span></span>  
  
 <span data-ttu-id="091a8-109">ppObj</span><span class="sxs-lookup"><span data-stu-id="091a8-109">ppObj</span></span>  
 <span data-ttu-id="091a8-110">[out] Pointeur vers un pointeur vers l’interface retournée.</span><span class="sxs-lookup"><span data-stu-id="091a8-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="091a8-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="091a8-111">Return Value</span></span>  
 <span data-ttu-id="091a8-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="091a8-112">S_OK</span></span>  
 <span data-ttu-id="091a8-113">Le lecteur a été créé avec succès.</span><span class="sxs-lookup"><span data-stu-id="091a8-113">Successfully created the reader.</span></span>  
  
 <span data-ttu-id="091a8-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span><span class="sxs-lookup"><span data-stu-id="091a8-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span></span>  
 <span data-ttu-id="091a8-115">Le module n’est pas un module en mémoire ou dynamique.</span><span class="sxs-lookup"><span data-stu-id="091a8-115">The module is not an in-memory or dynamic module.</span></span>  
  
 <span data-ttu-id="091a8-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span><span class="sxs-lookup"><span data-stu-id="091a8-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span></span>  
 <span data-ttu-id="091a8-117">Symboles n’ont pas été fournis par l’application ou ne sont pas encore disponibles.</span><span class="sxs-lookup"><span data-stu-id="091a8-117">Symbols have not been supplied by the application or are not yet available.</span></span>  
  
 <span data-ttu-id="091a8-118">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="091a8-118">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="091a8-119">Impossible de créer le lecteur.</span><span class="sxs-lookup"><span data-stu-id="091a8-119">Unable to create the reader.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="091a8-120">Notes</span><span class="sxs-lookup"><span data-stu-id="091a8-120">Remarks</span></span>  
 <span data-ttu-id="091a8-121">Cette méthode peut également être utilisée pour créer un objet lecteur de symboles pour les modules de mémoire (non dynamique), mais uniquement une fois que les symboles sont tout d’abord disponibles (indiqué par le [UpdateModuleSymbols, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) rappel).</span><span class="sxs-lookup"><span data-stu-id="091a8-121">This method can also be used to create a symbol reader object for in-memory (non-dynamic) modules, but only after the symbols are first available (indicated by the [UpdateModuleSymbols Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) callback).</span></span>  
  
 <span data-ttu-id="091a8-122">Cette méthode retourne une nouvelle instance de lecteur chaque fois qu’il est appelé (comme [CComPtrBase::CoCreateInstance](http://msdn.microsoft.com/library/c0965041-6cb6-40c5-b272-2b99f02668a6)).</span><span class="sxs-lookup"><span data-stu-id="091a8-122">This method returns a new reader instance every time it is called (like [CComPtrBase::CoCreateInstance](http://msdn.microsoft.com/library/c0965041-6cb6-40c5-b272-2b99f02668a6)).</span></span> <span data-ttu-id="091a8-123">Par conséquent, le débogueur doit mettre en cache le résultat et demande une nouvelle instance uniquement lorsque les données sous-jacentes peuvent avoir changé (autrement dit, quand un [LoadClass, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) rappel est reçu).</span><span class="sxs-lookup"><span data-stu-id="091a8-123">Therefore, the debugger should cache the result and request a new instance only when the underlying data may have changed (that is, when a [LoadClass Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) callback is received).</span></span>  
  
 <span data-ttu-id="091a8-124">Les modules dynamiques n’ont pas de symboles disponibles jusqu'à ce que le premier type a été chargé (comme indiqué par le [méthode LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) rappel).</span><span class="sxs-lookup"><span data-stu-id="091a8-124">Dynamic modules do not have any symbols available until the first type has been loaded (as indicated by the [LoadClass Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) callback).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="091a8-125">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="091a8-125">Requirements</span></span>  
 <span data-ttu-id="091a8-126">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="091a8-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="091a8-127">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="091a8-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="091a8-128">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="091a8-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="091a8-129">**Versions du .NET framework :** 4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="091a8-129">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="091a8-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="091a8-130">See Also</span></span>  
 [<span data-ttu-id="091a8-131">ICorDebugRemoteTarget, interface</span><span class="sxs-lookup"><span data-stu-id="091a8-131">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [<span data-ttu-id="091a8-132">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="091a8-132">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="091a8-133">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="091a8-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
