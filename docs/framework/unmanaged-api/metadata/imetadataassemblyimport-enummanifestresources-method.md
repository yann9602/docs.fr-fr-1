---
title: "IMetaDataAssemblyImport::EnumManifestResources, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.EnumManifestResources
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::EnumManifestResources
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumManifestResources method [.NET Framework metadata]
- EnumManifestResources method [.NET Framework metadata]
ms.assetid: 9543b111-5705-40c9-935c-a3ffc7a581aa
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 25d8b63e2f40566164274715e562960eafbb83e5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a><span data-ttu-id="56f8c-102">IMetaDataAssemblyImport::EnumManifestResources, méthode</span><span class="sxs-lookup"><span data-stu-id="56f8c-102">IMetaDataAssemblyImport::EnumManifestResources Method</span></span>
<span data-ttu-id="56f8c-103">Obtient un pointeur vers un énumérateur pour les ressources référencées dans le manifeste d’assembly actuel.</span><span class="sxs-lookup"><span data-stu-id="56f8c-103">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56f8c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56f8c-104">Syntax</span></span>  
  
```  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,   
    [out] mdManifestResource   rManifestResources[],   
    [in]  ULONG                cMax,   
    [out] ULONG                *pcTokens  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="56f8c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="56f8c-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="56f8c-106">[dans, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="56f8c-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="56f8c-107">Cela doit être une valeur null lorsque la valeur du `EnumManifestResources` méthode est appelée pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="56f8c-107">This must be a null value when the `EnumManifestResources` method is called for the first time.</span></span>  
  
 `rManifestResources`  
 <span data-ttu-id="56f8c-108">[out] Tableau utilisé pour stocker le `mdManifestResource` des jetons de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="56f8c-108">[out] The array used to store the `mdManifestResource` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="56f8c-109">[in] Le nombre maximal de `mdManifestResource` jetons qui peuvent être placés dans `rManifestResources`.</span><span class="sxs-lookup"><span data-stu-id="56f8c-109">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="56f8c-110">[out] Le nombre de `mdManifestResource` jetons placés dans `rManifestResources`.</span><span class="sxs-lookup"><span data-stu-id="56f8c-110">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56f8c-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="56f8c-111">Return Value</span></span>  
  
|<span data-ttu-id="56f8c-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="56f8c-112">HRESULT</span></span>|<span data-ttu-id="56f8c-113">Description</span><span class="sxs-lookup"><span data-stu-id="56f8c-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="56f8c-114">`EnumManifestResources`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="56f8c-114">`EnumManifestResources` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="56f8c-115">Il n’existe pas de jetons à énumérer.</span><span class="sxs-lookup"><span data-stu-id="56f8c-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="56f8c-116">Dans ce cas, `pcTokens` est définie sur zéro.</span><span class="sxs-lookup"><span data-stu-id="56f8c-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="56f8c-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="56f8c-117">Requirements</span></span>  
 <span data-ttu-id="56f8c-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56f8c-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56f8c-119">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="56f8c-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="56f8c-120">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="56f8c-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="56f8c-121">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56f8c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56f8c-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56f8c-122">See Also</span></span>  
 [<span data-ttu-id="56f8c-123">IMetaDataAssemblyImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="56f8c-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
