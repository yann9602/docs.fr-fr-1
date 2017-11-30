---
title: "IMetaDataImport::EnumMethodImpls, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumMethodImpls
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumMethodImpls
helpviewer_keywords:
- EnumMethodImpls method [.NET Framework metadata]
- IMetaDataImport::EnumMethodImpls method [.NET Framework metadata]
ms.assetid: 4e0f865d-88b5-44bd-be35-492622e5e08e
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2634642c49c9d95765b6a93048a04ce512b28099
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenummethodimpls-method"></a><span data-ttu-id="a21e7-102">IMetaDataImport::EnumMethodImpls, méthode</span><span class="sxs-lookup"><span data-stu-id="a21e7-102">IMetaDataImport::EnumMethodImpls Method</span></span>
<span data-ttu-id="a21e7-103">Énumère les jetons MethodBody et MethodDeclaration représentant les méthodes du type spécifié.</span><span class="sxs-lookup"><span data-stu-id="a21e7-103">Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a21e7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a21e7-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodImpls (  
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdToken     rMethodBody[],   
   [out]     mdToken     rMethodDecl[],   
   [in]      ULONG       cMax,   
   [in]      ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a21e7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a21e7-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="a21e7-106">[dans, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="a21e7-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="a21e7-107">Cela doit être NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="a21e7-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="a21e7-108">[in] Jeton TypeDef représentant le type dont les implémentations de méthode à énumérer.</span><span class="sxs-lookup"><span data-stu-id="a21e7-108">[in] A TypeDef token for the type whose method implementations to enumerate.</span></span>  
  
 `rMethodBody`  
 <span data-ttu-id="a21e7-109">[out] Le tableau pour stocker les jetons MethodBody.</span><span class="sxs-lookup"><span data-stu-id="a21e7-109">[out] The array to store the MethodBody tokens.</span></span>  
  
 `rMethodDecl`  
 <span data-ttu-id="a21e7-110">[out] Le tableau pour stocker les jetons MethodDeclaration.</span><span class="sxs-lookup"><span data-stu-id="a21e7-110">[out] The array to store the MethodDeclaration tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a21e7-111">[in] La taille maximale de la `rMethodBody` et `rMethodDecl` tableaux.</span><span class="sxs-lookup"><span data-stu-id="a21e7-111">[in] The maximum size of the `rMethodBody` and `rMethodDecl` arrays.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="a21e7-112">[in] Le nombre réel de méthodes retournées dans `rMethodBody` et `rMethodDecl`.</span><span class="sxs-lookup"><span data-stu-id="a21e7-112">[in] The actual number of methods returned in `rMethodBody` and `rMethodDecl`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a21e7-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a21e7-113">Return Value</span></span>  
  
|<span data-ttu-id="a21e7-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a21e7-114">HRESULT</span></span>|<span data-ttu-id="a21e7-115">Description</span><span class="sxs-lookup"><span data-stu-id="a21e7-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a21e7-116">`EnumMethodImpls`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="a21e7-116">`EnumMethodImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a21e7-117">Il n’existe aucun jeton de méthode à énumérer.</span><span class="sxs-lookup"><span data-stu-id="a21e7-117">There are no method tokens to enumerate.</span></span> <span data-ttu-id="a21e7-118">Dans ce cas, `pcTokens` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="a21e7-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a21e7-119">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a21e7-119">Requirements</span></span>  
 <span data-ttu-id="a21e7-120">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a21e7-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a21e7-121">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a21e7-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a21e7-122">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a21e7-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a21e7-123">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a21e7-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a21e7-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a21e7-124">See Also</span></span>  
 [<span data-ttu-id="a21e7-125">IMetaDataImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="a21e7-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="a21e7-126">IMetaDataImport2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="a21e7-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
