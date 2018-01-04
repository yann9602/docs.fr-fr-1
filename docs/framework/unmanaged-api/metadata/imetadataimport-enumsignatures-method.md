---
title: "IMetaDataImport::EnumSignatures, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumSignatures
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumSignatures
helpviewer_keywords:
- EnumSignatures method [.NET Framework metadata]
- IMetaDataImport::EnumSignatures method [.NET Framework metadata]
ms.assetid: d0d65060-6f90-42a2-95cf-6ffb04352996
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 88d47e2512103947f007c81450157a0b3e334a33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumsignatures-method"></a><span data-ttu-id="42af3-102">IMetaDataImport::EnumSignatures, méthode</span><span class="sxs-lookup"><span data-stu-id="42af3-102">IMetaDataImport::EnumSignatures Method</span></span>
<span data-ttu-id="42af3-103">Énumère les jetons Signature représentant des signatures autonomes dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="42af3-103">Enumerates Signature tokens representing stand-alone signatures in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42af3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42af3-104">Syntax</span></span>  
  
```  
HRESULT EnumSignatures (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdSignature  rSignatures[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcSignatures  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="42af3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="42af3-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="42af3-106">[dans, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="42af3-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="42af3-107">Cela doit être NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="42af3-107">This must be NULL for the first call of this method.</span></span>  
  
 `rSignatures`  
 <span data-ttu-id="42af3-108">[out] Tableau utilisé pour stocker les jetons de Signature.</span><span class="sxs-lookup"><span data-stu-id="42af3-108">[out] The array used to store the Signature tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="42af3-109">[in] Taille maximale du tableau `rSignatures`.</span><span class="sxs-lookup"><span data-stu-id="42af3-109">[in] The maximum size of the `rSignatures` array.</span></span>  
  
 `pcSignatures`  
 <span data-ttu-id="42af3-110">[out] Le nombre de jetons Signature retournés dans `rSignatures`.</span><span class="sxs-lookup"><span data-stu-id="42af3-110">[out] The number of Signature tokens returned in `rSignatures`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="42af3-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="42af3-111">Return Value</span></span>  
  
|<span data-ttu-id="42af3-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="42af3-112">HRESULT</span></span>|<span data-ttu-id="42af3-113">Description</span><span class="sxs-lookup"><span data-stu-id="42af3-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="42af3-114">`EnumSignatures`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="42af3-114">`EnumSignatures` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="42af3-115">Il n’existe pas de jetons à énumérer.</span><span class="sxs-lookup"><span data-stu-id="42af3-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="42af3-116">Dans ce cas, `pcSignatures` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="42af3-116">In that case, `pcSignatures` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42af3-117">Notes</span><span class="sxs-lookup"><span data-stu-id="42af3-117">Remarks</span></span>  
 <span data-ttu-id="42af3-118">Les jetons Signature sont créés par le [IMetaDataEmit::GetTokenFromSig](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="42af3-118">The Signature tokens are created by the [IMetaDataEmit::GetTokenFromSig](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42af3-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="42af3-119">Requirements</span></span>  
 <span data-ttu-id="42af3-120">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42af3-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42af3-121">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="42af3-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="42af3-122">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="42af3-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="42af3-123">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42af3-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42af3-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42af3-124">See Also</span></span>  
 [<span data-ttu-id="42af3-125">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="42af3-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="42af3-126">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="42af3-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
