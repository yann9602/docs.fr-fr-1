---
title: "IMetaDataEmit::SaveToMemory, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SaveToMemory
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SaveToMemory
helpviewer_keywords:
- IMetaDataEmit::SaveToMemory method [.NET Framework metadata]
- SaveToMemory method [.NET Framework metadata]
ms.assetid: d5237628-2675-45ed-a39e-65c0731b6a56
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 685ed69964970f505ad6f938af361c48664d2279
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsavetomemory-method"></a><span data-ttu-id="50eca-102">IMetaDataEmit::SaveToMemory, méthode</span><span class="sxs-lookup"><span data-stu-id="50eca-102">IMetaDataEmit::SaveToMemory Method</span></span>
<span data-ttu-id="50eca-103">Enregistre toutes les métadonnées dans la portée actuelle dans la zone de mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="50eca-103">Saves all metadata in the current scope to the specified area of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50eca-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50eca-104">Syntax</span></span>  
  
```  
HRESULT SaveToMemory (   
    [out]  void        *pbData,   
    [in]   ULONG       cbData   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="50eca-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="50eca-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="50eca-106">[out] L’adresse à laquelle commencer l’écriture des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="50eca-106">[out] The address at which to begin writing metadata.</span></span>  
  
 `cbData`  
 <span data-ttu-id="50eca-107">[in] La taille, en octets, de la mémoire allouée.</span><span class="sxs-lookup"><span data-stu-id="50eca-107">[in] The size, in bytes, of the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50eca-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="50eca-108">Requirements</span></span>  
 <span data-ttu-id="50eca-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50eca-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50eca-110">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="50eca-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="50eca-111">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="50eca-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50eca-112">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50eca-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50eca-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50eca-113">See Also</span></span>  
 [<span data-ttu-id="50eca-114">IMetaDataEmit (Interface)</span><span class="sxs-lookup"><span data-stu-id="50eca-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="50eca-115">IMetaDataEmit2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="50eca-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
