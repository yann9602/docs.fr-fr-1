---
title: "IMetaDataImport::EnumTypeDefs, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumTypeDefs
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a07d9ff237e6d3838fffb068e3a9ebf9febf66fc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="8c2b5-102">IMetaDataImport::EnumTypeDefs, méthode</span><span class="sxs-lookup"><span data-stu-id="8c2b5-102">IMetaDataImport::EnumTypeDefs Method</span></span>
<span data-ttu-id="8c2b5-103">Énumère les jetons TypeDef représentant tous les types au sein la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="8c2b5-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c2b5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c2b5-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,   
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,   
   [out] ULONG      *pcTypeDefs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8c2b5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8c2b5-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="8c2b5-106">[out] Pointeur vers le nouvel énumérateur.</span><span class="sxs-lookup"><span data-stu-id="8c2b5-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="8c2b5-107">Cela doit être NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="8c2b5-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="8c2b5-108">[in] Tableau utilisé pour stocker les jetons TypeDef.</span><span class="sxs-lookup"><span data-stu-id="8c2b5-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="8c2b5-109">[in] Taille maximale du tableau `rTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="8c2b5-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="8c2b5-110">[out] Le nombre de jetons TypeDef retournés dans `rTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="8c2b5-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c2b5-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8c2b5-111">Return Value</span></span>  
  
|<span data-ttu-id="8c2b5-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8c2b5-112">HRESULT</span></span>|<span data-ttu-id="8c2b5-113">Description</span><span class="sxs-lookup"><span data-stu-id="8c2b5-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="8c2b5-114">`EnumTypeDefs`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="8c2b5-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="8c2b5-115">Il n’existe pas de jetons à énumérer.</span><span class="sxs-lookup"><span data-stu-id="8c2b5-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="8c2b5-116">Dans ce cas, `pcTypeDefs` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="8c2b5-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c2b5-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="8c2b5-117">Remarks</span></span>  
 <span data-ttu-id="8c2b5-118">Le jeton TypeDef représente un type tel qu’une classe ou une interface, ainsi que tout type ajouté via un mécanisme d’extensibilité.</span><span class="sxs-lookup"><span data-stu-id="8c2b5-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c2b5-119">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8c2b5-119">Requirements</span></span>  
 <span data-ttu-id="8c2b5-120">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c2b5-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c2b5-121">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8c2b5-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8c2b5-122">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8c2b5-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8c2b5-123">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c2b5-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c2b5-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c2b5-124">See Also</span></span>  
 [<span data-ttu-id="8c2b5-125">IMetaDataImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="8c2b5-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="8c2b5-126">IMetaDataImport2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="8c2b5-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
