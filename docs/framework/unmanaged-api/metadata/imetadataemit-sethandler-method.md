---
title: "IMetaDataEmit::SetHandler, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetHandler
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetHandler
helpviewer_keywords:
- IMetaDataEmit::SetHandler method [.NET Framework metadata]
- SetHandler method [.NET Framework metadata]
ms.assetid: c6c1aaaf-e2cd-407c-b73e-fbe6ffd83bb3
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d4a56db43f932a155b4251f019e39dc5640eb014
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="ac537-102">IMetaDataEmit::SetHandler, méthode</span><span class="sxs-lookup"><span data-stu-id="ac537-102">IMetaDataEmit::SetHandler Method</span></span>
<span data-ttu-id="ac537-103">Définit la méthode référencée par le `IUnknown` pointeur en tant que notification de rappel pour le jeton remappe.</span><span class="sxs-lookup"><span data-stu-id="ac537-103">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac537-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac537-104">Syntax</span></span>  
  
```  
HRESULT SetHandler (   
    [in]  IUnknown    *pUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ac537-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ac537-105">Parameters</span></span>  
 `pUnk`  
 <span data-ttu-id="ac537-106">[in] Le Gestionnaire d’inscription.</span><span class="sxs-lookup"><span data-stu-id="ac537-106">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac537-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="ac537-107">Remarks</span></span>  
 <span data-ttu-id="ac537-108">Le moteur de métadonnées envoie la notification à l’aide de la méthode est fournie par `SetHandler`, pour les compilateurs qui ne génèrent pas d’enregistrements de manière optimisée et qui souhaitent optimiser les enregistrements sauvegardés.</span><span class="sxs-lookup"><span data-stu-id="ac537-108">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="ac537-109">Si la méthode de rappel n’est pas fournie via `SetHandler`, aucune optimisation ne se fera sur Enregistrer, sauf dans lequel importent les plusieurs étendues ont été fusionnées à l’aide de `IMapToken` de fusion pour chaque étendue.</span><span class="sxs-lookup"><span data-stu-id="ac537-109">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac537-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ac537-110">Requirements</span></span>  
 <span data-ttu-id="ac537-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac537-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac537-112">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ac537-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ac537-113">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ac537-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac537-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac537-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac537-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac537-115">See Also</span></span>  
 [<span data-ttu-id="ac537-116">IMetaDataEmit (Interface)</span><span class="sxs-lookup"><span data-stu-id="ac537-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="ac537-117">IMetaDataEmit2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="ac537-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
