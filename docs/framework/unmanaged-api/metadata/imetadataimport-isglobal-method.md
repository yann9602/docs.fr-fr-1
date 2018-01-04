---
title: "IMetaDataImport::IsGlobal, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.IsGlobal
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::IsGlobal
helpviewer_keywords:
- IsGlobal method [.NET Framework metadata]
- IMetaDataImport::IsGlobal method [.NET Framework metadata]
ms.assetid: 44cf6908-f555-4ae8-b2cf-24bd974bf2fe
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c23010f7175b63f140ec1367e90e145b18ae6f9c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportisglobal-method"></a><span data-ttu-id="c7b9a-102">IMetaDataImport::IsGlobal, méthode</span><span class="sxs-lookup"><span data-stu-id="c7b9a-102">IMetaDataImport::IsGlobal Method</span></span>
<span data-ttu-id="c7b9a-103">Obtient une valeur qui indique si le champ, la méthode ou le type représenté(e) par le jeton de métadonnées spécifié a une portée globale.</span><span class="sxs-lookup"><span data-stu-id="c7b9a-103">Gets a value indicating whether the field, method, or type represented by the specified metadata token has global scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7b9a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7b9a-104">Syntax</span></span>  
  
```  
HRESULT IsGlobal (  
   [in]  mdToken     pd,  
   [out] int         *pbGlobal  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c7b9a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c7b9a-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="c7b9a-106">[in] Un jeton de métadonnées qui représente un type, un champ ou une méthode.</span><span class="sxs-lookup"><span data-stu-id="c7b9a-106">[in] A metadata token that represents a type, field, or method.</span></span>  
  
 `pbGlobal`  
 <span data-ttu-id="c7b9a-107">[out] 1, si l’objet a une portée globale ; Sinon, 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="c7b9a-107">[out] 1 if the object has global scope; otherwise, 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7b9a-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c7b9a-108">Requirements</span></span>  
 <span data-ttu-id="c7b9a-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7b9a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7b9a-110">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c7b9a-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c7b9a-111">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c7b9a-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c7b9a-112">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7b9a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7b9a-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7b9a-113">See Also</span></span>  
 [<span data-ttu-id="c7b9a-114">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="c7b9a-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="c7b9a-115">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="c7b9a-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
