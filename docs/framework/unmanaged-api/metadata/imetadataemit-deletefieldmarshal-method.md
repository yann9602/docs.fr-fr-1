---
title: "IMetaDataEmit::DeleteFieldMarshal, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DeleteFieldMarshal
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DeleteFieldMarshal
helpviewer_keywords:
- IMetaDataEmit::DeleteFieldMarshal method [.NET Framework metadata]
- DeleteFieldMarshal method [.NET Framework metadata]
ms.assetid: 7c75aef9-c742-4b33-a14b-56ff94b0f725
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f66307a2589a824db0f8ce9dca737e6b201dad59
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdeletefieldmarshal-method"></a><span data-ttu-id="e67c4-102">IMetaDataEmit::DeleteFieldMarshal, méthode</span><span class="sxs-lookup"><span data-stu-id="e67c4-102">IMetaDataEmit::DeleteFieldMarshal Method</span></span>
<span data-ttu-id="e67c4-103">Détruit la signature de métadonnées pour l’objet référencé par le jeton spécifié de marshaling de PInvoke.</span><span class="sxs-lookup"><span data-stu-id="e67c4-103">Destroys the PInvoke marshaling metadata signature for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e67c4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e67c4-104">Syntax</span></span>  
  
```  
HRESULT DeleteFieldMarshal (  
    [in]  mdToken     tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e67c4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e67c4-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="e67c4-106">[in] Un `mdFieldDef` ou `mdParamDef` jeton qui représente le champ ou le paramètre pour lequel supprimer la signature de métadonnées de marshaling.</span><span class="sxs-lookup"><span data-stu-id="e67c4-106">[in] An `mdFieldDef` or `mdParamDef` token that represents the field or parameter for which to delete the marshaling metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e67c4-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e67c4-107">Requirements</span></span>  
 <span data-ttu-id="e67c4-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e67c4-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e67c4-109">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e67c4-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e67c4-110">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e67c4-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e67c4-111">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e67c4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e67c4-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e67c4-112">See Also</span></span>  
 [<span data-ttu-id="e67c4-113">IMetaDataEmit (Interface)</span><span class="sxs-lookup"><span data-stu-id="e67c4-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="e67c4-114">IMetaDataEmit2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="e67c4-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
