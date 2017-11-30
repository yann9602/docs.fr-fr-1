---
title: "IMetaDataEmit::DeleteClassLayout, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DeleteClassLayout
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DeleteClassLayout
helpviewer_keywords:
- DeleteClassLayout method [.NET Framework metadata]
- IMetaDataEmit::DeleteClassLayout method [.NET Framework metadata]
ms.assetid: 65a4ad49-fa49-4b36-8ed1-76dd6a185ab4
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a35606f85e134886addd8b30c240442800a9109e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdeleteclasslayout-method"></a><span data-ttu-id="a4c24-102">IMetaDataEmit::DeleteClassLayout, méthode</span><span class="sxs-lookup"><span data-stu-id="a4c24-102">IMetaDataEmit::DeleteClassLayout Method</span></span>
<span data-ttu-id="a4c24-103">Détruit la signature de métadonnées de disposition de classe pour le type représenté par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="a4c24-103">Destroys the class layout metadata signature for the type represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4c24-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4c24-104">Syntax</span></span>  
  
```  
HRESULT DeleteClassLayout (  
    [in]  mdTypeDef   td  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a4c24-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a4c24-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="a4c24-106">[in] Un `mdTypeDef` jeton de métadonnées qui représente le type pour lequel la disposition de la classe est supprimée.</span><span class="sxs-lookup"><span data-stu-id="a4c24-106">[in] An `mdTypeDef` metadata token that represents the type for which the class layout will be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4c24-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a4c24-107">Requirements</span></span>  
 <span data-ttu-id="a4c24-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4c24-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4c24-109">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a4c24-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a4c24-110">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a4c24-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a4c24-111">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4c24-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4c24-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4c24-112">See Also</span></span>  
 [<span data-ttu-id="a4c24-113">IMetaDataEmit (Interface)</span><span class="sxs-lookup"><span data-stu-id="a4c24-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="a4c24-114">IMetaDataEmit2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="a4c24-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
