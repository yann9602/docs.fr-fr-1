---
title: "IMetaDataEmit::SetFieldMarshal, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetFieldMarshal
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetFieldMarshal
helpviewer_keywords:
- SetFieldMarshal method [.NET Framework metadata]
- IMetaDataEmit::SetFieldMarshal method [.NET Framework metadata]
ms.assetid: be232314-7f69-4855-bfab-63361bd22307
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 20186870510e67e518414d2bd5e9a00fd5164dc8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="a4d11-102">IMetaDataEmit::SetFieldMarshal, méthode</span><span class="sxs-lookup"><span data-stu-id="a4d11-102">IMetaDataEmit::SetFieldMarshal Method</span></span>
<span data-ttu-id="a4d11-103">Définit l’informations de marshaling pour le paramètre de retour de la méthode, champ ou la méthode référencée par le jeton spécifié de PInvoke.</span><span class="sxs-lookup"><span data-stu-id="a4d11-103">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4d11-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4d11-104">Syntax</span></span>  
  
```  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,   
    [in]  PCCOR_SIGNATURE  pvNativeType,   
    [in]  ULONG            cbNativeType   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a4d11-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a4d11-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="a4d11-106">[in] Le jeton pour l’élément de données cible.</span><span class="sxs-lookup"><span data-stu-id="a4d11-106">[in] The token for target data item.</span></span> <span data-ttu-id="a4d11-107">Il s’agit soit un `mdFieldDef` ou un `mdParamDef` jeton.</span><span class="sxs-lookup"><span data-stu-id="a4d11-107">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="a4d11-108">[in] Signature de type non managé.</span><span class="sxs-lookup"><span data-stu-id="a4d11-108">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="a4d11-109">[in] Le nombre d’octets dans `pvNativeType`.</span><span class="sxs-lookup"><span data-stu-id="a4d11-109">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4d11-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a4d11-110">Requirements</span></span>  
 <span data-ttu-id="a4d11-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4d11-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4d11-112">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a4d11-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a4d11-113">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a4d11-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a4d11-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4d11-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4d11-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4d11-115">See Also</span></span>  
 [<span data-ttu-id="a4d11-116">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="a4d11-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="a4d11-117">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="a4d11-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
