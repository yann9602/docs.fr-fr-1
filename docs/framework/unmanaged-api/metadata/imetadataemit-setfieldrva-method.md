---
title: "IMetaDataEmit::SetFieldRVA, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetFieldRVA
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetFieldRVA
helpviewer_keywords:
- IMetaDataEmit::SetFieldRVA method [.NET Framework metadata]
- SetFieldRVA method [.NET Framework metadata]
ms.assetid: 6dc37f9d-87ee-4cb3-9216-ced600184ce8
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 260d5458af9fb8fbc8161018c438346fd58af06f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsetfieldrva-method"></a><span data-ttu-id="2be9d-102">IMetaDataEmit::SetFieldRVA, méthode</span><span class="sxs-lookup"><span data-stu-id="2be9d-102">IMetaDataEmit::SetFieldRVA Method</span></span>
<span data-ttu-id="2be9d-103">Définit une valeur de variable globale pour l’adresse virtuelle relative du champ référencé par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="2be9d-103">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2be9d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2be9d-104">Syntax</span></span>  
  
```  
HRESULT SetFieldRVA (   
    [in]  mdFieldDef  fd,   
    [in]  ULONG       ulRVA   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2be9d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2be9d-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="2be9d-106">[in] Le jeton pour le champ cible.</span><span class="sxs-lookup"><span data-stu-id="2be9d-106">[in] The token for the target field.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="2be9d-107">[in] L’adresse d’une zone de code ou de données.</span><span class="sxs-lookup"><span data-stu-id="2be9d-107">[in] The address of a code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2be9d-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2be9d-108">Requirements</span></span>  
 <span data-ttu-id="2be9d-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2be9d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2be9d-110">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2be9d-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2be9d-111">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2be9d-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2be9d-112">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2be9d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2be9d-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2be9d-113">See Also</span></span>  
 [<span data-ttu-id="2be9d-114">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="2be9d-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="2be9d-115">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="2be9d-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
