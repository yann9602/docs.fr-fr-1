---
title: "IMetaDataAssemblyEmit::DefineAssembly, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.DefineAssembly
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 35bc85cdc4380ee112b7095866c05e5d7639200b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitdefineassembly-method"></a><span data-ttu-id="aca6a-102">IMetaDataAssemblyEmit::DefineAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="aca6a-102">IMetaDataAssemblyEmit::DefineAssembly Method</span></span>
<span data-ttu-id="aca6a-103">Crée un `Assembly` structure contenant les métadonnées pour l’assembly spécifié et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="aca6a-103">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aca6a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aca6a-104">Syntax</span></span>  
  
```  
HRESULT DefineAssembly (  
    [in]  void                 *pbPublicKey,  
    [in]  ULONG                cbPublicKey,  
    [in]  ULONG                uHashAlgId,  
    [in]  LPCWSTR              szName,   
    [in]  ASSEMBLYMETADATA     *pMetaData,  
    [in]  DWORD                dwAssemblyFlags,  
    [out] mdAssembly           *pmda  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aca6a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="aca6a-105">Parameters</span></span>  
 `pbPublicKey`  
 <span data-ttu-id="aca6a-106">[in] La clé publique qui identifie l’éditeur de l’assembly, ou NULL si l’assembly n'est pas un nom fort.</span><span class="sxs-lookup"><span data-stu-id="aca6a-106">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="aca6a-107">[in] La taille en octets de `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="aca6a-107">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="aca6a-108">[in] Identificateur de l’algorithme de hachage à utiliser pour chiffrer les fichiers dans l’assembly, ou NULL pour spécifier l’algorithme SHA-1.</span><span class="sxs-lookup"><span data-stu-id="aca6a-108">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span></span>  
  
 `szName`  
 <span data-ttu-id="aca6a-109">[in] Nom de l’assembly du texte explicite.</span><span class="sxs-lookup"><span data-stu-id="aca6a-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="aca6a-110">Cette valeur ne doit pas dépasser 1 024 caractères.</span><span class="sxs-lookup"><span data-stu-id="aca6a-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="aca6a-111">[in] Un pointeur vers une instance ASSEMBLYMETADATA qui contient les informations de version, la plateforme et paramètres régionaux de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="aca6a-111">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="aca6a-112">[in] Une combinaison de [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) valeurs qui décrivent les fonctionnalités de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="aca6a-112">[in] A combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that describe features of the assembly.</span></span>  
  
 `pmda`  
 <span data-ttu-id="aca6a-113">[out] Pointeur vers le jeton de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="aca6a-113">[out] A pointer to the metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aca6a-114">Notes</span><span class="sxs-lookup"><span data-stu-id="aca6a-114">Remarks</span></span>  
 <span data-ttu-id="aca6a-115">Seul `Assembly` structure de métadonnées peut être définie dans un manifeste.</span><span class="sxs-lookup"><span data-stu-id="aca6a-115">Only one `Assembly` metadata structure can be defined within a manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aca6a-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="aca6a-116">Requirements</span></span>  
 <span data-ttu-id="aca6a-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aca6a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aca6a-118">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="aca6a-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aca6a-119">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aca6a-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aca6a-120">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aca6a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aca6a-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aca6a-121">See Also</span></span>  
 [<span data-ttu-id="aca6a-122">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="aca6a-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
