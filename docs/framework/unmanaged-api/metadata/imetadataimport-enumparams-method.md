---
title: "IMetaDataImport::EnumParams, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumParams
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumParams
helpviewer_keywords:
- IMetaDataImport::EnumParams method [.NET Framework metadata]
- EnumParams method [.NET Framework metadata]
ms.assetid: 52118dc9-fe6e-4b39-aa48-c3cc3ea4214d
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 42555e1300016222e9ea8064e90fa3062d79db6a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumparams-method"></a><span data-ttu-id="a0271-102">IMetaDataImport::EnumParams, méthode</span><span class="sxs-lookup"><span data-stu-id="a0271-102">IMetaDataImport::EnumParams Method</span></span>
<span data-ttu-id="a0271-103">Énumère les jetons ParamDef représentant les paramètres de la méthode référencée par le jeton MethodDef spécifié.</span><span class="sxs-lookup"><span data-stu-id="a0271-103">Enumerates ParamDef tokens representing the parameters of the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0271-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0271-104">Syntax</span></span>  
  
```  
HRESULT EnumParams (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,  
   [out] mdParamDef      rParams[],  
   [in]  ULONG           cMax,  
   [out] ULONG          *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0271-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a0271-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="a0271-106">[dans, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="a0271-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="a0271-107">Cela doit être NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="a0271-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="a0271-108">[in] Jeton MethodDef représentant la méthode avec les paramètres à énumérer.</span><span class="sxs-lookup"><span data-stu-id="a0271-108">[in] A MethodDef token representing the method with the parameters to enumerate.</span></span>  
  
 `rParams`  
 <span data-ttu-id="a0271-109">[out] Tableau utilisé pour stocker les jetons ParamDef.</span><span class="sxs-lookup"><span data-stu-id="a0271-109">[out] The array used to store the ParamDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a0271-110">[in] Taille maximale du tableau `rParams`.</span><span class="sxs-lookup"><span data-stu-id="a0271-110">[in] The maximum size of the `rParams` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="a0271-111">[out] Le nombre de jetons ParamDef retournés dans `rParams`.</span><span class="sxs-lookup"><span data-stu-id="a0271-111">[out] The number of ParamDef tokens returned in `rParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0271-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a0271-112">Return Value</span></span>  
  
|<span data-ttu-id="a0271-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a0271-113">HRESULT</span></span>|<span data-ttu-id="a0271-114">Description</span><span class="sxs-lookup"><span data-stu-id="a0271-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a0271-115">`EnumParams`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="a0271-115">`EnumParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a0271-116">Il n’existe pas de jetons à énumérer.</span><span class="sxs-lookup"><span data-stu-id="a0271-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="a0271-117">Dans ce cas, `pcTokens` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="a0271-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a0271-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a0271-118">Requirements</span></span>  
 <span data-ttu-id="a0271-119">**Plateforme :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0271-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0271-120">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a0271-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a0271-121">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a0271-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a0271-122">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0271-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0271-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0271-123">See Also</span></span>  
 [<span data-ttu-id="a0271-124">IMetaDataImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="a0271-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="a0271-125">IMetaDataImport2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="a0271-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
