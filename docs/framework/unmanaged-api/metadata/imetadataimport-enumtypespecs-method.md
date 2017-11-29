---
title: "IMetaDataImport::EnumTypeSpecs, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumTypeSpecs
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumTypeSpecs
helpviewer_keywords:
- EnumTypeSpecs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeSpecs method [.NET Framework metadata]
ms.assetid: 75331c7b-988b-436c-9eb9-a270d37b4f06
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a872af384a8df624178d8d37d5ad98a0b5c561d1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumtypespecs-method"></a><span data-ttu-id="09290-102">IMetaDataImport::EnumTypeSpecs, méthode</span><span class="sxs-lookup"><span data-stu-id="09290-102">IMetaDataImport::EnumTypeSpecs Method</span></span>
<span data-ttu-id="09290-103">Énumère les jetons TypeSpec définis dans la portée des métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="09290-103">Enumerates TypeSpec tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09290-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09290-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="09290-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="09290-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="09290-106">[dans, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="09290-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="09290-107">Cette valeur doit être NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="09290-107">This value must be NULL for the first call of this method.</span></span>  
  
 `rTypeSpecs`  
 <span data-ttu-id="09290-108">[out] Tableau utilisé pour stocker les jetons TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="09290-108">[out] The array used to store the TypeSpec tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="09290-109">[in] Taille maximale du tableau `rTypeSpecs`.</span><span class="sxs-lookup"><span data-stu-id="09290-109">[in] The maximum size of the `rTypeSpecs` array.</span></span>  
  
 `pcTypeSpecs`  
 <span data-ttu-id="09290-110">[out] Le nombre de jetons TypeSpec retournés dans `rTypeSpecs`.</span><span class="sxs-lookup"><span data-stu-id="09290-110">[out] The number of TypeSpec tokens returned in `rTypeSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09290-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="09290-111">Return Value</span></span>  
  
|<span data-ttu-id="09290-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="09290-112">HRESULT</span></span>|<span data-ttu-id="09290-113">Description</span><span class="sxs-lookup"><span data-stu-id="09290-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="09290-114">`EnumTypeSpecs`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="09290-114">`EnumTypeSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="09290-115">Il n’existe pas de jetons à énumérer.</span><span class="sxs-lookup"><span data-stu-id="09290-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="09290-116">Dans ce cas, `pcTypeSpecs` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="09290-116">In that case, `pcTypeSpecs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09290-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="09290-117">Remarks</span></span>  
 <span data-ttu-id="09290-118">Les jetons TypeSpec sont créés par le [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="09290-118">The TypeSpec tokens are created by the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09290-119">Spécifications</span><span class="sxs-lookup"><span data-stu-id="09290-119">Requirements</span></span>  
 <span data-ttu-id="09290-120">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09290-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09290-121">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="09290-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="09290-122">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="09290-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="09290-123">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09290-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09290-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09290-124">See Also</span></span>  
 [<span data-ttu-id="09290-125">IMetaDataImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="09290-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="09290-126">IMetaDataImport2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="09290-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
