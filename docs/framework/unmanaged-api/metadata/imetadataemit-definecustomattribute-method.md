---
title: "IMetaDataEmit::DefineCustomAttribute, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineCustomAttribute
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineCustomAttribute
helpviewer_keywords:
- DefineCustomAttribute method [.NET Framework metadata]
- IMetaDataEmit::DefineCustomAttribute method [.NET Framework metadata]
ms.assetid: 7dd14854-b756-4401-b167-88ca576dc8f0
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 053601376f8b75e5469a3ef8a3d890a6c6620e28
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="502a3-102">IMetaDataEmit::DefineCustomAttribute, méthode</span><span class="sxs-lookup"><span data-stu-id="502a3-102">IMetaDataEmit::DefineCustomAttribute Method</span></span>
<span data-ttu-id="502a3-103">Crée une définition pour un attribut personnalisé avec la signature de métadonnées spécifiée, à joindre à l’objet spécifié et obtient un jeton pour cette définition d’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="502a3-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="502a3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="502a3-104">Syntax</span></span>  
  
```  
HRESULT DefineCustomAttribute (   
    [in]  mdToken     tkObj,   
    [in]  mdToken     tkType,   
    [in]  void const  *pCustomAttribute,   
    [in]  ULONG       cbCustomAttribute,   
    [out] mdCustomAttribute *pcv   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="502a3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="502a3-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="502a3-106">[in] Le jeton pour l’élément propriétaire.</span><span class="sxs-lookup"><span data-stu-id="502a3-106">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="502a3-107">[in] Jeton qui identifie l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="502a3-107">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="502a3-108">[in] Pointeur vers l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="502a3-108">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="502a3-109">[in] Le nombre d’octets dans `pCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="502a3-109">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="502a3-110">[out] Le `mdCustomAttribute` jeton assigné.</span><span class="sxs-lookup"><span data-stu-id="502a3-110">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="502a3-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="502a3-111">Requirements</span></span>  
 <span data-ttu-id="502a3-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="502a3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="502a3-113">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="502a3-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="502a3-114">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="502a3-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="502a3-115">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="502a3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="502a3-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="502a3-116">See Also</span></span>  
 [<span data-ttu-id="502a3-117">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="502a3-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="502a3-118">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="502a3-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
