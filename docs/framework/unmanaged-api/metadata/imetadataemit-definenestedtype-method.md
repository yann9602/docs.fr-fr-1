---
title: "IMetaDataEmit::DefineNestedType, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineNestedType
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineNestedType
helpviewer_keywords:
- IMetaDataEmit::DefineNestedType method [.NET Framework metadata]
- DefineNestedType method [.NET Framework metadata]
ms.assetid: 1e994de6-4628-459c-b967-b34be1e9fe4f
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 99250d98f9ffd90857128aa5d8a675a997926bf5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinenestedtype-method"></a><span data-ttu-id="20f7d-102">IMetaDataEmit::DefineNestedType, méthode</span><span class="sxs-lookup"><span data-stu-id="20f7d-102">IMetaDataEmit::DefineNestedType Method</span></span>
<span data-ttu-id="20f7d-103">Crée la signature de métadonnées d’une définition de type, retourne un `mdTypeDef` pour ce type de jeton et spécifie que le type défini est un membre du type référencé par le `tdEncloser` paramètre.</span><span class="sxs-lookup"><span data-stu-id="20f7d-103">Creates the metadata signature of a type definition, returns an `mdTypeDef` token for that type, and specifies that the defined type is a member of the type referenced by the `tdEncloser` parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20f7d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20f7d-104">Syntax</span></span>  
  
```  
HRESULT DefineNestedType (   
    [in]  LPCWSTR     szTypeDef,  
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [in]  mdTypeDef   tdEncloser,   
    [out] mdTypeDef   *ptd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20f7d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="20f7d-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="20f7d-106">[in] Le nom du type au format Unicode.</span><span class="sxs-lookup"><span data-stu-id="20f7d-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="20f7d-107">[in] `TypeDef` attributs.</span><span class="sxs-lookup"><span data-stu-id="20f7d-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="20f7d-108">Il s’agit d’un masque de bits de `CorTypeAttr` valeurs.</span><span class="sxs-lookup"><span data-stu-id="20f7d-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="20f7d-109">[in] Le jeton de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="20f7d-109">[in] The token of the base class.</span></span> <span data-ttu-id="20f7d-110">Il s’agit soit un `mdTypeDef` ou un `mdTypeRef` jeton.</span><span class="sxs-lookup"><span data-stu-id="20f7d-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 <span data-ttu-id="20f7d-111">`rtkImplements`[]</span><span class="sxs-lookup"><span data-stu-id="20f7d-111">`rtkImplements`[]</span></span>  
 <span data-ttu-id="20f7d-112">[in] Tableau des jetons qui spécifient les interfaces que cette classe ou interface implémente.</span><span class="sxs-lookup"><span data-stu-id="20f7d-112">[in] An array of tokens that specify the interfaces that this class or interface implements.</span></span>  
  
 `tdEncloser`  
 <span data-ttu-id="20f7d-113">[in] Le jeton du type englobant.</span><span class="sxs-lookup"><span data-stu-id="20f7d-113">[in] The token of the enclosing type.</span></span> <span data-ttu-id="20f7d-114">Le dernier élément du tableau doit être `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="20f7d-114">The last element of the array must be `mdTokenNil`.</span></span>  
  
 `ptd`  
 <span data-ttu-id="20f7d-115">[out] Le `mdTypeDef` jeton assigné.</span><span class="sxs-lookup"><span data-stu-id="20f7d-115">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20f7d-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="20f7d-116">Requirements</span></span>  
 <span data-ttu-id="20f7d-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20f7d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20f7d-118">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="20f7d-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="20f7d-119">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="20f7d-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20f7d-120">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20f7d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20f7d-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20f7d-121">See Also</span></span>  
 [<span data-ttu-id="20f7d-122">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="20f7d-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="20f7d-123">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="20f7d-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
