---
title: "IMetaDataAssemblyImport::FindManifestResourceByName, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.FindManifestResourceByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::FindManifestResourceByName
helpviewer_keywords:
- FindManifestResourceByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindManifestResourceByName method [.NET Framework metadata]
ms.assetid: 7b72fa11-3866-402b-bdea-2b966b77cfe0
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 492f8a50c421df56d1b2f79d15d86ef3251b401e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="dc437-102">IMetaDataAssemblyImport::FindManifestResourceByName, méthode</span><span class="sxs-lookup"><span data-stu-id="dc437-102">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>
<span data-ttu-id="dc437-103">Obtient un pointeur vers la ressource de manifeste avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="dc437-103">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc437-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc437-104">Syntax</span></span>  
  
```  
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,   
    [out] mdManifestResource     *ptkManifestResource  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc437-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dc437-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="dc437-106">[in] Le nom de la ressource.</span><span class="sxs-lookup"><span data-stu-id="dc437-106">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="dc437-107">[out] Tableau utilisé pour stocker le `mdManifestResource` des jetons de métadonnées, dont chacun représente une ressource de manifeste.</span><span class="sxs-lookup"><span data-stu-id="dc437-107">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc437-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="dc437-108">Remarks</span></span>  
 <span data-ttu-id="dc437-109">Le `FindManifestResourceByName` méthode utilise les règles standards employées par le common language runtime pour résoudre les références.</span><span class="sxs-lookup"><span data-stu-id="dc437-109">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc437-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="dc437-110">Requirements</span></span>  
 <span data-ttu-id="dc437-111">**Plateforme :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc437-111">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc437-112">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dc437-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dc437-113">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dc437-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dc437-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc437-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc437-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc437-115">See Also</span></span>  
 [<span data-ttu-id="dc437-116">IMetaDataAssemblyImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="dc437-116">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="dc437-117">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="dc437-117">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
