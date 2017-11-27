---
title: "IMetaDataImport::IsValidToken, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.IsValidToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::IsValidToken
helpviewer_keywords:
- IMetaDataImport::IsValidToken method [.NET Framework metadata]
- IsValidToken method [.NET Framework metadata]
ms.assetid: aeb0fc63-9eff-4384-9284-cb9900572d74
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3c916e71518ded93c90b270205dd975201762846
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportisvalidtoken-method"></a><span data-ttu-id="1b872-102">IMetaDataImport::IsValidToken, méthode</span><span class="sxs-lookup"><span data-stu-id="1b872-102">IMetaDataImport::IsValidToken Method</span></span>
<span data-ttu-id="1b872-103">Obtient une valeur indiquant si le jeton spécifié contient une référence valide à un objet de code.</span><span class="sxs-lookup"><span data-stu-id="1b872-103">Gets a value indicating whether the specified token holds a valid reference to a code object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b872-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b872-104">Syntax</span></span>  
  
```  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1b872-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1b872-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="1b872-106">[in] Le jeton pour vérifier la validité de la référence.</span><span class="sxs-lookup"><span data-stu-id="1b872-106">[in] The token to check the reference validity for.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1b872-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1b872-107">Return Value</span></span>  
 <span data-ttu-id="1b872-108">`true`Si `tk` est un jeton de métadonnées valide dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="1b872-108">`true` if `tk` is a valid metadata token within the current scope.</span></span> <span data-ttu-id="1b872-109">Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="1b872-109">Otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b872-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1b872-110">Requirements</span></span>  
 <span data-ttu-id="1b872-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b872-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b872-112">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1b872-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1b872-113">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1b872-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1b872-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b872-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b872-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b872-115">See Also</span></span>  
 [<span data-ttu-id="1b872-116">IMetaDataImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="1b872-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="1b872-117">IMetaDataImport2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="1b872-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
