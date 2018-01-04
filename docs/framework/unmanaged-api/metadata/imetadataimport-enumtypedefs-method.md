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
ms.workload: dotnet
ms.openlocfilehash: aeb0e3c2eab4cde219b050bcf0e50202fe2be3f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="825c8-102">IMetaDataImport::EnumTypeDefs, méthode</span><span class="sxs-lookup"><span data-stu-id="825c8-102">IMetaDataImport::EnumTypeDefs Method</span></span>
<span data-ttu-id="825c8-103">Énumère les jetons TypeDef représentant tous les types au sein la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="825c8-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="825c8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="825c8-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,   
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,   
   [out] ULONG      *pcTypeDefs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="825c8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="825c8-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="825c8-106">[out] Pointeur vers le nouvel énumérateur.</span><span class="sxs-lookup"><span data-stu-id="825c8-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="825c8-107">Cela doit être NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="825c8-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="825c8-108">[in] Tableau utilisé pour stocker les jetons TypeDef.</span><span class="sxs-lookup"><span data-stu-id="825c8-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="825c8-109">[in] Taille maximale du tableau `rTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="825c8-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="825c8-110">[out] Le nombre de jetons TypeDef retournés dans `rTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="825c8-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="825c8-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="825c8-111">Return Value</span></span>  
  
|<span data-ttu-id="825c8-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="825c8-112">HRESULT</span></span>|<span data-ttu-id="825c8-113">Description</span><span class="sxs-lookup"><span data-stu-id="825c8-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="825c8-114">`EnumTypeDefs`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="825c8-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="825c8-115">Il n’existe pas de jetons à énumérer.</span><span class="sxs-lookup"><span data-stu-id="825c8-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="825c8-116">Dans ce cas, `pcTypeDefs` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="825c8-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="825c8-117">Notes</span><span class="sxs-lookup"><span data-stu-id="825c8-117">Remarks</span></span>  
 <span data-ttu-id="825c8-118">Le jeton TypeDef représente un type tel qu’une classe ou une interface, ainsi que tout type ajouté via un mécanisme d’extensibilité.</span><span class="sxs-lookup"><span data-stu-id="825c8-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="825c8-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="825c8-119">Requirements</span></span>  
 <span data-ttu-id="825c8-120">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="825c8-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="825c8-121">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="825c8-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="825c8-122">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="825c8-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="825c8-123">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="825c8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="825c8-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="825c8-124">See Also</span></span>  
 [<span data-ttu-id="825c8-125">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="825c8-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="825c8-126">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="825c8-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
