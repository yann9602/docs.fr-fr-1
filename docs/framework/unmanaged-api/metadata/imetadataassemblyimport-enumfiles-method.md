---
title: "IMetaDataAssemblyImport::EnumFiles, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.EnumFiles
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::EnumFiles
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumFiles method [.NET Framework metadata]
- EnumFiles method [.NET Framework metadata]
ms.assetid: f0d721e2-b946-426d-8e20-9124bd04e4cb
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5ce0682f6f7719c902183778578d75dd19d56867
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="34baa-102">IMetaDataAssemblyImport::EnumFiles, méthode</span><span class="sxs-lookup"><span data-stu-id="34baa-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>
<span data-ttu-id="34baa-103">Énumère les fichiers référencés dans le manifeste d’assembly actuel.</span><span class="sxs-lookup"><span data-stu-id="34baa-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34baa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34baa-104">Syntax</span></span>  
  
```  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,   
    [out] mdFile          rFiles[],   
    [in]  ULONG           cMax,   
    [out] ULONG           *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="34baa-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="34baa-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="34baa-106">[dans, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="34baa-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="34baa-107">Cela doit être une valeur null pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="34baa-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="34baa-108">[out] Tableau utilisé pour stocker le `mdFile` des jetons de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="34baa-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="34baa-109">[in] Le nombre maximal de `mdFile` jetons qui peuvent être placés dans `rFiles`.</span><span class="sxs-lookup"><span data-stu-id="34baa-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="34baa-110">[out] Le nombre de `mdFile` jetons placés dans `rFiles`.</span><span class="sxs-lookup"><span data-stu-id="34baa-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34baa-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="34baa-111">Return Value</span></span>  
  
|<span data-ttu-id="34baa-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="34baa-112">HRESULT</span></span>|<span data-ttu-id="34baa-113">Description</span><span class="sxs-lookup"><span data-stu-id="34baa-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="34baa-114">`EnumFiles`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="34baa-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="34baa-115">Il n’existe pas de jetons à énumérer.</span><span class="sxs-lookup"><span data-stu-id="34baa-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="34baa-116">Dans ce cas, `pcTokens` est définie sur zéro.</span><span class="sxs-lookup"><span data-stu-id="34baa-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="34baa-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="34baa-117">Requirements</span></span>  
 <span data-ttu-id="34baa-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34baa-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34baa-119">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="34baa-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="34baa-120">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="34baa-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="34baa-121">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34baa-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34baa-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34baa-122">See Also</span></span>  
 [<span data-ttu-id="34baa-123">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="34baa-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
