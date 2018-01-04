---
title: "IMetaDataFilter::MarkToken, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataFilter.MarkToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataFilter::MarkToken
helpviewer_keywords:
- IMetaDataFilter::MarkToken method [.NET Framework metadata]
- MarkToken method, IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: bd492834-6529-4d39-b93d-f8cdbd3e297f
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fb40d7674caae119b39f49b0c1024c7500bc892a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatafiltermarktoken-method"></a><span data-ttu-id="661d3-102">IMetaDataFilter::MarkToken, méthode</span><span class="sxs-lookup"><span data-stu-id="661d3-102">IMetaDataFilter::MarkToken Method</span></span>
<span data-ttu-id="661d3-103">Définit une valeur qui indique que le jeton de métadonnées spécifié a été traité.</span><span class="sxs-lookup"><span data-stu-id="661d3-103">Sets a value indicating that the specified metadata token has been processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="661d3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="661d3-104">Syntax</span></span>  
  
```  
HRESULT MarkToken (  
    [in] mdToken   tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="661d3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="661d3-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="661d3-106">[in] Le jeton à marquer comme traité.</span><span class="sxs-lookup"><span data-stu-id="661d3-106">[in] The token to mark as processed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="661d3-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="661d3-107">Requirements</span></span>  
 <span data-ttu-id="661d3-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="661d3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="661d3-109">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="661d3-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="661d3-110">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="661d3-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="661d3-111">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="661d3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="661d3-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="661d3-112">See Also</span></span>  
 [<span data-ttu-id="661d3-113">IMetaDataFilter, interface</span><span class="sxs-lookup"><span data-stu-id="661d3-113">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
