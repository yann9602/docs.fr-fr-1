---
title: "IMetaDataImport::GetMethodSemantics, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetMethodSemantics
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetMethodSemantics
helpviewer_keywords:
- GetMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::GetMethodSemantics method [.NET Framework metadata]
ms.assetid: 5e018eaa-d60e-4a0b-a2c5-8c36bd09d905
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f8921c4f6a676c9647d4e8907a22f0d68b0b359
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetmethodsemantics-method"></a><span data-ttu-id="a4cfa-102">IMetaDataImport::GetMethodSemantics, méthode</span><span class="sxs-lookup"><span data-stu-id="a4cfa-102">IMetaDataImport::GetMethodSemantics Method</span></span>
<span data-ttu-id="a4cfa-103">Obtient les indicateurs qui indique la relation entre la méthode référencée par le jeton MethodDef spécifié et la paire propriété et événement référencée par la EventProp spécifié jeton.</span><span class="sxs-lookup"><span data-stu-id="a4cfa-103">Gets flags indicating the relationship between the method referenced by the specified MethodDef token and the paired property and event referenced by the specified EventProp token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4cfa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4cfa-104">Syntax</span></span>  
  
```  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a4cfa-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a4cfa-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="a4cfa-106">[in] Jeton MethodDef représentant la méthode à obtenir les informations de rôle sémantique.</span><span class="sxs-lookup"><span data-stu-id="a4cfa-106">[in] A MethodDef token representing the method to get the semantic role information for.</span></span>  
  
 `tkEventProp`  
 <span data-ttu-id="a4cfa-107">[in] Un jeton représentant la paire propriété et un événement pour lequel obtenir le rôle de la méthode.</span><span class="sxs-lookup"><span data-stu-id="a4cfa-107">[in] A token representing the paired property and event for which to get the method's role.</span></span>  
  
 `pdwSemanticsFlags`  
 <span data-ttu-id="a4cfa-108">[out] Pointeur vers les indicateurs de sémantique associés.</span><span class="sxs-lookup"><span data-stu-id="a4cfa-108">[out] A pointer to the associated semantics flags.</span></span> <span data-ttu-id="a4cfa-109">Cette valeur est un masque de bits de le [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) énumération.</span><span class="sxs-lookup"><span data-stu-id="a4cfa-109">This value is a bitmask from the [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4cfa-110">Notes</span><span class="sxs-lookup"><span data-stu-id="a4cfa-110">Remarks</span></span>  
 <span data-ttu-id="a4cfa-111">Le [IMetaDataEmit::DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) méthode définit les indicateurs de sémantique d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="a4cfa-111">The [IMetaDataEmit::DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) method sets a method's semantics flags.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4cfa-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a4cfa-112">Requirements</span></span>  
 <span data-ttu-id="a4cfa-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4cfa-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4cfa-114">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a4cfa-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a4cfa-115">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a4cfa-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a4cfa-116">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4cfa-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4cfa-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4cfa-117">See Also</span></span>  
 [<span data-ttu-id="a4cfa-118">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="a4cfa-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="a4cfa-119">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="a4cfa-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
