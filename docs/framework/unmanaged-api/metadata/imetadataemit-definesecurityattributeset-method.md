---
title: "IMetaDataEmit::DefineSecurityAttributeSet, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineSecurityAttributeSet
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineSecurityAttributeSet
helpviewer_keywords:
- IMetaDataEmit::DefineSecurityAttributeSet method [.NET Framework metadata]
- DefineSecurityAttributeSet method [.NET Framework metadata]
ms.assetid: 27064ca2-4186-4433-90a7-3b297785e891
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4863ee416bba7fe66326c1d11ec3aa0037d022a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinesecurityattributeset-method"></a><span data-ttu-id="62d4f-102">IMetaDataEmit::DefineSecurityAttributeSet, méthode</span><span class="sxs-lookup"><span data-stu-id="62d4f-102">IMetaDataEmit::DefineSecurityAttributeSet Method</span></span>
<span data-ttu-id="62d4f-103">Crée un jeu d’autorisations de sécurité à associer à l’objet référencé par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="62d4f-103">Creates a set of security permissions to attach to the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62d4f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62d4f-104">Syntax</span></span>  
  
```  
HRESULT DefineSecurityAttributeSet (   
    [in]  mdToken       tkObj,   
    [in]  COR_SECATTR   rSecAttrs[],   
    [in]  ULONG         cSecAttrs,   
    [out] ULONG         *pulErrorAttr   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62d4f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="62d4f-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="62d4f-106">[in] Le jeton auquel les informations de sécurité sont attachées.</span><span class="sxs-lookup"><span data-stu-id="62d4f-106">[in] The token to which the security information is attached.</span></span>  
  
 `rSecAttrs`  
 <span data-ttu-id="62d4f-107">[in] Un tableau de `COR_SECATTR` structures.</span><span class="sxs-lookup"><span data-stu-id="62d4f-107">[in] An array of `COR_SECATTR` structures.</span></span>  
  
 `cSecAttrs`  
 <span data-ttu-id="62d4f-108">[in] Le nombre d’éléments dans `rSecAttrs`.</span><span class="sxs-lookup"><span data-stu-id="62d4f-108">[in] The number of elements in `rSecAttrs`.</span></span>  
  
 `pulErrorAttr`  
 <span data-ttu-id="62d4f-109">[out] Si la méthode échoue, spécifie l’index dans `rSecAttrs` de l’élément qui a provoqué le problème.</span><span class="sxs-lookup"><span data-stu-id="62d4f-109">[out] If the method fails, specifies the index in `rSecAttrs` of the element that caused the problem.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62d4f-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="62d4f-110">Requirements</span></span>  
 <span data-ttu-id="62d4f-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62d4f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62d4f-112">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="62d4f-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="62d4f-113">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="62d4f-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="62d4f-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62d4f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62d4f-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62d4f-115">See Also</span></span>  
 [<span data-ttu-id="62d4f-116">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="62d4f-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="62d4f-117">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="62d4f-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
