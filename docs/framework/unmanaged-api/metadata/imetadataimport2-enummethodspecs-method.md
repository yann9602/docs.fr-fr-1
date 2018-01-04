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
ms.workload: dotnet
ms.openlocfilehash: 6e134d19eb6699f39e6d538f93f989b87ed8f37d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="924c0-102">IMetaDataImport2::EnumMethodSpecs, méthode</span><span class="sxs-lookup"><span data-stu-id="924c0-102">IMetaDataImport2::EnumMethodSpecs Method</span></span>
<span data-ttu-id="924c0-103">Obtient un énumérateur pour un tableau de jetons MethodSpec associé MethodDef ou MemberRef spécifié de jeton.</span><span class="sxs-lookup"><span data-stu-id="924c0-103">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="924c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="924c0-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,   
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="924c0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="924c0-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="924c0-106">[dans, out] Un pointeur vers l’énumérateur pour `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="924c0-106">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="924c0-107">[in] Jeton MemberRef ou MethodDef qui représente la méthode dont les jetons MethodSpec doivent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="924c0-107">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="924c0-108">Si la valeur de `tk` est 0 (zéro), tous les jetons MethodSpec dans la portée seront énumérés.</span><span class="sxs-lookup"><span data-stu-id="924c0-108">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="924c0-109">[out] Tableau de jetons MethodSpec à énumérer.</span><span class="sxs-lookup"><span data-stu-id="924c0-109">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="924c0-110">[in] Nombre maximal demandé de jetons à placer dans `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="924c0-110">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="924c0-111">[out] Le nombre retourné de jetons placé dans `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="924c0-111">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="924c0-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="924c0-112">Return Value</span></span>  
  
|<span data-ttu-id="924c0-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="924c0-113">HRESULT</span></span>|<span data-ttu-id="924c0-114">Description</span><span class="sxs-lookup"><span data-stu-id="924c0-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="924c0-115">`EnumMethodSpecs`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="924c0-115">`EnumMethodSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="924c0-116">`phEnum`ne contient aucun élément de membre.</span><span class="sxs-lookup"><span data-stu-id="924c0-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="924c0-117">Dans ce cas, `pcMethodSpecs` est définie sur 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="924c0-117">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="924c0-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="924c0-118">Requirements</span></span>  
 <span data-ttu-id="924c0-119">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="924c0-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="924c0-120">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="924c0-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="924c0-121">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="924c0-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="924c0-122">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="924c0-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="924c0-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="924c0-123">See Also</span></span>  
 [<span data-ttu-id="924c0-124">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="924c0-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="924c0-125">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="924c0-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
