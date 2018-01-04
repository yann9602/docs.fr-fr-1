---
title: "IMetaDataEmit::SetTypeDefProps, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetTypeDefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetTypeDefProps
helpviewer_keywords:
- SetTypeDefProps method [.NET Framework metadata]
- IMetaDataEmit::SetTypeDefProps method [.NET Framework metadata]
ms.assetid: 480d596a-759f-4d29-ac1a-3dbff8f3544d
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a03b781865b55b832b34bfdab7c88ce33f4e9e12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="f36cb-102">IMetaDataEmit::SetTypeDefProps, méthode</span><span class="sxs-lookup"><span data-stu-id="f36cb-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="f36cb-103">Définit les fonctionnalités d’un type défini par un appel antérieur à [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="f36cb-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f36cb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f36cb-104">Syntax</span></span>  
  
```  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[]   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f36cb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f36cb-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="f36cb-106">[in] Un `mdTypeDef` jeton obtenu à partir de l’appel d’origine à [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="f36cb-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="f36cb-107">[in] `TypeDef` attributs.</span><span class="sxs-lookup"><span data-stu-id="f36cb-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="f36cb-108">Il s’agit d’un masque de bits de `CorTypeAttr` valeurs.</span><span class="sxs-lookup"><span data-stu-id="f36cb-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="f36cb-109">[in] Le `mdToken` de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="f36cb-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="f36cb-110">Obtenu à partir d’un appel précédent à [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), ou `null`.</span><span class="sxs-lookup"><span data-stu-id="f36cb-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="f36cb-111">[in] Tableau de jetons pour les interfaces implémentées par ce type.</span><span class="sxs-lookup"><span data-stu-id="f36cb-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="f36cb-112">Ces `mdTypeRef` jetons sont obtenus à l’aide de [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="f36cb-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="f36cb-113">Le dernier élément du tableau est doit être `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="f36cb-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f36cb-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f36cb-114">Requirements</span></span>  
 <span data-ttu-id="f36cb-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f36cb-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f36cb-116">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f36cb-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f36cb-117">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f36cb-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f36cb-118">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f36cb-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f36cb-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f36cb-119">See Also</span></span>  
 [<span data-ttu-id="f36cb-120">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="f36cb-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="f36cb-121">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="f36cb-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
