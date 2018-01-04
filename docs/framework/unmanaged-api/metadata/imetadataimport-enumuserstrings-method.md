---
title: "IMetaDataImport::EnumUserStrings, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumUserStrings
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumUserStrings
helpviewer_keywords:
- IMetaDataImport::EnumUserStrings method [.NET Framework metadata]
- EnumUserStrings method [.NET Framework metadata]
ms.assetid: 2b1f1418-4be8-4cdb-b418-b3abccc527a7
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3d9c802318203db2ccd6043cded3c7730b18b0cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumuserstrings-method"></a><span data-ttu-id="77f28-102">IMetaDataImport::EnumUserStrings, méthode</span><span class="sxs-lookup"><span data-stu-id="77f28-102">IMetaDataImport::EnumUserStrings Method</span></span>
<span data-ttu-id="77f28-103">Énumère les jetons String représentant des chaînes codées en dur dans la portée des métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="77f28-103">Enumerates String tokens representing hard-coded strings in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77f28-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77f28-104">Syntax</span></span>  
  
```  
HRESULT EnumUserStrings (  
   [in, out]  HCORENUM    *phEnum,  
   [out]  mdString        rStrings[],  
   [in]   ULONG           cMax,  
   [out]  ULONG           *pcStrings  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="77f28-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="77f28-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="77f28-106">[dans, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="77f28-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="77f28-107">Cela doit être NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="77f28-107">This must be NULL for the first call of this method.</span></span>  
  
 `rStrings`  
 <span data-ttu-id="77f28-108">[out] Tableau utilisé pour stocker les jetons de chaîne.</span><span class="sxs-lookup"><span data-stu-id="77f28-108">[out] The array used to store the String tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="77f28-109">[in] Taille maximale du tableau `rStrings`.</span><span class="sxs-lookup"><span data-stu-id="77f28-109">[in] The maximum size of the `rStrings` array.</span></span>  
  
 `pcStrings`  
 <span data-ttu-id="77f28-110">[out] Le nombre de jetons de chaîne retournée dans `rStrings`.</span><span class="sxs-lookup"><span data-stu-id="77f28-110">[out] The number of String tokens returned in `rStrings`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77f28-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="77f28-111">Return Value</span></span>  
  
|<span data-ttu-id="77f28-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="77f28-112">HRESULT</span></span>|<span data-ttu-id="77f28-113">Description</span><span class="sxs-lookup"><span data-stu-id="77f28-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="77f28-114">`EnumUserStrings`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="77f28-114">`EnumUserStrings` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="77f28-115">Il n’existe pas de jetons à énumérer.</span><span class="sxs-lookup"><span data-stu-id="77f28-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="77f28-116">Dans ce cas, `pcStrings` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="77f28-116">In that case, `pcStrings` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77f28-117">Notes</span><span class="sxs-lookup"><span data-stu-id="77f28-117">Remarks</span></span>  
 <span data-ttu-id="77f28-118">Les jetons String sont créés par le [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="77f28-118">The String tokens are created by the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span> <span data-ttu-id="77f28-119">Cette méthode est conçue pour être utilisée par un navigateur de métadonnées plutôt que par un compilateur.</span><span class="sxs-lookup"><span data-stu-id="77f28-119">This method is designed to be used by a metadata browser rather than by a compiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77f28-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="77f28-120">Requirements</span></span>  
 <span data-ttu-id="77f28-121">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77f28-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77f28-122">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="77f28-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="77f28-123">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="77f28-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="77f28-124">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77f28-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77f28-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77f28-125">See Also</span></span>  
 [<span data-ttu-id="77f28-126">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="77f28-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="77f28-127">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="77f28-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
