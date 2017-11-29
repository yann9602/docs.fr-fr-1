---
title: "IMetaDataEmit2::DefineMethodSpec, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2.DefineMethodSpec
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2::DefineMethodSpec
helpviewer_keywords:
- DefineMethodSpec method [.NET Framework metadata]
- IMetaDataEmit2::DefineMethodSpec method [.NET Framework metadata]
ms.assetid: 3c24e552-fc69-4971-b65a-a3e4b5f7f1e8
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 036654c733dc73d40c526bf5cad4dd3750e2e9d6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemit2definemethodspec-method"></a><span data-ttu-id="1b6a7-102">IMetaDataEmit2::DefineMethodSpec, méthode</span><span class="sxs-lookup"><span data-stu-id="1b6a7-102">IMetaDataEmit2::DefineMethodSpec Method</span></span>
<span data-ttu-id="1b6a7-103">Crée une instance générique d’une méthode et obtient un jeton pour la définition.</span><span class="sxs-lookup"><span data-stu-id="1b6a7-103">Creates a generic instance of a method, and gets a token to the definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b6a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b6a7-104">Syntax</span></span>  
  
```  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [out] mdMethodSpec      *pmi  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1b6a7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1b6a7-105">Parameters</span></span>  
 `tkParent`  
 <span data-ttu-id="1b6a7-106">[in] Un jeton pour la méthode de laquelle créer l’instance générique.</span><span class="sxs-lookup"><span data-stu-id="1b6a7-106">[in] A token for the method of which to create the generic instance.</span></span> <span data-ttu-id="1b6a7-107">Le jeton doit être de type `mdMethodDef` ou `mdMemberRef`.</span><span class="sxs-lookup"><span data-stu-id="1b6a7-107">The token must be of type `mdMethodDef` or `mdMemberRef`.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="1b6a7-108">[in] Pointeur vers la signature COM + binaire de la méthode.</span><span class="sxs-lookup"><span data-stu-id="1b6a7-108">[in] A pointer to the binary COM+ signature of the method.</span></span>  
  
 `cbSibBlob`  
 <span data-ttu-id="1b6a7-109">[in] La taille, en octets, de `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="1b6a7-109">[in] The size, in bytes, of `pvSigBlob`.</span></span>  
  
 `pmi`  
 <span data-ttu-id="1b6a7-110">[out] Jeton servant à la définition de signature de métadonnées de la méthode.</span><span class="sxs-lookup"><span data-stu-id="1b6a7-110">[out] A token to the metadata signature definition of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b6a7-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1b6a7-111">Requirements</span></span>  
 <span data-ttu-id="1b6a7-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b6a7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b6a7-113">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1b6a7-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1b6a7-114">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1b6a7-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1b6a7-115">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b6a7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b6a7-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b6a7-116">See Also</span></span>  
 [<span data-ttu-id="1b6a7-117">IMetaDataEmit2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="1b6a7-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="1b6a7-118">IMetaDataEmit (Interface)</span><span class="sxs-lookup"><span data-stu-id="1b6a7-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
