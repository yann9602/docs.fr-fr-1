---
title: "IMetaDataFilter::IsTokenMarked, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataFilter.IsTokenMarked
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataFilter::IsTokenMarked
helpviewer_keywords:
- IMetaDataFilter::IsTokenMarked method [.NET Framework metadata]
- IsTokenMarked method [.NET Framework metadata]
ms.assetid: 7d90dcee-0206-4540-807b-06982fe65f1a
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 832f1e57e55245a84d093a41c627613d5fbe6902
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadatafilteristokenmarked-method"></a><span data-ttu-id="f3e32-102">IMetaDataFilter::IsTokenMarked, méthode</span><span class="sxs-lookup"><span data-stu-id="f3e32-102">IMetaDataFilter::IsTokenMarked Method</span></span>
<span data-ttu-id="f3e32-103">Obtient une valeur qui indique si le jeton de métadonnées spécifié a été marqué comme traité.</span><span class="sxs-lookup"><span data-stu-id="f3e32-103">Gets a value indicating whether the specified metadata token has been marked as processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3e32-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3e32-104">Syntax</span></span>  
  
```  
HRESULT IsTokenMarked (  
    [in]  mdToken  tk,   
    [out] BOOL     *pIsMarked  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f3e32-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f3e32-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="f3e32-106">[in] Le jeton à examiner pour une marque de traitement.</span><span class="sxs-lookup"><span data-stu-id="f3e32-106">[in] The token to examine for a processing mark.</span></span>  
  
 `pIsMarked`  
 <span data-ttu-id="f3e32-107">[out] Une valeur qui est `true` si `tk` a été traitée ; sinon `false`.</span><span class="sxs-lookup"><span data-stu-id="f3e32-107">[out] A value that is `true` if `tk` has been processed; otherwise `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3e32-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f3e32-108">Requirements</span></span>  
 <span data-ttu-id="f3e32-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3e32-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3e32-110">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f3e32-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f3e32-111">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f3e32-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f3e32-112">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3e32-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3e32-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3e32-113">See Also</span></span>  
 [<span data-ttu-id="f3e32-114">IMetaDataFilter (Interface)</span><span class="sxs-lookup"><span data-stu-id="f3e32-114">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
