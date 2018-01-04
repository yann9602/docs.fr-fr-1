---
title: "IMetaDataAssemblyImport::GetAssemblyProps, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.GetAssemblyProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::GetAssemblyProps
helpviewer_keywords:
- GetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetAssemblyProps method [.NET Framework metadata]
ms.assetid: 0eaa4aa9-9441-444a-920c-e4b2a2db899e
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e99474fea329f53286d698d0e1a302909d5cc65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="58ca5-102">IMetaDataAssemblyImport::GetAssemblyProps, méthode</span><span class="sxs-lookup"><span data-stu-id="58ca5-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>
<span data-ttu-id="58ca5-103">Obtient le jeu de propriétés de l’assembly avec la signature de métadonnées spécifiée.</span><span class="sxs-lookup"><span data-stu-id="58ca5-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58ca5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58ca5-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyProps (  
    [in]  mdAssembly          mda,  
    [out] const void          **ppbPublicKey,   
    [out] ULONG               *pcbPublicKey,  
    [out] ULONG               *pulHashAlgId,  
    [out] LPWSTR              szName,  
    [in] ULONG                cchName,  
    [out] ULONG               *pchName,  
    [out] ASSEMBLYMETADATA    *pMetaData,  
    [out] DWORD               *pdwAssemblyFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="58ca5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="58ca5-105">Parameters</span></span>  
 `mda`  
 <span data-ttu-id="58ca5-106">[in].</span><span class="sxs-lookup"><span data-stu-id="58ca5-106">[in].</span></span> <span data-ttu-id="58ca5-107">Le `mdAssembly` jeton de métadonnées qui représente l’assembly pour lequel obtenir les propriétés.</span><span class="sxs-lookup"><span data-stu-id="58ca5-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="58ca5-108">[out] Pointeur vers la clé publique ou le jeton de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="58ca5-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="58ca5-109">[out] Le nombre d’octets dans la clé publique retournée.</span><span class="sxs-lookup"><span data-stu-id="58ca5-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="58ca5-110">[out] Pointeur vers l’algorithme utilisé pour hacher les fichiers dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="58ca5-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="58ca5-111">[out] Le nom simple de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="58ca5-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="58ca5-112">[in] La taille, en caractères étendus de `szName`.</span><span class="sxs-lookup"><span data-stu-id="58ca5-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="58ca5-113">[out] Le nombre de caractères étendus réellement retournés dans `szName`.</span><span class="sxs-lookup"><span data-stu-id="58ca5-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="58ca5-114">[out] Pointeur vers une structure ASSEMBLYMETADATA qui contient les métadonnées de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="58ca5-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="58ca5-115">[out] Indicateurs qui décrivent les métadonnées appliquées à un assembly.</span><span class="sxs-lookup"><span data-stu-id="58ca5-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="58ca5-116">Cette valeur est une combinaison d’une ou plusieurs [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) valeurs.</span><span class="sxs-lookup"><span data-stu-id="58ca5-116">This value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58ca5-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="58ca5-117">Requirements</span></span>  
 <span data-ttu-id="58ca5-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58ca5-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58ca5-119">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="58ca5-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="58ca5-120">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="58ca5-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="58ca5-121">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58ca5-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58ca5-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58ca5-122">See Also</span></span>  
 [<span data-ttu-id="58ca5-123">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="58ca5-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
