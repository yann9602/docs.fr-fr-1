---
title: "IMetaDataEmit::SetEventProps, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetEventProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetEventProps
helpviewer_keywords:
- IMetaDataEmit::SetEventProps method [.NET Framework metadata]
- SetEventProps method [.NET Framework metadata]
ms.assetid: 3b039e50-63ec-4730-99ff-2327408de477
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f8e2089c3f4b4e7677c2ddb9eabc8ee08cfd3695
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="cc3d2-102">IMetaDataEmit::SetEventProps, méthode</span><span class="sxs-lookup"><span data-stu-id="cc3d2-102">IMetaDataEmit::SetEventProps Method</span></span>
<span data-ttu-id="cc3d2-103">Définit ou met à jour la fonctionnalité spécifiée d’un événement défini par un appel antérieur à [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="cc3d2-103">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc3d2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc3d2-104">Syntax</span></span>  
  
```  
HRESULT SetEventProps (  
    [in]  mdEvent     ev,   
    [in]  DWORD       dwEventFlags,   
    [in]  mdToken     tkEventType,   
    [in]  mdMethodDef mdAddOn,   
    [in]  mdMethodDef mdRemoveOn,   
    [in]  mdMethodDef mdFire,   
    [in]  mdMethodDef rmdOtherMethods[]   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cc3d2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cc3d2-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="cc3d2-106">[in] Le jeton d’événement.</span><span class="sxs-lookup"><span data-stu-id="cc3d2-106">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="cc3d2-107">[in] Indicateurs d’événement.</span><span class="sxs-lookup"><span data-stu-id="cc3d2-107">[in] Event flags.</span></span> <span data-ttu-id="cc3d2-108">Il s’agit d’un masque de bits de `CorEventAttr` valeurs.</span><span class="sxs-lookup"><span data-stu-id="cc3d2-108">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="cc3d2-109">[in] Le jeton pour la classe d’événements.</span><span class="sxs-lookup"><span data-stu-id="cc3d2-109">[in] The token for the event class.</span></span> <span data-ttu-id="cc3d2-110">Il s’agit soit un `mdTypeDef` ou un `mdTypeRef` jeton.</span><span class="sxs-lookup"><span data-stu-id="cc3d2-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="cc3d2-111">[in] La méthode utilisée pour s’abonner à l’événement, ou null.</span><span class="sxs-lookup"><span data-stu-id="cc3d2-111">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="cc3d2-112">[in] La méthode utilisée pour annuler l’abonnement à l’événement, ou null.</span><span class="sxs-lookup"><span data-stu-id="cc3d2-112">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="cc3d2-113">[in] La méthode utilisée (par une classe dérivée) pour déclencher l’événement.</span><span class="sxs-lookup"><span data-stu-id="cc3d2-113">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="cc3d2-114">[in] Tableau de jetons pour les autres méthodes associées à l’événement.</span><span class="sxs-lookup"><span data-stu-id="cc3d2-114">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="cc3d2-115">Le dernier élément du tableau doit être `mdMethodDefNil`.</span><span class="sxs-lookup"><span data-stu-id="cc3d2-115">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc3d2-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cc3d2-116">Requirements</span></span>  
 <span data-ttu-id="cc3d2-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc3d2-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc3d2-118">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cc3d2-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cc3d2-119">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cc3d2-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cc3d2-120">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc3d2-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc3d2-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc3d2-121">See Also</span></span>  
 [<span data-ttu-id="cc3d2-122">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="cc3d2-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="cc3d2-123">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="cc3d2-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
