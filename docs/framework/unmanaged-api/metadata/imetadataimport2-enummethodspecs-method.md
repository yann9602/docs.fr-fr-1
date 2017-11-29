---
title: "IMetaDataImport2::EnumMethodSpecs, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.EnumMethodSpecs
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::EnumMethodSpecs
helpviewer_keywords:
- IMetaDataImport2::EnumMethodSpecs method [.NET Framework metadata]
- EnumMethodSpecs method [.NET Framework metadata]
ms.assetid: b3fc1e6c-bcb6-4915-baf8-7dc0a31b8724
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: db1968c73d5a1c6e0687bc86f249c70b6c21712c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="59577-102">IMetaDataImport2::EnumMethodSpecs, méthode</span><span class="sxs-lookup"><span data-stu-id="59577-102">IMetaDataImport2::EnumMethodSpecs Method</span></span>
<span data-ttu-id="59577-103">Obtient un énumérateur pour un tableau de jetons MethodSpec associé MethodDef ou MemberRef spécifié de jeton.</span><span class="sxs-lookup"><span data-stu-id="59577-103">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59577-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59577-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,   
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="59577-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="59577-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="59577-106">[dans, out] Un pointeur vers l’énumérateur pour `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="59577-106">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="59577-107">[in] Jeton MemberRef ou MethodDef qui représente la méthode dont les jetons MethodSpec doivent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="59577-107">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="59577-108">Si la valeur de `tk` est 0 (zéro), tous les jetons MethodSpec dans la portée seront énumérés.</span><span class="sxs-lookup"><span data-stu-id="59577-108">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="59577-109">[out] Tableau de jetons MethodSpec à énumérer.</span><span class="sxs-lookup"><span data-stu-id="59577-109">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="59577-110">[in] Nombre maximal demandé de jetons à placer dans `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="59577-110">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="59577-111">[out] Le nombre retourné de jetons placé dans `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="59577-111">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="59577-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="59577-112">Return Value</span></span>  
  
|<span data-ttu-id="59577-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="59577-113">HRESULT</span></span>|<span data-ttu-id="59577-114">Description</span><span class="sxs-lookup"><span data-stu-id="59577-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="59577-115">`EnumMethodSpecs`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="59577-115">`EnumMethodSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="59577-116">`phEnum`ne contient aucun élément de membre.</span><span class="sxs-lookup"><span data-stu-id="59577-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="59577-117">Dans ce cas, `pcMethodSpecs` est définie sur 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="59577-117">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="59577-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="59577-118">Requirements</span></span>  
 <span data-ttu-id="59577-119">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59577-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59577-120">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="59577-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="59577-121">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="59577-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="59577-122">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59577-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59577-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59577-123">See Also</span></span>  
 [<span data-ttu-id="59577-124">IMetaDataImport2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="59577-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="59577-125">IMetaDataImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="59577-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
