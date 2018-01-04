---
title: "IMetaDataAssemblyEmit::SetAssemblyRefProps, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.SetAssemblyRefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::SetAssemblyRefProps
helpviewer_keywords:
- SetAssemblyRefProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 70a32bf3-9051-4f96-ae87-11356d06a073
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 446137d28fdd64d7f9e5c84cc57e9ec967982430
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a><span data-ttu-id="8c914-102">IMetaDataAssemblyEmit::SetAssemblyRefProps, méthode</span><span class="sxs-lookup"><span data-stu-id="8c914-102">IMetaDataAssemblyEmit::SetAssemblyRefProps Method</span></span>
<span data-ttu-id="8c914-103">Modifie la structure de métadonnées `AssemblyRef` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8c914-103">Modifies the specified `AssemblyRef` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c914-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c914-104">Syntax</span></span>  
  
```  
HRESULT SetAssemblyRefProps (  
    [in] mdAssemblyRef              ar,  
    [in] const void                 *pbPublicKeyOrToken,  
    [in] ULONG                      cbPublicKeyOrToken,  
    [in] LPCWSTR                    szName,   
    [in] const ASSEMBLYMETADATA     *pMetaData,   
    [in] const void                 *pbHashValue,  
    [in] ULONG                      cbHashValue,  
    [in] DWORD                      dwAssemblyRefFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8c914-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8c914-105">Parameters</span></span>  
 `ar`  
 <span data-ttu-id="8c914-106">[in] Le jeton de métadonnées qui spécifie le `AssemblyRef` structure de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="8c914-106">[in] The metadata token that specifies the `AssemblyRef` metadata structure to be modified.</span></span>  
  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="8c914-107">[in] La clé publique de l’éditeur de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="8c914-107">[in] The public key of the publisher of the referenced assembly.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="8c914-108">[in] La taille en octets de `pbPublicKeyOrToken`.</span><span class="sxs-lookup"><span data-stu-id="8c914-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="8c914-109">[in] Nom de l’assembly du texte explicite.</span><span class="sxs-lookup"><span data-stu-id="8c914-109">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="8c914-110">[in] Un pointeur vers une instance ASSEMBLYMETADATA qui contient les informations de version, la plateforme et paramètres régionaux de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="8c914-110">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="8c914-111">[in] Pointeur vers les données de hachage associées à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="8c914-111">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="8c914-112">[in] La taille en octets de `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="8c914-112">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="8c914-113">[in] Une combinaison d’opérations de [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) valeurs qui spécifient les attributs de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="8c914-113">[in] A bitwise combination of [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) values that specify attributes of the referenced assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c914-114">Notes</span><span class="sxs-lookup"><span data-stu-id="8c914-114">Remarks</span></span>  
 <span data-ttu-id="8c914-115">Pour créer un `AssemblyRef` structure des métadonnées, utilisez le [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="8c914-115">To create an `AssemblyRef` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c914-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8c914-116">Requirements</span></span>  
 <span data-ttu-id="8c914-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c914-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c914-118">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8c914-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8c914-119">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8c914-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8c914-120">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c914-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c914-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c914-121">See Also</span></span>  
 [<span data-ttu-id="8c914-122">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="8c914-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
