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
ms.openlocfilehash: 50f92d0ff307621695887ee7a0af2d4d19985f51
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="3e227-102">IMetaDataEmit::SetTypeDefProps, méthode</span><span class="sxs-lookup"><span data-stu-id="3e227-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="3e227-103">Définit les fonctionnalités d’un type défini par un appel antérieur à [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="3e227-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e227-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e227-104">Syntax</span></span>  
  
```  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[]   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3e227-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3e227-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="3e227-106">[in] Un `mdTypeDef` jeton obtenu à partir de l’appel d’origine à [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="3e227-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="3e227-107">[in] `TypeDef` attributs.</span><span class="sxs-lookup"><span data-stu-id="3e227-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="3e227-108">Il s’agit d’un masque de bits de `CorTypeAttr` valeurs.</span><span class="sxs-lookup"><span data-stu-id="3e227-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="3e227-109">[in] Le `mdToken` de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="3e227-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="3e227-110">Obtenu à partir d’un appel précédent à [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), ou `null`.</span><span class="sxs-lookup"><span data-stu-id="3e227-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="3e227-111">[in] Tableau de jetons pour les interfaces implémentées par ce type.</span><span class="sxs-lookup"><span data-stu-id="3e227-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="3e227-112">Ces `mdTypeRef` jetons sont obtenus à l’aide de [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="3e227-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="3e227-113">Le dernier élément du tableau est doit être `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="3e227-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e227-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3e227-114">Requirements</span></span>  
 <span data-ttu-id="3e227-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e227-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e227-116">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3e227-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3e227-117">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3e227-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e227-118">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e227-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e227-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e227-119">See Also</span></span>  
 [<span data-ttu-id="3e227-120">IMetaDataEmit (Interface)</span><span class="sxs-lookup"><span data-stu-id="3e227-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="3e227-121">IMetaDataEmit2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="3e227-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
