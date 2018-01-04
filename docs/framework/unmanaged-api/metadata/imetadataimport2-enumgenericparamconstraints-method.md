---
title: "IMetaDataImport2::EnumGenericParamConstraints, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.EnumGenericParamConstraints
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::EnumGenericParamConstraints
helpviewer_keywords:
- EnumGenericParamConstraints method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParamConstraints method [.NET Framework metadata]
ms.assetid: 8a7d4e40-28fe-4e14-b801-4049880130e7
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72f863205c0fa7f4c6b4477c9d9143d1923a5d4c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="68289-102">IMetaDataImport2::EnumGenericParamConstraints, méthode</span><span class="sxs-lookup"><span data-stu-id="68289-102">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>
<span data-ttu-id="68289-103">Obtient un énumérateur pour un tableau de contraintes de paramètres génériques associé au paramètre générique représenté par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="68289-103">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68289-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68289-104">Syntax</span></span>  
  
```  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="68289-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="68289-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="68289-106">[dans, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="68289-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="68289-107">[in]   Jeton qui représente le paramètre générique dont les contraintes doivent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="68289-107">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="68289-108">[out] Tableau de contraintes de paramètre générique pour les énumérer.</span><span class="sxs-lookup"><span data-stu-id="68289-108">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="68289-109">[in]   Nombre maximal demandé de jetons à placer dans `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="68289-109">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="68289-110">[out] Un pointeur vers le nombre de jetons placés dans `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="68289-110">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="68289-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="68289-111">Return Value</span></span>  
  
|<span data-ttu-id="68289-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="68289-112">HRESULT</span></span>|<span data-ttu-id="68289-113">Description</span><span class="sxs-lookup"><span data-stu-id="68289-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="68289-114">`EnumGenericParameterConstraints`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="68289-114">`EnumGenericParameterConstraints` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="68289-115">`phEnum`ne contient aucun élément de membre.</span><span class="sxs-lookup"><span data-stu-id="68289-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="68289-116">Dans ce cas, `pcGenericParameterConstraints` est définie sur 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="68289-116">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="68289-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="68289-117">Requirements</span></span>  
 <span data-ttu-id="68289-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68289-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68289-119">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="68289-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="68289-120">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="68289-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="68289-121">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68289-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68289-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68289-122">See Also</span></span>  
 [<span data-ttu-id="68289-123">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="68289-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="68289-124">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="68289-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
