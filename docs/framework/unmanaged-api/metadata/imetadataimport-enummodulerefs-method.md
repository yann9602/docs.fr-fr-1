---
title: "IMetaDataImport::EnumModuleRefs, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumModuleRefs
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumModuleRefs
helpviewer_keywords:
- EnumModuleRefs method [.NET Framework metadata]
- IMetaDataImport::EnumModuleRefs method [.NET Framework metadata]
ms.assetid: 53441f3a-68d2-477c-906e-37c55dfcfb4d
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ebba448881b934220f0eb46c392ab0909ae37f68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenummodulerefs-method"></a><span data-ttu-id="7caf3-102">IMetaDataImport::EnumModuleRefs, méthode</span><span class="sxs-lookup"><span data-stu-id="7caf3-102">IMetaDataImport::EnumModuleRefs Method</span></span>
<span data-ttu-id="7caf3-103">Énumère les jetons ModuleRef qui représentent des modules importés.</span><span class="sxs-lookup"><span data-stu-id="7caf3-103">Enumerates ModuleRef tokens that represent imported modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7caf3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7caf3-104">Syntax</span></span>  
  
```  
HRESULT EnumModuleRefs (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdModuleRef  rModuleRefs[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcModuleRefs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7caf3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7caf3-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="7caf3-106">[dans, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="7caf3-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="7caf3-107">Cela doit être NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="7caf3-107">This must be NULL for the first call of this method.</span></span>  
  
 `rModuleRefs`  
 <span data-ttu-id="7caf3-108">[out] Tableau utilisé pour stocker les jetons ModuleRef.</span><span class="sxs-lookup"><span data-stu-id="7caf3-108">[out] The array used to store the ModuleRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="7caf3-109">[in] Taille maximale du tableau `rModuleRefs`.</span><span class="sxs-lookup"><span data-stu-id="7caf3-109">[in] The maximum size of the `rModuleRefs` array.</span></span>  
  
 `pcModuleRefs`  
 <span data-ttu-id="7caf3-110">[out] Le nombre de jetons ModuleRef retournés dans `rModuleRefs`.</span><span class="sxs-lookup"><span data-stu-id="7caf3-110">[out] The number of ModuleRef tokens returned in `rModuleRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7caf3-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7caf3-111">Return Value</span></span>  
  
|<span data-ttu-id="7caf3-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7caf3-112">HRESULT</span></span>|<span data-ttu-id="7caf3-113">Description</span><span class="sxs-lookup"><span data-stu-id="7caf3-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="7caf3-114">`EnumModuleRefs`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="7caf3-114">`EnumModuleRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="7caf3-115">Il n’existe pas de jetons à énumérer.</span><span class="sxs-lookup"><span data-stu-id="7caf3-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="7caf3-116">Dans ce cas, `pcModuleRefs` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="7caf3-116">In that case, `pcModuleRefs` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7caf3-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7caf3-117">Requirements</span></span>  
 <span data-ttu-id="7caf3-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7caf3-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7caf3-119">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7caf3-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7caf3-120">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7caf3-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7caf3-121">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7caf3-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7caf3-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7caf3-122">See Also</span></span>  
 [<span data-ttu-id="7caf3-123">IMetaDataImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="7caf3-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="7caf3-124">IMetaDataImport2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="7caf3-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
