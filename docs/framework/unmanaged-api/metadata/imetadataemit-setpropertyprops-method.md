---
title: "IMetaDataEmit::SetPropertyProps, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetPropertyProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetPropertyProps
helpviewer_keywords:
- SetPropertyProps method [.NET Framework metadata]
- IMetaDataEmit::SetPropertyProps method [.NET Framework metadata]
ms.assetid: e2501fc8-b2bc-4dcc-9205-e3acd5a53ffe
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: fe79846b9fd576941c706b48a7aed0667c264a3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetpropertyprops-method"></a><span data-ttu-id="31993-102">IMetaDataEmit::SetPropertyProps, méthode</span><span class="sxs-lookup"><span data-stu-id="31993-102">IMetaDataEmit::SetPropertyProps Method</span></span>
<span data-ttu-id="31993-103">Définit les fonctionnalités stockées dans les métadonnées pour une propriété définie par un appel antérieur à [DefineProperty, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span><span class="sxs-lookup"><span data-stu-id="31993-103">Sets the features stored in metadata for a property defined by a prior call to [DefineProperty Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31993-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31993-104">Syntax</span></span>  
  
```  
HRESULT SetPropertyProps (   
    [in]  mdProperty      pr,   
    [in]  DWORD           dwPropFlags,   
    [in]  DWORD           dwCPlusTypeFlag,   
    [in]  void const      *pValue,   
    [in]  ULONG           cchValue,   
    [in]  mdMethodDef     mdSetter,   
    [in]  mdMethodDef     mdGetter,   
    [in]  mdMethodDef     rmdOtherMethods[]   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31993-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="31993-105">Parameters</span></span>  
 `pr`  
 <span data-ttu-id="31993-106">[in] Le jeton pour la propriété à modifier</span><span class="sxs-lookup"><span data-stu-id="31993-106">[in] The token for the property to be changed</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="31993-107">[in] Indicateurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="31993-107">[in] Property flags.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="31993-108">[in] Le type de la valeur de propriété par défaut.</span><span class="sxs-lookup"><span data-stu-id="31993-108">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="31993-109">[in] La valeur par défaut pour la propriété.</span><span class="sxs-lookup"><span data-stu-id="31993-109">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="31993-110">[in] Le nombre de caractères (Unicode) caractères `pValue`.</span><span class="sxs-lookup"><span data-stu-id="31993-110">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="31993-111">[in] La méthode qui définit la valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="31993-111">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="31993-112">[in] La méthode qui obtient la valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="31993-112">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="31993-113">[in] Un tableau des autres méthodes associées à la propriété.</span><span class="sxs-lookup"><span data-stu-id="31993-113">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="31993-114">Mettre fin à ce tableau avec un `mdTokenNil` jeton.</span><span class="sxs-lookup"><span data-stu-id="31993-114">Terminate this array with an `mdTokenNil` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31993-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="31993-115">Requirements</span></span>  
 <span data-ttu-id="31993-116">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31993-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31993-117">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="31993-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="31993-118">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="31993-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31993-119">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31993-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31993-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31993-120">See Also</span></span>  
 [<span data-ttu-id="31993-121">IMetaDataEmit (Interface)</span><span class="sxs-lookup"><span data-stu-id="31993-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="31993-122">IMetaDataEmit2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="31993-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
