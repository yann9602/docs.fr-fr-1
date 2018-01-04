---
title: "IMetaDataEmit::DeletePinvokeMap, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DeletePinvokeMap
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DeletePinvokeMap
helpviewer_keywords:
- IMetaDataEmit::DeletePinvokeMap method [.NET Framework metadata]
- DeletePinvokeMap method [.NET Framework metadata]
ms.assetid: 3c4f6b54-5ce7-4a2a-83e1-6dec16441f50
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1479c3fb19feec0e42ee4aec8544a35ce51350a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="5f65f-102">IMetaDataEmit::DeletePinvokeMap, méthode</span><span class="sxs-lookup"><span data-stu-id="5f65f-102">IMetaDataEmit::DeletePinvokeMap Method</span></span>
<span data-ttu-id="5f65f-103">Supprime les métadonnées de mappage PInvoke pour l’objet référencé par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="5f65f-103">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f65f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f65f-104">Syntax</span></span>  
  
```  
HRESULT DeletePinvokeMap (   
    [in]  mdToken     tk   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5f65f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5f65f-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="5f65f-106">[in] Un `mdFieldDef` ou `mdMethodDef` jeton qui représente l’objet pour lequel supprimer les métadonnées de mappage PInvoke.</span><span class="sxs-lookup"><span data-stu-id="5f65f-106">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f65f-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5f65f-107">Requirements</span></span>  
 <span data-ttu-id="5f65f-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f65f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f65f-109">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5f65f-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5f65f-110">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5f65f-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5f65f-111">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f65f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f65f-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f65f-112">See Also</span></span>  
 [<span data-ttu-id="5f65f-113">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="5f65f-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="5f65f-114">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="5f65f-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
