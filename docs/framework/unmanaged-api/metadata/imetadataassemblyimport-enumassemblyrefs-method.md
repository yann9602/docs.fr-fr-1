---
title: "IMetaDataAssemblyImport::EnumAssemblyRefs, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.EnumAssemblyRefs
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::EnumAssemblyRefs
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs method [.NET Framework metadata]
- EnumAssemblyRefs method [.NET Framework metadata]
ms.assetid: 8844d0dd-730e-4592-8a7b-c1462d312c70
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 24a289ed42a99cd26c7829d9a5789ac3027026c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="ade32-102">IMetaDataAssemblyImport::EnumAssemblyRefs, méthode</span><span class="sxs-lookup"><span data-stu-id="ade32-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>
<span data-ttu-id="ade32-103">Énumère les `mdAssemblyRef` instances définies dans le manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="ade32-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ade32-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ade32-104">Syntax</span></span>  
  
```  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,   
    [out]     mdAssemblyRef   rAssemblyRefs[],   
    [in]      ULONG           cMax,   
    [out]     ULONG           *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ade32-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ade32-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="ade32-106">[dans, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="ade32-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="ade32-107">Cela doit être une valeur null lorsque la valeur du `EnumAssemblyRefs` méthode est appelée pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="ade32-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="ade32-108">[out] L’énumération des `mdAssemblyRef` des jetons de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="ade32-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ade32-109">[in] Le nombre maximal de jetons qui peuvent être placées dans le `rAssemblyRefs` tableau.</span><span class="sxs-lookup"><span data-stu-id="ade32-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="ade32-110">[out] Le nombre de jetons placés dans `rAssemblyRefs`.</span><span class="sxs-lookup"><span data-stu-id="ade32-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ade32-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ade32-111">Return Value</span></span>  
  
|<span data-ttu-id="ade32-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ade32-112">HRESULT</span></span>|<span data-ttu-id="ade32-113">Description</span><span class="sxs-lookup"><span data-stu-id="ade32-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="ade32-114">`EnumAssemblyRefs`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="ade32-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="ade32-115">Il n’existe pas de jetons à énumérer.</span><span class="sxs-lookup"><span data-stu-id="ade32-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="ade32-116">Dans ce cas, `pcTokens` est définie sur zéro.</span><span class="sxs-lookup"><span data-stu-id="ade32-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ade32-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ade32-117">Requirements</span></span>  
 <span data-ttu-id="ade32-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ade32-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ade32-119">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ade32-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ade32-120">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ade32-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ade32-121">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ade32-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ade32-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ade32-122">See Also</span></span>  
 [<span data-ttu-id="ade32-123">IMetaDataAssemblyImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="ade32-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
