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
ms.openlocfilehash: 9556880ad534f5c82d8d0e874129876478e2e63f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostfiltermarktoken-method"></a><span data-ttu-id="3e980-102">IHostFilter::MarkToken, méthode</span><span class="sxs-lookup"><span data-stu-id="3e980-102">IHostFilter::MarkToken Method</span></span>
<span data-ttu-id="3e980-103">Indique que le jeton de métadonnées spécifié sera traité.</span><span class="sxs-lookup"><span data-stu-id="3e980-103">Indicates that the specified metadata token will be processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e980-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e980-104">Syntax</span></span>  
  
```  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3e980-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3e980-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="3e980-106">[in] Le jeton de métadonnées à traiter.</span><span class="sxs-lookup"><span data-stu-id="3e980-106">[in] The metadata token to be processed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e980-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="3e980-107">Remarks</span></span>  
 <span data-ttu-id="3e980-108">En règle générale, vous souhaitez un jeton de traitement s’il est dans la portée de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="3e980-108">Typically, you want a token to be processed if it is in the metadata scope.</span></span> <span data-ttu-id="3e980-109">Le `MarkToken` méthode est passée au moteur de métadonnées via la [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="3e980-109">The `MarkToken` method is passed to the metadata engine via the [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e980-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3e980-110">Requirements</span></span>  
 <span data-ttu-id="3e980-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e980-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e980-112">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3e980-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3e980-113">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3e980-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3e980-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e980-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e980-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e980-115">See Also</span></span>  
 [<span data-ttu-id="3e980-116">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="3e980-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="3e980-117">IHostFilter (Interface)</span><span class="sxs-lookup"><span data-stu-id="3e980-117">IHostFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)
