---
title: "IMetaDataEmit::TranslateSigWithScope, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.TranslateSigWithScope
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::TranslateSigWithScope
helpviewer_keywords:
- TranslateSigWithScope method [.NET Framework metadata]
- IMetaDataEmit::TranslateSigWithScope method [.NET Framework metadata]
ms.assetid: 47915d33-b7bf-409e-b484-4ee1df15de22
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5127defc97423283b52b7b5bd8c6b7a31104fbc2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemittranslatesigwithscope-method"></a><span data-ttu-id="6f983-102">IMetaDataEmit::TranslateSigWithScope, méthode</span><span class="sxs-lookup"><span data-stu-id="6f983-102">IMetaDataEmit::TranslateSigWithScope Method</span></span>
<span data-ttu-id="6f983-103">Importe un assembly dans la portée actuelle et obtient une nouvelle signature de métadonnées pour la portée fusionnée.</span><span class="sxs-lookup"><span data-stu-id="6f983-103">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f983-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f983-104">Syntax</span></span>  
  
```  
HRESULT TranslateSigWithScope (   
    [in]  IMetaDataAssemblyImport   *pAssemImport,   
    [in]  const void                *pbHashValue,   
    [in]  ULONG                     cbHashValue,   
    [in]  IMetaDataImport           *import,   
    [in]  PCCOR_SIGNATURE           pbSigBlob,   
    [in]  ULONG                     cbSigBlob,  
    [in]  IMetaDataAssemblyEmit     *pAssemEmit,   
    [in]  IMetaDataEmit             *emit,   
    [out] PCOR_SIGNATURE            pvTranslatedSig,   
    [in]  ULONG                     cbTranslatedSigMax,   
    [out] ULONG                     *pcbTranslatedSig   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f983-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6f983-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="6f983-106">[in] L’interface pour importer l’assembly (où la signature est définie).</span><span class="sxs-lookup"><span data-stu-id="6f983-106">[in] The interface for import assembly (where the signature is defined).</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="6f983-107">[in] L’objet blob de hachage pour l’assembly.</span><span class="sxs-lookup"><span data-stu-id="6f983-107">[in] The hash blob for the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="6f983-108">[in] Le nombre d’octets dans `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="6f983-108">[in] The count of bytes in `pbHashValue`.</span></span>  
  
 `import`  
 <span data-ttu-id="6f983-109">[in] L’interface pour la portée d’importation de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="6f983-109">[in] The interface for import metadata scope.</span></span>  
  
 `pbSigBlob`  
 <span data-ttu-id="6f983-110">[in] La signature à importer.</span><span class="sxs-lookup"><span data-stu-id="6f983-110">[in] The signature to be imported.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="6f983-111">[in] La taille, en octets, de `pbSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="6f983-111">[in] The size, in bytes, of `pbSigBlob`.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="6f983-112">[in] L’interface pour exporter l’assembly.</span><span class="sxs-lookup"><span data-stu-id="6f983-112">[in] The interface for export assembly.</span></span>  
  
 `emit`  
 <span data-ttu-id="6f983-113">[in] L’interface pour la portée de métadonnées d’exportation.</span><span class="sxs-lookup"><span data-stu-id="6f983-113">[in] The interface for export metadata scope.</span></span>  
  
 `pvTranslatedSig`  
 <span data-ttu-id="6f983-114">[out] La mémoire tampon pour stocker l’objet blob de signature traduite.</span><span class="sxs-lookup"><span data-stu-id="6f983-114">[out] The buffer to hold the translated signature blob.</span></span>  
  
 `cbTranslatedSigMax`  
 <span data-ttu-id="6f983-115">[in] La capacité, en octets, de `pvTranslatedSig`.</span><span class="sxs-lookup"><span data-stu-id="6f983-115">[in] The capacity, in bytes, of `pvTranslatedSig`.</span></span>  
  
 `pcbTranslatedSig`  
 <span data-ttu-id="6f983-116">[out] Le nombre d’octets réels dans la signature traduite.</span><span class="sxs-lookup"><span data-stu-id="6f983-116">[out] The number of actual bytes in the translated signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f983-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6f983-117">Requirements</span></span>  
 <span data-ttu-id="6f983-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f983-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f983-119">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6f983-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6f983-120">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6f983-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6f983-121">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f983-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f983-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f983-122">See Also</span></span>  
 [<span data-ttu-id="6f983-123">IMetaDataAssemblyEmit (Interface)</span><span class="sxs-lookup"><span data-stu-id="6f983-123">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="6f983-124">IMetaDataAssemblyImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="6f983-124">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="6f983-125">IMetaDataEmit (Interface)</span><span class="sxs-lookup"><span data-stu-id="6f983-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="6f983-126">IMetaDataEmit2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="6f983-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="6f983-127">IMetaDataImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="6f983-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
