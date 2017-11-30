---
title: "IMetaDataEmit::GetTokenFromTypeSpec, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.GetTokenFromTypeSpec
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::GetTokenFromTypeSpec
helpviewer_keywords:
- GetTokenFromTypeSpec method [.NET Framework metadata]
- IMetaDataEmit::GetTokenFromTypeSpec method [.NET Framework metadata]
ms.assetid: 7de6447a-a751-49d8-87e2-951cee77b536
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8f83d1adb37691b525927eeb8a87b620fa3c7353
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitgettokenfromtypespec-method"></a><span data-ttu-id="254be-102">IMetaDataEmit::GetTokenFromTypeSpec, méthode</span><span class="sxs-lookup"><span data-stu-id="254be-102">IMetaDataEmit::GetTokenFromTypeSpec Method</span></span>
<span data-ttu-id="254be-103">Obtient les métadonnées jeton pour le type avec la signature de métadonnées spécifiée.</span><span class="sxs-lookup"><span data-stu-id="254be-103">Gets a metadata token for the type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="254be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="254be-104">Syntax</span></span>  
  
```  
HRESULT GetTokenFromTypeSpec (   
    [in]  PCCOR_SIGNATURE       pvSig,   
    [in]  ULONG                 cbSig,   
    [out] mdTypeSpec            *ptypespec   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="254be-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="254be-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="254be-106">[in] La signature est définie.</span><span class="sxs-lookup"><span data-stu-id="254be-106">[in] The signature being defined.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="254be-107">[in] Le nombre d’octets dans `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="254be-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `ptypespec`  
 <span data-ttu-id="254be-108">[out] Le `mdTypeSpec` jeton assigné.</span><span class="sxs-lookup"><span data-stu-id="254be-108">[out] The `mdTypeSpec` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="254be-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="254be-109">Requirements</span></span>  
 <span data-ttu-id="254be-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="254be-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="254be-111">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="254be-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="254be-112">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="254be-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="254be-113">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="254be-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="254be-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="254be-114">See Also</span></span>  
 [<span data-ttu-id="254be-115">IMetaDataEmit (Interface)</span><span class="sxs-lookup"><span data-stu-id="254be-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="254be-116">IMetaDataEmit2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="254be-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
