---
title: "IMetaDataImport::GetSigFromToken, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetSigFromToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetSigFromToken
helpviewer_keywords:
- IMetaDataImport::GetSigFromToken method [.NET Framework metadata]
- GetSigFromToken method [.NET Framework metadata]
ms.assetid: ab894dc4-f7b6-4afc-bfcb-582a4b7e53a2
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6328e112aa948ecc2f0f5d816c4fd77673e06244
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetsigfromtoken-method"></a><span data-ttu-id="c5dfa-102">IMetaDataImport::GetSigFromToken, méthode</span><span class="sxs-lookup"><span data-stu-id="c5dfa-102">IMetaDataImport::GetSigFromToken Method</span></span>
<span data-ttu-id="c5dfa-103">Obtient la signature de métadonnées binaires associée au jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="c5dfa-103">Gets the binary metadata signature associated with the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5dfa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5dfa-104">Syntax</span></span>  
  
```  
HRESULT GetSigFromToken (   
   [in]   mdSignature        mdSig,   
   [out]  PCCOR_SIGNATURE    *ppvSig,   
   [out]  ULONG              *pcbSig   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5dfa-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c5dfa-105">Parameters</span></span>  
 `mdSig`  
 <span data-ttu-id="c5dfa-106">[in] Le jeton à retourner de la signature de métadonnées binaires.</span><span class="sxs-lookup"><span data-stu-id="c5dfa-106">[in] The token to return the binary metadata signature for.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="c5dfa-107">[out] Pointeur vers la signature de métadonnées retournée.</span><span class="sxs-lookup"><span data-stu-id="c5dfa-107">[out] A pointer to the returned metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="c5dfa-108">[out] La taille en octets de la signature de métadonnées binaires.</span><span class="sxs-lookup"><span data-stu-id="c5dfa-108">[out] The size in bytes of the binary metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5dfa-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c5dfa-109">Requirements</span></span>  
 <span data-ttu-id="c5dfa-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5dfa-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5dfa-111">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c5dfa-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c5dfa-112">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c5dfa-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c5dfa-113">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5dfa-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5dfa-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5dfa-114">See Also</span></span>  
 [<span data-ttu-id="c5dfa-115">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="c5dfa-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="c5dfa-116">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="c5dfa-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
