---
title: "IMetaDataAssemblyEmit::SetFileProps, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.SetFileProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::SetFileProps
helpviewer_keywords:
- IMetaDataAssemblyEmit::SetFileProps method [.NET Framework metadata]
- SetFileProps method [.NET Framework metadata]
ms.assetid: 85667d38-611c-45a9-938d-930ac7a7b681
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f179ce3e54a5229423d7267cd52a97edef3b619d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitsetfileprops-method"></a><span data-ttu-id="ab75d-102">IMetaDataAssemblyEmit::SetFileProps, méthode</span><span class="sxs-lookup"><span data-stu-id="ab75d-102">IMetaDataAssemblyEmit::SetFileProps Method</span></span>
<span data-ttu-id="ab75d-103">Modifie la structure de métadonnées `File` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ab75d-103">Modifies the specified `File` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab75d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab75d-104">Syntax</span></span>  
  
```  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,   
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ab75d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ab75d-105">Parameters</span></span>  
 `file`  
 <span data-ttu-id="ab75d-106">[in] Le jeton de métadonnées qui spécifie le `File` structure de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="ab75d-106">[in] The metadata token that specifies the `File` metadata structure to be modified.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="ab75d-107">[in] Pointeur vers les données de hachage associés au fichier.</span><span class="sxs-lookup"><span data-stu-id="ab75d-107">[in] A pointer to the hash data associated with the file.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="ab75d-108">[in] La taille en octets de `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="ab75d-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="ab75d-109">[in] Une combinaison d’opérations de [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) valeurs qui spécifient plusieurs attributs du fichier.</span><span class="sxs-lookup"><span data-stu-id="ab75d-109">[in] A bitwise combination of [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values that specify various attributes of the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab75d-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="ab75d-110">Remarks</span></span>  
 <span data-ttu-id="ab75d-111">Pour créer un `File` structure des métadonnées, utilisez le [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="ab75d-111">To create a `File` metadata structure, use the [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab75d-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ab75d-112">Requirements</span></span>  
 <span data-ttu-id="ab75d-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab75d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab75d-114">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ab75d-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ab75d-115">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ab75d-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ab75d-116">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab75d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab75d-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab75d-117">See Also</span></span>  
 [<span data-ttu-id="ab75d-118">IMetaDataAssemblyEmit (Interface)</span><span class="sxs-lookup"><span data-stu-id="ab75d-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
