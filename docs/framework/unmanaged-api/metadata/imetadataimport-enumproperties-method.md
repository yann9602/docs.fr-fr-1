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
ms.openlocfilehash: d46e18707ff6b34e32a73aed81c2b7e57f769ed6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumproperties-method"></a><span data-ttu-id="75aaa-102">IMetaDataImport::EnumProperties, méthode</span><span class="sxs-lookup"><span data-stu-id="75aaa-102">IMetaDataImport::EnumProperties Method</span></span>
<span data-ttu-id="75aaa-103">Énumère les jetons PropertyDef représentant les propriétés du type référencé par le jeton TypeDef spécifié.</span><span class="sxs-lookup"><span data-stu-id="75aaa-103">Enumerates PropertyDef tokens representing the properties of the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75aaa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75aaa-104">Syntax</span></span>  
  
```  
HRESULT EnumProperties (  
   [in, out] HCORENUM    *phEnum,  
   [in]      mdTypeDef   td,  
   [out]     mdProperty  rProperties[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcProperties  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="75aaa-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="75aaa-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="75aaa-106">[dans, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="75aaa-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="75aaa-107">Cela doit être NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="75aaa-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="75aaa-108">[in] Jeton TypeDef représentant le type avec des propriétés à énumérer.</span><span class="sxs-lookup"><span data-stu-id="75aaa-108">[in] A TypeDef token representing the type with properties to enumerate.</span></span>  
  
 `rProperties`  
 <span data-ttu-id="75aaa-109">[out] Tableau utilisé pour stocker les jetons PropertyDef.</span><span class="sxs-lookup"><span data-stu-id="75aaa-109">[out] The array used to store the PropertyDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="75aaa-110">[in] Taille maximale du tableau `rProperties`.</span><span class="sxs-lookup"><span data-stu-id="75aaa-110">[in] The maximum size of the `rProperties` array.</span></span>  
  
 `pcProperties`  
 <span data-ttu-id="75aaa-111">[out] Le nombre de jetons PropertyDef retournés dans `rProperties`.</span><span class="sxs-lookup"><span data-stu-id="75aaa-111">[out] The number of PropertyDef tokens returned in `rProperties`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="75aaa-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="75aaa-112">Return Value</span></span>  
  
|<span data-ttu-id="75aaa-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="75aaa-113">HRESULT</span></span>|<span data-ttu-id="75aaa-114">Description</span><span class="sxs-lookup"><span data-stu-id="75aaa-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="75aaa-115">`EnumProperties`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="75aaa-115">`EnumProperties` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="75aaa-116">Il n’existe pas de jetons à énumérer.</span><span class="sxs-lookup"><span data-stu-id="75aaa-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="75aaa-117">Dans ce cas, `pcProperties` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="75aaa-117">In that case, `pcProperties` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="75aaa-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="75aaa-118">Requirements</span></span>  
 <span data-ttu-id="75aaa-119">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75aaa-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75aaa-120">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="75aaa-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="75aaa-121">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="75aaa-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="75aaa-122">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75aaa-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75aaa-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75aaa-123">See Also</span></span>  
 [<span data-ttu-id="75aaa-124">IMetaDataImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="75aaa-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="75aaa-125">IMetaDataImport2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="75aaa-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
