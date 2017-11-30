---
title: "IMetaDataImport::EnumMethodsWithName, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumMethodsWithName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumMethodsWithName
helpviewer_keywords:
- IMetaDataImport::EnumMethodsWithName method [.NET Framework metadata]
- EnumMethodsWithName method [.NET Framework metadata]
ms.assetid: a8624913-2e23-46ad-a0c1-bb8eccbbf20f
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: dadff8be283160ddc6049d0d2f8b78052e5c8ec5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenummethodswithname-method"></a><span data-ttu-id="b290f-102">IMetaDataImport::EnumMethodsWithName, méthode</span><span class="sxs-lookup"><span data-stu-id="b290f-102">IMetaDataImport::EnumMethodsWithName Method</span></span>
<span data-ttu-id="b290f-103">Énumère les méthodes portant le nom spécifié et définies par le type référencé par le jeton TypeDef spécifié.</span><span class="sxs-lookup"><span data-stu-id="b290f-103">Enumerates methods that have the specified name and that are defined by the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b290f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b290f-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodsWithName (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdTypeDef       cl,  
   [in]  LPCWSTR         szName,  
   [out] mdMethodDef     rMethods[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b290f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b290f-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="b290f-106">[dans, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="b290f-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="b290f-107">Cela doit être NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="b290f-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="b290f-108">[in] Un jeton TypeDef représentant le type dont les méthodes à énumérer.</span><span class="sxs-lookup"><span data-stu-id="b290f-108">[in] A TypeDef token representing the type whose methods to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="b290f-109">[in] Nom qui limite la portée de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="b290f-109">[in] The name that limits the scope of the enumeration.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="b290f-110">[out] Tableau utilisé pour stocker les jetons MethodDef.</span><span class="sxs-lookup"><span data-stu-id="b290f-110">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b290f-111">[in] Taille maximale du tableau `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="b290f-111">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="b290f-112">[out] Le nombre de jetons MethodDef retournés dans `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="b290f-112">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b290f-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="b290f-113">Remarks</span></span>  
 <span data-ttu-id="b290f-114">Cette méthode énumère des champs et méthodes, mais pas propriétés ou des événements.</span><span class="sxs-lookup"><span data-stu-id="b290f-114">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="b290f-115">Contrairement aux [IMetaDataImport::EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` ignore tous les jetons de méthode qui n’ont pas le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="b290f-115">Unlike [IMetaDataImport::EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` discards all method tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b290f-116">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b290f-116">Return Value</span></span>  
  
|<span data-ttu-id="b290f-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b290f-117">HRESULT</span></span>|<span data-ttu-id="b290f-118">Description</span><span class="sxs-lookup"><span data-stu-id="b290f-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b290f-119">`EnumMethodsWithName`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="b290f-119">`EnumMethodsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b290f-120">Il n’existe pas de jetons à énumérer.</span><span class="sxs-lookup"><span data-stu-id="b290f-120">There are no tokens to enumerate.</span></span> <span data-ttu-id="b290f-121">Dans ce cas, `pcTokens` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="b290f-121">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b290f-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b290f-122">Requirements</span></span>  
 <span data-ttu-id="b290f-123">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b290f-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b290f-124">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b290f-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b290f-125">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b290f-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b290f-126">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b290f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b290f-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b290f-127">See Also</span></span>  
 [<span data-ttu-id="b290f-128">IMetaDataImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="b290f-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="b290f-129">IMetaDataImport2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="b290f-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
