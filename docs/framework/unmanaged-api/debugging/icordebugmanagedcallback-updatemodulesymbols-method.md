---
title: "ICorDebugManagedCallback::UpdateModuleSymbols, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.UpdateModuleSymbols
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::UpdateModuleSymbols
helpviewer_keywords:
- UpdateModuleSymbols method [.NET Framework debugging]
- ICorDebugManagedCallback::UpdateModuleSymbols method [.NET Framework debugging]
ms.assetid: 0863f644-58e8-45a0-b0c3-a28e99b20938
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ad5a84268f3810a1fb73a21a6bd8106e82ccbd78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackupdatemodulesymbols-method"></a><span data-ttu-id="96c8b-102">ICorDebugManagedCallback::UpdateModuleSymbols, méthode</span><span class="sxs-lookup"><span data-stu-id="96c8b-102">ICorDebugManagedCallback::UpdateModuleSymbols Method</span></span>
<span data-ttu-id="96c8b-103">Notifie le débogueur que les symboles pour un module du common language runtime ont été modifiés.</span><span class="sxs-lookup"><span data-stu-id="96c8b-103">Notifies the debugger that the symbols for a common language runtime module have changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96c8b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96c8b-104">Syntax</span></span>  
  
```  
HRESULT UpdateModuleSymbols (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule,  
    [in] IStream            *pSymbolStream  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="96c8b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="96c8b-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="96c8b-106">[in] Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application qui contient le module dans lequel les symboles ont changé.</span><span class="sxs-lookup"><span data-stu-id="96c8b-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the module in which the symbols have changed.</span></span>  
  
 `pModule`  
 <span data-ttu-id="96c8b-107">[in] Pointeur vers un objet ICorDebugModule qui représente le module dans lequel les symboles ont changé.</span><span class="sxs-lookup"><span data-stu-id="96c8b-107">[in] A pointer to an ICorDebugModule object that represents the module in which the symbols have changed.</span></span>  
  
 `pSymbolStream`  
 <span data-ttu-id="96c8b-108">[in] Un pointeur vers un COM Win32 `IStream` objet qui contient les symboles modifiés.</span><span class="sxs-lookup"><span data-stu-id="96c8b-108">[in] A pointer to a Win32 COM `IStream` object that contains the modified symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96c8b-109">Notes</span><span class="sxs-lookup"><span data-stu-id="96c8b-109">Remarks</span></span>  
 <span data-ttu-id="96c8b-110">Cette méthode permet de mettre à jour l’affichage du débogueur des symboles d’un module en appelant [ISymUnmanagedReader::UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) ou [ISymUnmanagedReader::ReplaceSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span><span class="sxs-lookup"><span data-stu-id="96c8b-110">This method provides an opportunity to update the debugger's view of a module's symbols by calling [ISymUnmanagedReader::UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) or [ISymUnmanagedReader::ReplaceSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span></span>  
  
 <span data-ttu-id="96c8b-111">Ce rappel peut se produire plusieurs fois pour le même module.</span><span class="sxs-lookup"><span data-stu-id="96c8b-111">This callback can occur multiple times for the same module.</span></span>  
  
 <span data-ttu-id="96c8b-112">Un débogueur doit tenter de lier des points d’arrêt au niveau source indépendants.</span><span class="sxs-lookup"><span data-stu-id="96c8b-112">A debugger should try to bind unbound source-level breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96c8b-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="96c8b-113">Requirements</span></span>  
 <span data-ttu-id="96c8b-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96c8b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96c8b-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="96c8b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96c8b-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96c8b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96c8b-117">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96c8b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96c8b-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96c8b-118">See Also</span></span>  
 [<span data-ttu-id="96c8b-119">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="96c8b-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
