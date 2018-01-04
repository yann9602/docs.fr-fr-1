---
title: "IMetaDataEmit::DefineMethodImpl, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineMethodImpl
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineMethodImpl
helpviewer_keywords:
- DefineMethodImpl method [.NET Framework metadata]
- IMetaDataEmit::DefineMethodImpl method [.NET Framework metadata]
ms.assetid: 9dcc8b3d-33ee-4c7c-8d6f-322c57b94a0f
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5bf16c51a241a01f18aae84f8b3bb7554f08b87c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="ffce0-102">IMetaDataEmit::DefineMethodImpl, méthode</span><span class="sxs-lookup"><span data-stu-id="ffce0-102">IMetaDataEmit::DefineMethodImpl Method</span></span>
<span data-ttu-id="ffce0-103">Crée une définition pour l’implémentation d’une méthode héritée d’une interface et retourne un jeton pour cette définition d’implémentation de méthode.</span><span class="sxs-lookup"><span data-stu-id="ffce0-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffce0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ffce0-104">Syntax</span></span>  
  
```  
HRESULT DefineMethodImpl (   
    [in]  mdTypeDef         td,   
    [in]  mdToken           tkBody,   
    [in]  mdToken           tkDecl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ffce0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ffce0-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="ffce0-106">[in] Le `mdTypedef` jeton de la classe d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="ffce0-106">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="ffce0-107">[in] Le `mdMethodDef` ou `mdMethodRef` jeton du corps du code.</span><span class="sxs-lookup"><span data-stu-id="ffce0-107">[in] The `mdMethodDef` or `mdMethodRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="ffce0-108">[in] Le `mdMethodDef` ou `mdMethodRef` jeton de la méthode d’interface implémentée.</span><span class="sxs-lookup"><span data-stu-id="ffce0-108">[in] The `mdMethodDef` or `mdMethodRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffce0-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ffce0-109">Requirements</span></span>  
 <span data-ttu-id="ffce0-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffce0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffce0-111">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ffce0-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ffce0-112">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ffce0-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ffce0-113">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffce0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffce0-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ffce0-114">See Also</span></span>  
 [<span data-ttu-id="ffce0-115">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="ffce0-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="ffce0-116">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="ffce0-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
