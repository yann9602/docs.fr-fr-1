---
title: "IMetaDataImport::EnumMembersWithName, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumMembersWithName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumMembersWithName
helpviewer_keywords:
- IMetaDataImport::EnumMembersWithName method [.NET Framework metadata]
- EnumMembersWithName method [.NET Framework metadata]
ms.assetid: 7c9e9120-3104-42f0-86ce-19a025f20dcc
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 64568fb185cd8a18e43639568ecb67fcfa350dba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenummemberswithname-method"></a><span data-ttu-id="b8f78-102">IMetaDataImport::EnumMembersWithName, méthode</span><span class="sxs-lookup"><span data-stu-id="b8f78-102">IMetaDataImport::EnumMembersWithName Method</span></span>
<span data-ttu-id="b8f78-103">Énumère les jetons MemberDef représentant les membres du type spécifié avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="b8f78-103">Enumerates MemberDef tokens representing members of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8f78-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8f78-104">Syntax</span></span>  
  
```  
HRESULT EnumMembersWithName (  
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   cl,   
   [in]      LPCWSTR     szName,   
   [out]     mdToken     rMembers[],   
   [in]      ULONG       cMax,   
   [out]     ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b8f78-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b8f78-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="b8f78-106">[dans, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="b8f78-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="b8f78-107">[in] Un jeton TypeDef représentant le type avec des membres à énumérer.</span><span class="sxs-lookup"><span data-stu-id="b8f78-107">[in] A TypeDef token representing the type with members to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="b8f78-108">[in] Le nom du membre qui limite la portée de l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="b8f78-108">[in] The member name that limits the scope of the enumerator.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="b8f78-109">[out] Tableau utilisé pour stocker les jetons MemberDef.</span><span class="sxs-lookup"><span data-stu-id="b8f78-109">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b8f78-110">[in] Taille maximale du tableau `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="b8f78-110">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="b8f78-111">[out] Le nombre réel de jetons MemberDef retournés dans `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="b8f78-111">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8f78-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="b8f78-112">Remarks</span></span>  
 <span data-ttu-id="b8f78-113">Cette méthode énumère des champs et méthodes, mais pas propriétés ou des événements.</span><span class="sxs-lookup"><span data-stu-id="b8f78-113">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="b8f78-114">Contrairement aux [IMetaDataImport::EnumMembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md), `EnumMembersWithName` ignore tous les jetons de champ et de membre qui n’ont pas le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="b8f78-114">Unlike [IMetaDataImport::EnumMembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md), `EnumMembersWithName` discards all field and member tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b8f78-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b8f78-115">Return Value</span></span>  
  
|<span data-ttu-id="b8f78-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b8f78-116">HRESULT</span></span>|<span data-ttu-id="b8f78-117">Description</span><span class="sxs-lookup"><span data-stu-id="b8f78-117">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b8f78-118">`EnumTypeDefs`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="b8f78-118">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b8f78-119">Il n’existe pas de jetons MemberDef à énumérer.</span><span class="sxs-lookup"><span data-stu-id="b8f78-119">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="b8f78-120">Dans ce cas, `pcTokens` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="b8f78-120">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b8f78-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b8f78-121">Requirements</span></span>  
 <span data-ttu-id="b8f78-122">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8f78-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8f78-123">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b8f78-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b8f78-124">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b8f78-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b8f78-125">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8f78-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8f78-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8f78-126">See Also</span></span>  
 [<span data-ttu-id="b8f78-127">IMetaDataImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="b8f78-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="b8f78-128">IMetaDataImport2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="b8f78-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
