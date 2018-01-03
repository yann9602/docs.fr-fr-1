---
title: "ICorDebugModule::GetMetaDataInterface, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetMetaDataInterface
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetMetaDataInterface
helpviewer_keywords:
- ICorDebugModule::GetMetaDatainterface method [.NET Framework debugging]
- GetMetaDatainterface method [.NET Framework debugging]
ms.assetid: 30d906f2-cf35-4fa9-9d4c-0c31b58c9f3a
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d374b83155ccc8511c6e3217a8a49819d81a7d48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodulegetmetadatainterface-method"></a><span data-ttu-id="17d5d-102">ICorDebugModule::GetMetaDataInterface, méthode</span><span class="sxs-lookup"><span data-stu-id="17d5d-102">ICorDebugModule::GetMetaDataInterface Method</span></span>
<span data-ttu-id="17d5d-103">Obtient un objet d’interface de métadonnées qui peut être utilisé pour examiner les métadonnées pour le module.</span><span class="sxs-lookup"><span data-stu-id="17d5d-103">Gets a metadata interface object that can be used to examine the metadata for the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17d5d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17d5d-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="17d5d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="17d5d-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="17d5d-106">[in] L’ID de référence qui spécifie l’interface de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="17d5d-106">[in] The reference ID that specifies the metadata interface.</span></span>  
  
 `ppObj`  
 <span data-ttu-id="17d5d-107">[out] Un pointeur vers l’adresse d’un `T:IUnknown` objet qui est un de le [interfaces de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="17d5d-107">[out] A pointer to the address of an `T:IUnknown` object that is one of the [metadata interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17d5d-108">Notes</span><span class="sxs-lookup"><span data-stu-id="17d5d-108">Remarks</span></span>  
 <span data-ttu-id="17d5d-109">Le débogueur peut utiliser le `GetMetaDataInterface` méthode pour effectuer une copie des métadonnées d’origine pour un module, qu’il doit effectuer pour pouvoir modifier ce module.</span><span class="sxs-lookup"><span data-stu-id="17d5d-109">The debugger can use the `GetMetaDataInterface` method to make a copy of the original metadata for a module, which it must do in order to edit that module.</span></span> <span data-ttu-id="17d5d-110">Le débogueur appelle `GetMetaDataInterface` pour obtenir un [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) objet d’interface pour le module, puis appelle [IMetaDataEmit::SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) pour enregistrer une copie de métadonnées du module dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="17d5d-110">The debugger calls `GetMetaDataInterface` to get an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface object for the module, then calls [IMetaDataEmit::SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) to save a copy of the module's metadata to memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17d5d-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="17d5d-111">Requirements</span></span>  
 <span data-ttu-id="17d5d-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17d5d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17d5d-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="17d5d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17d5d-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17d5d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17d5d-115">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17d5d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17d5d-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17d5d-116">See Also</span></span>  
 [<span data-ttu-id="17d5d-117">Métadonnées</span><span class="sxs-lookup"><span data-stu-id="17d5d-117">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)
