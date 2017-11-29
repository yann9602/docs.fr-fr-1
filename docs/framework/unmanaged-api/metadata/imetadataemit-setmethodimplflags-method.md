---
title: "IMetaDataEmit::SetMethodImplFlags, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetMethodImplFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetMethodImplFlags
helpviewer_keywords:
- IMetaDataEmit::SetMethodImplFlags method [.NET Framework metadata]
- SetMethodImpFlags method [.NET Framework metadata]
ms.assetid: 4bc82d9b-9544-4be3-ba51-a2d4d806158a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d69940d5cffe397d009b7364a20a09dbbd95db4c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetmethodimplflags-method"></a><span data-ttu-id="100bc-102">IMetaDataEmit::SetMethodImplFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="100bc-102">IMetaDataEmit::SetMethodImplFlags Method</span></span>
<span data-ttu-id="100bc-103">Définit ou met à jour de la signature de métadonnées de l’implémentation de méthode héritée qui est référencée par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="100bc-103">Sets or updates the metadata signature of the inherited method implementation that is referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="100bc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="100bc-104">Syntax</span></span>  
  
```  
HRESULT SetMethodImplFlags (   
    [in]  mdMethodDef   md,   
    [in]  DWORD         dwImplFlags   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="100bc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="100bc-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="100bc-106">[in] Le jeton pour la méthode doit être modifié.</span><span class="sxs-lookup"><span data-stu-id="100bc-106">[in] The token for the method to be changed.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="100bc-107">[in] Une combinaison des valeurs de la [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) énumération qui spécifie les fonctionnalités d’implémentation de méthode.</span><span class="sxs-lookup"><span data-stu-id="100bc-107">[in] A combination of the values of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the method implementation features.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="100bc-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="100bc-108">Requirements</span></span>  
 <span data-ttu-id="100bc-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="100bc-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="100bc-110">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="100bc-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="100bc-111">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="100bc-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="100bc-112">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="100bc-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="100bc-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="100bc-113">See Also</span></span>  
 [<span data-ttu-id="100bc-114">IMetaDataEmit (Interface)</span><span class="sxs-lookup"><span data-stu-id="100bc-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="100bc-115">IMetaDataEmit2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="100bc-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
