---
title: "IMetaDataAssemblyEmit::DefineAssemblyRef, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.DefineAssemblyRef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::DefineAssemblyRef
helpviewer_keywords:
- DefineAssemblyRef method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineAssemblyRef method [.NET Framework metadata]
ms.assetid: 0b284b18-0084-4b3a-912a-5ebe9f29c88b
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 074e589b84e21de4ec3bcc3c54a865297587d383
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a><span data-ttu-id="4527d-102">IMetaDataAssemblyEmit::DefineAssemblyRef, méthode</span><span class="sxs-lookup"><span data-stu-id="4527d-102">IMetaDataAssemblyEmit::DefineAssemblyRef Method</span></span>
<span data-ttu-id="4527d-103">Crée une structure `AssemblyRef` contenant les métadonnées pour l'assembly que cet assembly référence et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="4527d-103">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4527d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4527d-104">Syntax</span></span>  
  
```  
HRESULT DefineAssemblyRef (  
    [in]  void                *pbPublicKeyOrToken,  
    [in]  ULONG               cbPublicKeyOrToken,  
    [in]  LPCWSTR             szName,  
    [in]  ASSEMBLYMETADATA    pMetaData,  
    [in]  void                *pbHashValue,  
    [in]  ULONG               cbHashValue,  
    [in]  DWORD               dwAssemblyRefFlags,  
    [out] mdAssemblyRef       *pmdar  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4527d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4527d-105">Parameters</span></span>  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="4527d-106">[in] La clé publique de l’éditeur de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="4527d-106">[in] The public key of the publisher of the referenced assembly.</span></span> <span data-ttu-id="4527d-107">La fonction d’assistance [StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) peut être utilisé pour obtenir le hachage de la clé publique à passer comme ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="4527d-107">The helper function [StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) can be used to get the hash of the public key to pass as this parameter.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="4527d-108">[in] La taille en octets de `pbPublicKeyOrToken`.</span><span class="sxs-lookup"><span data-stu-id="4527d-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="4527d-109">[in] Nom de l’assembly du texte explicite.</span><span class="sxs-lookup"><span data-stu-id="4527d-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="4527d-110">Cette valeur ne doit pas dépasser 1 024 caractères.</span><span class="sxs-lookup"><span data-stu-id="4527d-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="4527d-111">[in] Instance ASSEMBLYMETADATA qui contient les informations de version, la plate-forme et paramètres régionaux de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="4527d-111">[in] An ASSEMBLYMETADATA instance that contains the version, platform and locale information of the referenced assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="4527d-112">[in] Les données de hachage associées à l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="4527d-112">[in] The hash data associated with the referenced assembly.</span></span> <span data-ttu-id="4527d-113">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="4527d-113">Optional.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="4527d-114">[in] La taille en octets de `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="4527d-114">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="4527d-115">[in] Une combinaison d’opérations de [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) valeurs qui influencent le comportement du moteur d’exécution.</span><span class="sxs-lookup"><span data-stu-id="4527d-115">[in] A bitwise combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that influence the behavior of the execution engine.</span></span>  
  
 `pmdar`  
 <span data-ttu-id="4527d-116">[out] Un pointeur vers retourné `AssemblyRef` jeton de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="4527d-116">[out] A pointer to the returned `AssemblyRef` metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4527d-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="4527d-117">Remarks</span></span>  
 <span data-ttu-id="4527d-118">Un `AssemblyRef` structure de métadonnées doit être définie pour chaque assembly que cet assembly référence.</span><span class="sxs-lookup"><span data-stu-id="4527d-118">One `AssemblyRef` metadata structure must be defined for each assembly that this assembly references.</span></span>  
  
 <span data-ttu-id="4527d-119">Au moment de l’exécution, les détails d’un assembly référencé sont passés à la résolution d’assembly avec une indication qu’ils représentent les informations « comme généré ».</span><span class="sxs-lookup"><span data-stu-id="4527d-119">At run time, the details of a referenced assembly are passed to the assembly resolver with an indication that they represent the "as built" information.</span></span> <span data-ttu-id="4527d-120">Le programme de résolution d’assembly applique ensuite la stratégie.</span><span class="sxs-lookup"><span data-stu-id="4527d-120">The assembly resolver then applies policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4527d-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4527d-121">Requirements</span></span>  
 <span data-ttu-id="4527d-122">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4527d-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4527d-123">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4527d-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4527d-124">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4527d-124">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4527d-125">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4527d-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4527d-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4527d-126">See Also</span></span>  
 [<span data-ttu-id="4527d-127">IMetaDataAssemblyEmit (Interface)</span><span class="sxs-lookup"><span data-stu-id="4527d-127">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
