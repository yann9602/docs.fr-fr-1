---
title: "IMetaDataEmit::DefineParam, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineParam
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f4bf36edfad504f2858a45d5e34891042d8850bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefineparam-method"></a><span data-ttu-id="f6b7d-102">IMetaDataEmit::DefineParam, méthode</span><span class="sxs-lookup"><span data-stu-id="f6b7d-102">IMetaDataEmit::DefineParam Method</span></span>
<span data-ttu-id="f6b7d-103">Crée une définition de paramètre avec la signature spécifiée pour la méthode référencée par le jeton spécifié et obtient un jeton pour cette définition de paramètre.</span><span class="sxs-lookup"><span data-stu-id="f6b7d-103">Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6b7d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6b7d-104">Syntax</span></span>  
  
```  
HRESULT DefineParam (  
    [in]  mdMethodDef md,   
    [in]  ULONG       ulParamSeq,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwParamFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,  
    [in]  ULONG       cchValue,   
    [out] mdParamDef  *ppd   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f6b7d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f6b7d-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="f6b7d-106">[in] Le jeton pour la méthode dont le paramètre est défini.</span><span class="sxs-lookup"><span data-stu-id="f6b7d-106">[in] The token for the method whose parameter is being defined.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="f6b7d-107">[in] Numéro de séquence du paramètre.</span><span class="sxs-lookup"><span data-stu-id="f6b7d-107">[in] The parameter sequence number.</span></span>  
  
 `szName`  
 <span data-ttu-id="f6b7d-108">[in] Le nom du paramètre au format Unicode.</span><span class="sxs-lookup"><span data-stu-id="f6b7d-108">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="f6b7d-109">[in] Indicateurs pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="f6b7d-109">[in] Flags for the parameter.</span></span> <span data-ttu-id="f6b7d-110">Il s’agit d’un masque de bits de `CorParamAttr` valeurs.</span><span class="sxs-lookup"><span data-stu-id="f6b7d-110">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="f6b7d-111">[in] `ELEMENT_TYPE_`  *\**  pour la valeur de constante.</span><span class="sxs-lookup"><span data-stu-id="f6b7d-111">[in] `ELEMENT_TYPE_`*\** for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="f6b7d-112">[in] La valeur de constante pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="f6b7d-112">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="f6b7d-113">[in] La taille, en caractères Unicode de `pValue`.</span><span class="sxs-lookup"><span data-stu-id="f6b7d-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
 `ppd`  
 <span data-ttu-id="f6b7d-114">[out] Le `mdParamDef` jeton assigné.</span><span class="sxs-lookup"><span data-stu-id="f6b7d-114">[out] The `mdParamDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6b7d-115">Notes</span><span class="sxs-lookup"><span data-stu-id="f6b7d-115">Remarks</span></span>  
 <span data-ttu-id="f6b7d-116">Les valeurs de séquence dans `ulParamSeq` commencent à 1 pour les paramètres.</span><span class="sxs-lookup"><span data-stu-id="f6b7d-116">The sequence values in `ulParamSeq` begin with 1 for parameters.</span></span> <span data-ttu-id="f6b7d-117">Une valeur de retour a un numéro de séquence 0.</span><span class="sxs-lookup"><span data-stu-id="f6b7d-117">A return value has a sequence number of 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6b7d-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f6b7d-118">Requirements</span></span>  
 <span data-ttu-id="f6b7d-119">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6b7d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6b7d-120">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f6b7d-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f6b7d-121">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f6b7d-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f6b7d-122">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6b7d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6b7d-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6b7d-123">See Also</span></span>  
 [<span data-ttu-id="f6b7d-124">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="f6b7d-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="f6b7d-125">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="f6b7d-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
