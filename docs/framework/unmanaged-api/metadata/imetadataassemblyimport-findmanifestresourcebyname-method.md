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
ms.workload: dotnet
ms.openlocfilehash: 2d6cc738c227157b45e242fb46a672d28d6ce778
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="a0a56-102">IMetaDataAssemblyImport::FindManifestResourceByName, méthode</span><span class="sxs-lookup"><span data-stu-id="a0a56-102">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>
<span data-ttu-id="a0a56-103">Obtient un pointeur vers la ressource de manifeste avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="a0a56-103">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0a56-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0a56-104">Syntax</span></span>  
  
```  
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,   
    [out] mdManifestResource     *ptkManifestResource  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0a56-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a0a56-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="a0a56-106">[in] Le nom de la ressource.</span><span class="sxs-lookup"><span data-stu-id="a0a56-106">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="a0a56-107">[out] Tableau utilisé pour stocker le `mdManifestResource` des jetons de métadonnées, dont chacun représente une ressource de manifeste.</span><span class="sxs-lookup"><span data-stu-id="a0a56-107">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0a56-108">Notes</span><span class="sxs-lookup"><span data-stu-id="a0a56-108">Remarks</span></span>  
 <span data-ttu-id="a0a56-109">Le `FindManifestResourceByName` méthode utilise les règles standards employées par le common language runtime pour résoudre les références.</span><span class="sxs-lookup"><span data-stu-id="a0a56-109">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0a56-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a0a56-110">Requirements</span></span>  
 <span data-ttu-id="a0a56-111">**Plateforme :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0a56-111">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0a56-112">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a0a56-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a0a56-113">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a0a56-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a0a56-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0a56-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0a56-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0a56-115">See Also</span></span>  
 [<span data-ttu-id="a0a56-116">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="a0a56-116">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="a0a56-117">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="a0a56-117">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
