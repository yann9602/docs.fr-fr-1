---
title: "IHostFilter::MarkToken, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostFilter.MarkToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostFilter::MarkToken
helpviewer_keywords:
- MarkToken method, IHostFilter interface [.NET Framework metadata]
- IHostFilter::MarkToken method [.NET Framework metadata]
ms.assetid: d7061343-d0a3-4fd5-b312-61974f98bd62
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ca342e04f554d070546c6c6d82d5ad56a4dad8cf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostfiltermarktoken-method"></a><span data-ttu-id="ad1ab-102">IHostFilter::MarkToken, méthode</span><span class="sxs-lookup"><span data-stu-id="ad1ab-102">IHostFilter::MarkToken Method</span></span>
<span data-ttu-id="ad1ab-103">Indique que le jeton de métadonnées spécifié sera traité.</span><span class="sxs-lookup"><span data-stu-id="ad1ab-103">Indicates that the specified metadata token will be processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad1ab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad1ab-104">Syntax</span></span>  
  
```  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad1ab-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ad1ab-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="ad1ab-106">[in] Le jeton de métadonnées à traiter.</span><span class="sxs-lookup"><span data-stu-id="ad1ab-106">[in] The metadata token to be processed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad1ab-107">Notes</span><span class="sxs-lookup"><span data-stu-id="ad1ab-107">Remarks</span></span>  
 <span data-ttu-id="ad1ab-108">En règle générale, vous souhaitez un jeton de traitement s’il est dans la portée de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="ad1ab-108">Typically, you want a token to be processed if it is in the metadata scope.</span></span> <span data-ttu-id="ad1ab-109">Le `MarkToken` méthode est passée au moteur de métadonnées via la [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="ad1ab-109">The `MarkToken` method is passed to the metadata engine via the [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad1ab-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ad1ab-110">Requirements</span></span>  
 <span data-ttu-id="ad1ab-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad1ab-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad1ab-112">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ad1ab-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ad1ab-113">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ad1ab-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ad1ab-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad1ab-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad1ab-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad1ab-115">See Also</span></span>  
 [<span data-ttu-id="ad1ab-116">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="ad1ab-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="ad1ab-117">IHostFilter, interface</span><span class="sxs-lookup"><span data-stu-id="ad1ab-117">IHostFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)
