---
title: "ICorDebugModule::GetToken, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetToken
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetToken
helpviewer_keywords:
- ICorDebugModule::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: f759f87a-18ae-4c1a-8300-29b803432d0a
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 651612b07a69f0cbcc9c818fe7627bf496f6d68e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodulegettoken-method"></a><span data-ttu-id="921c0-102">ICorDebugModule::GetToken, méthode</span><span class="sxs-lookup"><span data-stu-id="921c0-102">ICorDebugModule::GetToken Method</span></span>
<span data-ttu-id="921c0-103">Obtient le jeton de l’entrée de table pour ce module.</span><span class="sxs-lookup"><span data-stu-id="921c0-103">Gets the token for the table entry for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="921c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="921c0-104">Syntax</span></span>  
  
```  
HRESULT GetToken(  
    [out] mdModule *pToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="921c0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="921c0-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="921c0-106">[out] Un pointeur vers le `mdModule` jeton qui fait référence à des métadonnées du module.</span><span class="sxs-lookup"><span data-stu-id="921c0-106">[out] A pointer to the `mdModule` token that references the module's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="921c0-107">Notes</span><span class="sxs-lookup"><span data-stu-id="921c0-107">Remarks</span></span>  
 <span data-ttu-id="921c0-108">Le jeton peut être passé à la [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md), et [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interfaces d’importation de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="921c0-108">The token can be passed to the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md), and [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) metadata import interfaces.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="921c0-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="921c0-109">Requirements</span></span>  
 <span data-ttu-id="921c0-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="921c0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="921c0-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="921c0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="921c0-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="921c0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="921c0-113">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="921c0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="921c0-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="921c0-114">See Also</span></span>  
 [<span data-ttu-id="921c0-115">Métadonnées</span><span class="sxs-lookup"><span data-stu-id="921c0-115">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)
