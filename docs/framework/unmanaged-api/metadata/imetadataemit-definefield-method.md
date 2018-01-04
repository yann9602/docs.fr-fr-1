---
title: "IMetaDataEmit::DefineField, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineField
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e2c4b5604c3daec78744eb8902a30750571b9f82
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="f896a-102">IMetaDataEmit::DefineField, méthode</span><span class="sxs-lookup"><span data-stu-id="f896a-102">IMetaDataEmit::DefineField Method</span></span>
<span data-ttu-id="f896a-103">Crée une définition pour un champ avec la signature de métadonnées spécifiée et obtient un jeton pour cette définition de champ.</span><span class="sxs-lookup"><span data-stu-id="f896a-103">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f896a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f896a-104">Syntax</span></span>  
  
```  
HRESULT DefineField (   
    [in]  mdTypeDef   td,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwFieldFlags,   
    [in]  PCCOR_SIGNATURE pvSigBlob,   
    [in]  ULONG       cbSigBlob,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue,   
    [out] mdFieldDef  *pmd   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f896a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f896a-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="f896a-106">[in] Le `mdTypeDef` jeton pour l’interface ou la classe englobante.</span><span class="sxs-lookup"><span data-stu-id="f896a-106">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="f896a-107">[in] Le nom du champ au format Unicode.</span><span class="sxs-lookup"><span data-stu-id="f896a-107">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="f896a-108">[in] Les attributs de champ.</span><span class="sxs-lookup"><span data-stu-id="f896a-108">[in] The field attributes.</span></span> <span data-ttu-id="f896a-109">Il s’agit d’un masque de bits de `CorFieldAttr` valeurs.</span><span class="sxs-lookup"><span data-stu-id="f896a-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="f896a-110">[in] La signature de champ comme un objet BLOB.</span><span class="sxs-lookup"><span data-stu-id="f896a-110">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="f896a-111">[in] Le nombre d’octets dans `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="f896a-111">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlage`  
 <span data-ttu-id="f896a-112">[in] Le `ELEMENT_TYPE_`  *\**  pour la valeur de constante.</span><span class="sxs-lookup"><span data-stu-id="f896a-112">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="f896a-113">Il s’agit d’un `CorElementType` valeur.</span><span class="sxs-lookup"><span data-stu-id="f896a-113">This is a `CorElementType` value.</span></span> <span data-ttu-id="f896a-114">Si vous ne pas définir une valeur constante pour le champ, utilisez `ELEMENT_TYPE_END`.</span><span class="sxs-lookup"><span data-stu-id="f896a-114">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="f896a-115">[in] La valeur de constante pour le champ.</span><span class="sxs-lookup"><span data-stu-id="f896a-115">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="f896a-116">[in] La taille en caractères (Unicode) de `pValue`.</span><span class="sxs-lookup"><span data-stu-id="f896a-116">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="f896a-117">[out] Le `mdFieldDef` jeton assigné.</span><span class="sxs-lookup"><span data-stu-id="f896a-117">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f896a-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f896a-118">Requirements</span></span>  
 <span data-ttu-id="f896a-119">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f896a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f896a-120">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f896a-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f896a-121">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f896a-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f896a-122">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f896a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f896a-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f896a-123">See Also</span></span>  
 [<span data-ttu-id="f896a-124">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="f896a-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="f896a-125">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="f896a-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
