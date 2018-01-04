---
title: "IMetaDataImport::EnumFieldsWithName, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumFieldsWithName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumFieldsWithName
helpviewer_keywords:
- IMetaDataImport::EnumFieldsWithName method [.NET Framework metadata]
- EnumFieldsWithName method [.NET Framework metadata]
ms.assetid: 42145e8d-000f-4d0b-ae43-c08201190fa2
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 77b5ba7e191d9aa0f1587e4ac1ec25e655c27b14
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumfieldswithname-method"></a><span data-ttu-id="21b69-102">IMetaDataImport::EnumFieldsWithName, méthode</span><span class="sxs-lookup"><span data-stu-id="21b69-102">IMetaDataImport::EnumFieldsWithName Method</span></span>
<span data-ttu-id="21b69-103">Énumère les jetons FieldDef du type spécifié avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="21b69-103">Enumerates FieldDef tokens of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21b69-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21b69-104">Syntax</span></span>  
  
```  
HRESULT EnumFieldsWithName (  
   [in, out] HCORENUM    *phEnum,   
   [in]  mdTypeDef       cl,   
   [in]  LPCWSTR         szName,   
   [out] mdFieldDef      rFields[],   
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTokens   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="21b69-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="21b69-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="21b69-106">[dans, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="21b69-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="21b69-107">[in] Le jeton du type dont les champs doivent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="21b69-107">[in] The token of the type whose fields are to be enumerated.</span></span>  
  
 `szName`  
 <span data-ttu-id="21b69-108">[in] Le nom du champ qui limite la portée de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="21b69-108">[in] The field name that limits the scope of the enumeration.</span></span>  
  
 `rFields`  
 <span data-ttu-id="21b69-109">[out] Tableau utilisé pour stocker les jetons FieldDef.</span><span class="sxs-lookup"><span data-stu-id="21b69-109">[out] Array used to store the FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="21b69-110">[in] Taille maximale du tableau `rFields`.</span><span class="sxs-lookup"><span data-stu-id="21b69-110">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="21b69-111">[out] Le nombre réel de jetons FieldDef retournés dans `rFields`.</span><span class="sxs-lookup"><span data-stu-id="21b69-111">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21b69-112">Notes</span><span class="sxs-lookup"><span data-stu-id="21b69-112">Remarks</span></span>  
 <span data-ttu-id="21b69-113">Contrairement aux [IMetaDataImport::EnumFields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md), `EnumFieldsWithName` ignore tous les jetons de champ qui n’ont pas le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="21b69-113">Unlike [IMetaDataImport::EnumFields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md), `EnumFieldsWithName` discards all field tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21b69-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="21b69-114">Return Value</span></span>  
  
|<span data-ttu-id="21b69-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="21b69-115">HRESULT</span></span>|<span data-ttu-id="21b69-116">Description</span><span class="sxs-lookup"><span data-stu-id="21b69-116">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="21b69-117">`EnumFieldsWithName`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="21b69-117">`EnumFieldsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="21b69-118">Il n’existe pas de champs à énumérer.</span><span class="sxs-lookup"><span data-stu-id="21b69-118">There are no fields to enumerate.</span></span> <span data-ttu-id="21b69-119">Dans ce cas, `pcTokens` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="21b69-119">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="21b69-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="21b69-120">Requirements</span></span>  
 <span data-ttu-id="21b69-121">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21b69-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21b69-122">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="21b69-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="21b69-123">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="21b69-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="21b69-124">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21b69-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21b69-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21b69-125">See Also</span></span>  
 [<span data-ttu-id="21b69-126">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="21b69-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="21b69-127">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="21b69-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
