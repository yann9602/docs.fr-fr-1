---
title: "IMetaDataAssemblyImport::GetExportedTypeProps, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.GetExportedTypeProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::GetExportedTypeProps
helpviewer_keywords:
- GetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 25ca7623-5a55-4f09-b44a-36b03d142278
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7fc5bb8266814fc4f1333de78fce4b6af86893c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a><span data-ttu-id="5c8f9-102">IMetaDataAssemblyImport::GetExportedTypeProps, méthode</span><span class="sxs-lookup"><span data-stu-id="5c8f9-102">IMetaDataAssemblyImport::GetExportedTypeProps Method</span></span>
<span data-ttu-id="5c8f9-103">Obtient le jeu de propriétés du type exporté avec la signature de métadonnées spécifiée.</span><span class="sxs-lookup"><span data-stu-id="5c8f9-103">Gets the set of properties of the exported type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c8f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c8f9-104">Syntax</span></span>  
  
```  
HRESULT GetExportedTypeProps (  
    [in]  mdExportedType    mdct,   
    [out] LPWSTR            szName,   
    [in]  ULONG             cchName,   
    [out] ULONG             *pchName,   
    [out] mdToken           *ptkImplementation,   
    [out] mdTypeDef         *ptkTypeDef,   
    [out] DWORD             *pdwExportedTypeFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5c8f9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5c8f9-105">Parameters</span></span>  
 `mdct`  
 <span data-ttu-id="5c8f9-106">[in] Un `mdExportedType` jeton de métadonnées qui représente le type exporté.</span><span class="sxs-lookup"><span data-stu-id="5c8f9-106">[in] An `mdExportedType` metadata token that represents the exported type.</span></span>  
  
 `szName`  
 <span data-ttu-id="5c8f9-107">[out] Le nom du type exporté.</span><span class="sxs-lookup"><span data-stu-id="5c8f9-107">[out] The name of the exported type.</span></span>  
  
 `cchName`  
 <span data-ttu-id="5c8f9-108">[in] La taille, en caractères larges, de `szName`.</span><span class="sxs-lookup"><span data-stu-id="5c8f9-108">[in] The size, in wide characters, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="5c8f9-109">[out] Le nombre de caractères étendus réellement retournés dans`szName`</span><span class="sxs-lookup"><span data-stu-id="5c8f9-109">[out] The number of wide characters actually returned in `szName`</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="5c8f9-110">[out] Un `mdFile`, `mdAssemblyRef`, ou `mdExportedType` jeton de métadonnées qui contienne ou autorise l’accès aux propriétés du type exporté.</span><span class="sxs-lookup"><span data-stu-id="5c8f9-110">[out] An `mdFile`, `mdAssemblyRef`, or `mdExportedType` metadata token that contains or allows access to the properties of the exported type.</span></span>  
  
 `ptkTypeDef`  
 <span data-ttu-id="5c8f9-111">[out] Un pointeur vers un `mdTypeDef` jeton qui représente un type dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="5c8f9-111">[out] A pointer to an `mdTypeDef` token that represents a type in the file.</span></span>  
  
 `pdwExportedTypeFlags`  
 <span data-ttu-id="5c8f9-112">[out] Pointeur vers les indicateurs qui décrivent les métadonnées appliquées au type exporté.</span><span class="sxs-lookup"><span data-stu-id="5c8f9-112">[out] A pointer to the flags that describe the metadata applied to the exported type.</span></span> <span data-ttu-id="5c8f9-113">La valeur des indicateurs peut être une ou plusieurs [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) valeurs.</span><span class="sxs-lookup"><span data-stu-id="5c8f9-113">The flags value can be one or more [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c8f9-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5c8f9-114">Requirements</span></span>  
 <span data-ttu-id="5c8f9-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c8f9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c8f9-116">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5c8f9-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5c8f9-117">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5c8f9-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5c8f9-118">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c8f9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c8f9-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c8f9-119">See Also</span></span>  
 [<span data-ttu-id="5c8f9-120">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="5c8f9-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
