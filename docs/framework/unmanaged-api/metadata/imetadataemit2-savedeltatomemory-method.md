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
ms.openlocfilehash: b8c3148cdb417d627afd9ba007fb9892b47dcef3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemit2savedeltatomemory-method"></a><span data-ttu-id="aba02-102">IMetaDataEmit2::SaveDeltaToMemory, méthode</span><span class="sxs-lookup"><span data-stu-id="aba02-102">IMetaDataEmit2::SaveDeltaToMemory Method</span></span>
<span data-ttu-id="aba02-103">Enregistre les modifications de la session active de modifier et continuer à la mémoire.</span><span class="sxs-lookup"><span data-stu-id="aba02-103">Saves changes from the current edit-and-continue session to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aba02-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aba02-104">Syntax</span></span>  
  
```  
HRESULT SaveDeltaToMemory (  
    [out] void        *pbData,   
    [in]  ULONG       cbData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aba02-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="aba02-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="aba02-106">[out] L’adresse à laquelle commencer l’écriture du delta de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="aba02-106">[out] The address at which to begin writing the metadata delta.</span></span>  
  
 `cbData`  
 <span data-ttu-id="aba02-107">[in] La taille des modifications.</span><span class="sxs-lookup"><span data-stu-id="aba02-107">[in] The size of the changes.</span></span> <span data-ttu-id="aba02-108">Utilisez [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) pour déterminer la taille.</span><span class="sxs-lookup"><span data-stu-id="aba02-108">Use [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) to determine the size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aba02-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="aba02-109">Requirements</span></span>  
 <span data-ttu-id="aba02-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aba02-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aba02-111">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="aba02-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aba02-112">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aba02-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aba02-113">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aba02-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aba02-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aba02-114">See Also</span></span>  
 [<span data-ttu-id="aba02-115">IMetaDataEmit2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="aba02-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="aba02-116">IMetaDataEmit (Interface)</span><span class="sxs-lookup"><span data-stu-id="aba02-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
