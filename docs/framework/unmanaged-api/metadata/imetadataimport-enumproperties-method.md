---
title: "IMetaDataImport::EnumProperties, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumProperties
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumProperties
helpviewer_keywords:
- IMetaDataImport::EnumProperties method [.NET Framework metadata]
- EnumProperties method [.NET Framework metadata]
ms.assetid: 60573ad7-8821-4721-a068-3f7a6d25926a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63ff10904440f55ec3fe6fb6aa581fbf560763e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumproperties-method"></a><span data-ttu-id="f60d9-102">IMetaDataImport::EnumProperties, méthode</span><span class="sxs-lookup"><span data-stu-id="f60d9-102">IMetaDataImport::EnumProperties Method</span></span>
<span data-ttu-id="f60d9-103">Énumère les jetons PropertyDef représentant les propriétés du type référencé par le jeton TypeDef spécifié.</span><span class="sxs-lookup"><span data-stu-id="f60d9-103">Enumerates PropertyDef tokens representing the properties of the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f60d9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f60d9-104">Syntax</span></span>  
  
```  
HRESULT EnumProperties (  
   [in, out] HCORENUM    *phEnum,  
   [in]      mdTypeDef   td,  
   [out]     mdProperty  rProperties[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcProperties  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f60d9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f60d9-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="f60d9-106">[dans, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="f60d9-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="f60d9-107">Cela doit être NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="f60d9-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="f60d9-108">[in] Jeton TypeDef représentant le type avec des propriétés à énumérer.</span><span class="sxs-lookup"><span data-stu-id="f60d9-108">[in] A TypeDef token representing the type with properties to enumerate.</span></span>  
  
 `rProperties`  
 <span data-ttu-id="f60d9-109">[out] Tableau utilisé pour stocker les jetons PropertyDef.</span><span class="sxs-lookup"><span data-stu-id="f60d9-109">[out] The array used to store the PropertyDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f60d9-110">[in] Taille maximale du tableau `rProperties`.</span><span class="sxs-lookup"><span data-stu-id="f60d9-110">[in] The maximum size of the `rProperties` array.</span></span>  
  
 `pcProperties`  
 <span data-ttu-id="f60d9-111">[out] Le nombre de jetons PropertyDef retournés dans `rProperties`.</span><span class="sxs-lookup"><span data-stu-id="f60d9-111">[out] The number of PropertyDef tokens returned in `rProperties`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f60d9-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f60d9-112">Return Value</span></span>  
  
|<span data-ttu-id="f60d9-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f60d9-113">HRESULT</span></span>|<span data-ttu-id="f60d9-114">Description</span><span class="sxs-lookup"><span data-stu-id="f60d9-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f60d9-115">`EnumProperties`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="f60d9-115">`EnumProperties` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f60d9-116">Il n’existe pas de jetons à énumérer.</span><span class="sxs-lookup"><span data-stu-id="f60d9-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="f60d9-117">Dans ce cas, `pcProperties` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="f60d9-117">In that case, `pcProperties` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f60d9-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f60d9-118">Requirements</span></span>  
 <span data-ttu-id="f60d9-119">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f60d9-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f60d9-120">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f60d9-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f60d9-121">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f60d9-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f60d9-122">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f60d9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f60d9-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f60d9-123">See Also</span></span>  
 [<span data-ttu-id="f60d9-124">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="f60d9-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="f60d9-125">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="f60d9-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
