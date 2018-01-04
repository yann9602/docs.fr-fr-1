---
title: "IMetaDataEmit::DefineTypeDef, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineTypeDef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineTypeDef
helpviewer_keywords:
- IMetaDataEmit::DefineTypeDef method [.NET Framework metadata]
- DefineTypeDef method [.NET Framework metadata]
ms.assetid: dd11c485-be95-4b97-9cd8-68679a4fb432
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da8fed37605252139428aa40bb3785c242d95cac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinetypedef-method"></a><span data-ttu-id="a65ac-102">IMetaDataEmit::DefineTypeDef, méthode</span><span class="sxs-lookup"><span data-stu-id="a65ac-102">IMetaDataEmit::DefineTypeDef Method</span></span>
<span data-ttu-id="a65ac-103">Crée une définition de type pour un type de common language runtime et obtient un jeton de métadonnées pour cette définition de type.</span><span class="sxs-lookup"><span data-stu-id="a65ac-103">Creates a type definition for a common language runtime type, and gets a metadata token for that type definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a65ac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a65ac-104">Syntax</span></span>  
  
```  
HRESULT DefineTypeDef (   
    [in]  LPCWSTR     szTypeDef,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [out] mdTypeDef   *ptd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a65ac-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a65ac-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="a65ac-106">[in] Le nom du type au format Unicode.</span><span class="sxs-lookup"><span data-stu-id="a65ac-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="a65ac-107">[in] `TypeDef` attributs.</span><span class="sxs-lookup"><span data-stu-id="a65ac-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="a65ac-108">Il s’agit d’un masque de bits de `CoreTypeAttr` valeurs.</span><span class="sxs-lookup"><span data-stu-id="a65ac-108">This is a bitmask of `CoreTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="a65ac-109">[in] Le jeton de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="a65ac-109">[in] The token of the base class.</span></span> <span data-ttu-id="a65ac-110">Il doit être un `mdTypeDef` ou un `mdTypeRef` jeton.</span><span class="sxs-lookup"><span data-stu-id="a65ac-110">It must be either an `mdTypeDef` or an `mdTypeRef` token.</span></span>  
  
 `rtkImplements`  
 <span data-ttu-id="a65ac-111">[in] Tableau des jetons spécifiant les interfaces que cette classe ou interface implémente.</span><span class="sxs-lookup"><span data-stu-id="a65ac-111">[in] An array of tokens specifying the interfaces that this class or interface implements.</span></span>  
  
 `ptd`  
 <span data-ttu-id="a65ac-112">[out] Le `mdTypeDef` jeton assigné.</span><span class="sxs-lookup"><span data-stu-id="a65ac-112">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a65ac-113">Notes</span><span class="sxs-lookup"><span data-stu-id="a65ac-113">Remarks</span></span>  
 <span data-ttu-id="a65ac-114">Un indicateur dans `dwTypeDefFlags` Spécifie si le type en cours de création est un type système référence type commun (classe ou interface) ou un type de valeur système type commun.</span><span class="sxs-lookup"><span data-stu-id="a65ac-114">A flag in `dwTypeDefFlags` specifies whether the type being created is a common type system reference type (class or interface) or a common type system value type.</span></span>  
  
 <span data-ttu-id="a65ac-115">Selon les paramètres fournis, cette méthode, un effet secondaire peut également créer un `mdInterfaceImpl` enregistrement pour chaque interface héritée ou implémentée par ce type.</span><span class="sxs-lookup"><span data-stu-id="a65ac-115">Depending on the parameters supplied, this method, as a side effect, may also create an `mdInterfaceImpl` record for each interface that is inherited or implemented by this type.</span></span> <span data-ttu-id="a65ac-116">Toutefois, cette méthode ne retourne pas un de ces `mdInterfaceImpl` jetons.</span><span class="sxs-lookup"><span data-stu-id="a65ac-116">However, this method does not return any of these `mdInterfaceImpl` tokens.</span></span> <span data-ttu-id="a65ac-117">Si un client souhaite ultérieurement ajouter ou modifier un `mdInterfaceImpl` jeton, elle doit utiliser le `IMetaDataImport` interface pour les énumérer.</span><span class="sxs-lookup"><span data-stu-id="a65ac-117">If a client wants to later add or modify an `mdInterfaceImpl` token, it must use the `IMetaDataImport` interface to enumerate them.</span></span> <span data-ttu-id="a65ac-118">Si vous souhaitez utiliser une sémantique COM de le `[default]` interface, vous devez fournir l’interface par défaut en tant que le premier élément de `rtkImplements`; un attribut personnalisé est défini sur la classe indiquera que la classe possède une interface par défaut (qui est censé toujours pour être le tout d’abord `mdInterfaceImpl` jeton déclaré pour la classe).</span><span class="sxs-lookup"><span data-stu-id="a65ac-118">If you want to use COM semantics of the `[default]` interface, you should supply the default interface as the first element in `rtkImplements`; a custom attribute set on the class will indicate that the class has a default interface (which is always assumed to be the first `mdInterfaceImpl` token declared for the class).</span></span>  
  
 <span data-ttu-id="a65ac-119">Chaque élément de la `rtkImplements` tableau contient un `mdTypeDef` ou `mdTypeRef` jeton.</span><span class="sxs-lookup"><span data-stu-id="a65ac-119">Each element of the `rtkImplements` array holds an `mdTypeDef` or `mdTypeRef` token.</span></span> <span data-ttu-id="a65ac-120">Le dernier élément du tableau doit être `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="a65ac-120">The last element in the array must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a65ac-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a65ac-121">Requirements</span></span>  
 <span data-ttu-id="a65ac-122">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a65ac-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a65ac-123">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a65ac-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a65ac-124">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a65ac-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a65ac-125">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a65ac-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a65ac-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a65ac-126">See Also</span></span>  
 [<span data-ttu-id="a65ac-127">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="a65ac-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="a65ac-128">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="a65ac-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
