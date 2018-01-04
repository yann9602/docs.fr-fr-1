---
title: "IMetaDataImport::GetModuleFromScope, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetModuleFromScope
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetModuleFromScope
helpviewer_keywords:
- GetModuleFromScope method [.NET Framework metadata]
- IMetaDataImport::GetModuleFromScope method [.NET Framework metadata]
ms.assetid: add68d3f-45fd-4bef-af94-eb5273f26b11
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b389df634a69bff6197ae11dea96fbb6344dd369
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="9d4cd-102">IMetaDataImport::GetModuleFromScope, méthode</span><span class="sxs-lookup"><span data-stu-id="9d4cd-102">IMetaDataImport::GetModuleFromScope Method</span></span>
<span data-ttu-id="9d4cd-103">Obtient des jetons de métadonnées pour le module référencé dans la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="9d4cd-103">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d4cd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d4cd-104">Syntax</span></span>  
  
```  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d4cd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9d4cd-105">Parameters</span></span>  
 `pmd`  
 <span data-ttu-id="9d4cd-106">[out] Pointeur vers le jeton représentant le module référencé dans la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="9d4cd-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d4cd-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9d4cd-107">Requirements</span></span>  
 <span data-ttu-id="9d4cd-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d4cd-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d4cd-109">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9d4cd-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9d4cd-110">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9d4cd-110">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9d4cd-111">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d4cd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d4cd-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d4cd-112">See Also</span></span>  
 [<span data-ttu-id="9d4cd-113">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="9d4cd-113">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="9d4cd-114">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="9d4cd-114">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
