---
title: "IMetaDataImport::GetRVA, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetRVA
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6c055afaa129b52c67cd0463a5d44afec5cde103
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="bf3a9-102">IMetaDataImport::GetRVA, méthode</span><span class="sxs-lookup"><span data-stu-id="bf3a9-102">IMetaDataImport::GetRVA Method</span></span>
<span data-ttu-id="bf3a9-103">Obtient l’adresse virtuelle relative (RVA) et les indicateurs d’implémentation de la méthode ou le champ représenté par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="bf3a9-103">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf3a9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf3a9-104">Syntax</span></span>  
  
```  
HRESULT GetRVA (  
   [in]  mdToken     tk,   
   [out] ULONG       *pulCodeRVA,   
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bf3a9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bf3a9-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="bf3a9-106">[in] Un jeton de métadonnées MethodDef ou FieldDef qui représente l’objet de code pour renvoyer l’adresse RVA.</span><span class="sxs-lookup"><span data-stu-id="bf3a9-106">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="bf3a9-107">Si le jeton est FieldDef, le champ doit être une variable globale.</span><span class="sxs-lookup"><span data-stu-id="bf3a9-107">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="bf3a9-108">[out] Pointeur vers l’adresse virtuelle relative de l’objet de code représenté par le jeton.</span><span class="sxs-lookup"><span data-stu-id="bf3a9-108">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="bf3a9-109">[out] Pointeur vers les indicateurs d’implémentation pour la méthode.</span><span class="sxs-lookup"><span data-stu-id="bf3a9-109">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="bf3a9-110">Cette valeur est un masque de bits de le [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) énumération.</span><span class="sxs-lookup"><span data-stu-id="bf3a9-110">This value is a bitmask from the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="bf3a9-111">La valeur de `pdwImplFlags` n’est valide uniquement si `tk` est un jeton MethodDef.</span><span class="sxs-lookup"><span data-stu-id="bf3a9-111">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf3a9-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bf3a9-112">Requirements</span></span>  
 <span data-ttu-id="bf3a9-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf3a9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf3a9-114">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bf3a9-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bf3a9-115">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bf3a9-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bf3a9-116">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf3a9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf3a9-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf3a9-117">See Also</span></span>  
 [<span data-ttu-id="bf3a9-118">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="bf3a9-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="bf3a9-119">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="bf3a9-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
