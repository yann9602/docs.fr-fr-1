---
title: "IMetaDataEmit::GetTokenFromSig, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.GetTokenFromSig
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::GetTokenFromSig
helpviewer_keywords:
- IMetaDataEmit::GetTokenFromSig method [.NET Framework metadata]
- GetTokenFromSig method [.NET Framework metadata]
ms.assetid: 50a58a83-6287-40a4-b315-47823cea0a5c
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: aefd95f62fce70f87c0724cbb4013462a449c7f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="b46f7-102">IMetaDataEmit::GetTokenFromSig, méthode</span><span class="sxs-lookup"><span data-stu-id="b46f7-102">IMetaDataEmit::GetTokenFromSig Method</span></span>
<span data-ttu-id="b46f7-103">Obtient un jeton pour la signature de métadonnées spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b46f7-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b46f7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b46f7-104">Syntax</span></span>  
  
```  
HRESULT GetTokenFromSig (   
    [in]  PCCOR_SIGNATURE pvSig,   
    [in]  ULONG       cbSig,   
    [out] mdSignature *pmsig   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b46f7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b46f7-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="b46f7-106">[in] La signature à rendre persistante et stockées.</span><span class="sxs-lookup"><span data-stu-id="b46f7-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="b46f7-107">[in] Le nombre d’octets dans `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="b46f7-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="b46f7-108">[out] Le `mdSignature` jeton assigné.</span><span class="sxs-lookup"><span data-stu-id="b46f7-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b46f7-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b46f7-109">Requirements</span></span>  
 <span data-ttu-id="b46f7-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b46f7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b46f7-111">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b46f7-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b46f7-112">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b46f7-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b46f7-113">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b46f7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b46f7-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b46f7-114">See Also</span></span>  
 [<span data-ttu-id="b46f7-115">IMetaDataEmit (Interface)</span><span class="sxs-lookup"><span data-stu-id="b46f7-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="b46f7-116">IMetaDataEmit2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="b46f7-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
