---
title: "IMetaDataEmit::DeleteToken, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DeleteToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DeleteToken
helpviewer_keywords:
- DeleteToken method [.NET Framework metadata]
- IMetaDataEmit::DeleteToken method [.NET Framework metadata]
ms.assetid: a4926d0a-261b-46b1-9994-82633661a64b
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5fe79e13a44ef9d916a0009c46200605950e8895
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdeletetoken-method"></a><span data-ttu-id="978ac-102">IMetaDataEmit::DeleteToken, méthode</span><span class="sxs-lookup"><span data-stu-id="978ac-102">IMetaDataEmit::DeleteToken Method</span></span>
<span data-ttu-id="978ac-103">Supprime le jeton spécifié de la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="978ac-103">Deletes the specified token from the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="978ac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="978ac-104">Syntax</span></span>  
  
```  
HRESULT DeleteToken (   
    [in]  mdToken     tkObj   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="978ac-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="978ac-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="978ac-106">[in] Le jeton doit être supprimé.</span><span class="sxs-lookup"><span data-stu-id="978ac-106">[in] The token to be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="978ac-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="978ac-107">Requirements</span></span>  
 <span data-ttu-id="978ac-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="978ac-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="978ac-109">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="978ac-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="978ac-110">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="978ac-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="978ac-111">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="978ac-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="978ac-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="978ac-112">See Also</span></span>  
 [<span data-ttu-id="978ac-113">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="978ac-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="978ac-114">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="978ac-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
