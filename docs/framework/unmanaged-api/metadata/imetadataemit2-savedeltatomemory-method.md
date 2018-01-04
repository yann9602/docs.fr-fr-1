---
title: "IMetaDataEmit2::SaveDeltaToMemory, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2.SaveDeltaToMemory
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2::SaveDeltaToMemory
helpviewer_keywords:
- SaveDeltaToMemory method [.NET Framework metadata]
- IMetaDataEmit2::SaveDeltaToMemory method [.NET Framework metadata]
ms.assetid: e2146726-0084-4c9e-a2d2-e8d461b13b21
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f4243840ac64a14b4f4e6c86787fdf238507635
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemit2savedeltatomemory-method"></a><span data-ttu-id="9fef4-102">IMetaDataEmit2::SaveDeltaToMemory, méthode</span><span class="sxs-lookup"><span data-stu-id="9fef4-102">IMetaDataEmit2::SaveDeltaToMemory Method</span></span>
<span data-ttu-id="9fef4-103">Enregistre les modifications de la session active de modifier et continuer à la mémoire.</span><span class="sxs-lookup"><span data-stu-id="9fef4-103">Saves changes from the current edit-and-continue session to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fef4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9fef4-104">Syntax</span></span>  
  
```  
HRESULT SaveDeltaToMemory (  
    [out] void        *pbData,   
    [in]  ULONG       cbData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9fef4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9fef4-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="9fef4-106">[out] L’adresse à laquelle commencer l’écriture du delta de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="9fef4-106">[out] The address at which to begin writing the metadata delta.</span></span>  
  
 `cbData`  
 <span data-ttu-id="9fef4-107">[in] La taille des modifications.</span><span class="sxs-lookup"><span data-stu-id="9fef4-107">[in] The size of the changes.</span></span> <span data-ttu-id="9fef4-108">Utilisez [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) pour déterminer la taille.</span><span class="sxs-lookup"><span data-stu-id="9fef4-108">Use [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) to determine the size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fef4-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9fef4-109">Requirements</span></span>  
 <span data-ttu-id="9fef4-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fef4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fef4-111">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9fef4-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9fef4-112">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9fef4-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9fef4-113">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fef4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fef4-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9fef4-114">See Also</span></span>  
 [<span data-ttu-id="9fef4-115">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="9fef4-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="9fef4-116">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="9fef4-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
