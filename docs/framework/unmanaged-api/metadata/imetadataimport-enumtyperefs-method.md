---
title: "IMetaDataImport::EnumTypeRefs, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumTypeRefs
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumTypeRefs
helpviewer_keywords:
- EnumTypeRefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeRefs method [.NET Framework metadata]
ms.assetid: b4896b8f-8e97-469c-8089-e72a025661b5
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3099f129abd3477aeb08526b9f0dcd5b701d4dc8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="94c36-102">IMetaDataImport::EnumTypeRefs, méthode</span><span class="sxs-lookup"><span data-stu-id="94c36-102">IMetaDataImport::EnumTypeRefs Method</span></span>
<span data-ttu-id="94c36-103">Énumère les jetons TypeRef définis dans la portée des métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="94c36-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94c36-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94c36-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,   
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTypeRefs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="94c36-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="94c36-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="94c36-106">[dans, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="94c36-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="94c36-107">Cela doit être NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="94c36-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="94c36-108">[out] Tableau utilisé pour stocker les jetons TypeRef.</span><span class="sxs-lookup"><span data-stu-id="94c36-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="94c36-109">[in] Taille maximale du tableau `rTypeRefs`.</span><span class="sxs-lookup"><span data-stu-id="94c36-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="94c36-110">[out] Un pointeur vers le nombre de jetons TypeRef retournés dans `rTypeRefs`.</span><span class="sxs-lookup"><span data-stu-id="94c36-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="94c36-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="94c36-111">Return Value</span></span>  
  
|<span data-ttu-id="94c36-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="94c36-112">HRESULT</span></span>|<span data-ttu-id="94c36-113">Description</span><span class="sxs-lookup"><span data-stu-id="94c36-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="94c36-114">`EnumTypeRefs`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="94c36-114">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="94c36-115">Il n’existe pas de jetons à énumérer.</span><span class="sxs-lookup"><span data-stu-id="94c36-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="94c36-116">Dans ce cas, `pcTypeRefs` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="94c36-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94c36-117">Notes</span><span class="sxs-lookup"><span data-stu-id="94c36-117">Remarks</span></span>  
 <span data-ttu-id="94c36-118">Un jeton TypeRef représente une référence à un type.</span><span class="sxs-lookup"><span data-stu-id="94c36-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94c36-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="94c36-119">Requirements</span></span>  
 <span data-ttu-id="94c36-120">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94c36-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94c36-121">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="94c36-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="94c36-122">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="94c36-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="94c36-123">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94c36-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94c36-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94c36-124">See Also</span></span>  
 [<span data-ttu-id="94c36-125">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="94c36-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="94c36-126">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="94c36-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
