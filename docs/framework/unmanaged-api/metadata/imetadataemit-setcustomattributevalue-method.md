---
title: "IMetaDataEmit::SetCustomAttributeValue, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetCustomAttributeValue
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetCustomAttributeValue
helpviewer_keywords:
- SetCustomAttributeValue method [.NET Framework metadata]
- IMetaDataEmit::SetCustomAttributeValue method [.NET Framework metadata]
ms.assetid: f721c863-9642-4e64-917a-65f9e55c25b9
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 30538b0f6f6aa196edf8373f5f4e6f09ba903223
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetcustomattributevalue-method"></a><span data-ttu-id="9fafd-102">IMetaDataEmit::SetCustomAttributeValue, méthode</span><span class="sxs-lookup"><span data-stu-id="9fafd-102">IMetaDataEmit::SetCustomAttributeValue Method</span></span>
<span data-ttu-id="9fafd-103">Définit ou met à jour la valeur d’un attribut personnalisé défini par un appel antérieur à [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span><span class="sxs-lookup"><span data-stu-id="9fafd-103">Sets or updates the value of a custom attribute defined by a prior call to [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fafd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9fafd-104">Syntax</span></span>  
  
```  
HRESULT SetCustomAttributeValue (   
    [in]  mdCustomAttribute       pcv,   
    [in]  void const              *pCustomAttribute,    
    [in]  ULONG                   cbCustomAttribute   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9fafd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9fafd-105">Parameters</span></span>  
 `pcv`  
 <span data-ttu-id="9fafd-106">[in] Le jeton de l’attribut personnalisé cible.</span><span class="sxs-lookup"><span data-stu-id="9fafd-106">[in] The token of the target custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="9fafd-107">[in] Pointeur vers le tableau qui contient l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="9fafd-107">[in] A pointer to the array that contains the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="9fafd-108">[in] La taille, en octets, de l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="9fafd-108">[in] The size, in bytes, of the custom attribute.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fafd-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9fafd-109">Requirements</span></span>  
 <span data-ttu-id="9fafd-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fafd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fafd-111">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9fafd-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9fafd-112">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9fafd-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9fafd-113">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fafd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fafd-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9fafd-114">See Also</span></span>  
 [<span data-ttu-id="9fafd-115">IMetaDataEmit (Interface)</span><span class="sxs-lookup"><span data-stu-id="9fafd-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="9fafd-116">IMetaDataEmit2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="9fafd-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
