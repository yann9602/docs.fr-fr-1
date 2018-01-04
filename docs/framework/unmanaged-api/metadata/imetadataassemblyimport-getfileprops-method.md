---
title: "IMetaDataAssemblyImport::GetFileProps, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.GetFileProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::GetFileProps
helpviewer_keywords:
- GetFileProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetFileProps method [.NET Framework metadata]
ms.assetid: c5e6216f-ae3d-4697-9688-66b69c1251ec
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 55984c4adaf291e3b962514cdc3bea964d1c91bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportgetfileprops-method"></a><span data-ttu-id="5e751-102">IMetaDataAssemblyImport::GetFileProps, méthode</span><span class="sxs-lookup"><span data-stu-id="5e751-102">IMetaDataAssemblyImport::GetFileProps Method</span></span>
<span data-ttu-id="5e751-103">Obtient les propriétés du fichier avec la signature de métadonnées spécifiée.</span><span class="sxs-lookup"><span data-stu-id="5e751-103">Gets the properties of the file with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e751-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e751-104">Syntax</span></span>  
  
```  
HRESULT GetFileProps (  
    [in]  mdFile      mdf,   
    [out] LPWSTR      szName,   
    [in]  ULONG       cchName,   
    [out] ULONG       *pchName,   
    [out] const void  **ppbHashValue,   
    [out] ULONG       *pcbHashValue,   
    [out] DWORD       *pdwFileFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5e751-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5e751-105">Parameters</span></span>  
 `mdf`  
 <span data-ttu-id="5e751-106">[in] Le `mdFile` jeton de métadonnées qui représente le fichier pour lequel obtenir les propriétés.</span><span class="sxs-lookup"><span data-stu-id="5e751-106">[in] The `mdFile` metadata token that represents the file for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="5e751-107">[out] Le nom simple du fichier.</span><span class="sxs-lookup"><span data-stu-id="5e751-107">[out] The simple name of the file.</span></span>  
  
 `cchName`  
 <span data-ttu-id="5e751-108">[in] La taille, en caractères étendus de `szName`.</span><span class="sxs-lookup"><span data-stu-id="5e751-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="5e751-109">[out] Le nombre de caractères étendus réellement retournés dans `szName`.</span><span class="sxs-lookup"><span data-stu-id="5e751-109">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="5e751-110">[out] Pointeur vers la valeur de hachage.</span><span class="sxs-lookup"><span data-stu-id="5e751-110">[out] A pointer to the hash value.</span></span> <span data-ttu-id="5e751-111">Il s’agit du hachage, à l’aide de l’algorithme SHA-1, du fichier.</span><span class="sxs-lookup"><span data-stu-id="5e751-111">This is the hash, using the SHA-1 algorithm, of the file.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="5e751-112">[out] Le nombre de caractères étendus dans la valeur de hachage retournée.</span><span class="sxs-lookup"><span data-stu-id="5e751-112">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwFileFlags`  
 <span data-ttu-id="5e751-113">[out] Pointeur vers les indicateurs qui décrivent les métadonnées appliquées à un fichier.</span><span class="sxs-lookup"><span data-stu-id="5e751-113">[out] A pointer to the flags that describe the metadata applied to a file.</span></span> <span data-ttu-id="5e751-114">La valeur des indicateurs est une combinaison d’une ou plusieurs [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) valeurs.</span><span class="sxs-lookup"><span data-stu-id="5e751-114">The flags value is a combination of one or more [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e751-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5e751-115">Requirements</span></span>  
 <span data-ttu-id="5e751-116">**Plateforme :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e751-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e751-117">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5e751-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5e751-118">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5e751-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5e751-119">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e751-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e751-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e751-120">See Also</span></span>  
 [<span data-ttu-id="5e751-121">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="5e751-121">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
