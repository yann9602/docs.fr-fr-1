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
ms.workload: dotnet
ms.openlocfilehash: 61af4f5e68ebd5d5e4639cbc4c581d1c66358ff8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportisvalidtoken-method"></a><span data-ttu-id="2cba1-102">IMetaDataImport::IsValidToken, méthode</span><span class="sxs-lookup"><span data-stu-id="2cba1-102">IMetaDataImport::IsValidToken Method</span></span>
<span data-ttu-id="2cba1-103">Obtient une valeur indiquant si le jeton spécifié contient une référence valide à un objet de code.</span><span class="sxs-lookup"><span data-stu-id="2cba1-103">Gets a value indicating whether the specified token holds a valid reference to a code object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cba1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2cba1-104">Syntax</span></span>  
  
```  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2cba1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2cba1-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="2cba1-106">[in] Le jeton pour vérifier la validité de la référence.</span><span class="sxs-lookup"><span data-stu-id="2cba1-106">[in] The token to check the reference validity for.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2cba1-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2cba1-107">Return Value</span></span>  
 <span data-ttu-id="2cba1-108">`true`Si `tk` est un jeton de métadonnées valide dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="2cba1-108">`true` if `tk` is a valid metadata token within the current scope.</span></span> <span data-ttu-id="2cba1-109">Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="2cba1-109">Otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cba1-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2cba1-110">Requirements</span></span>  
 <span data-ttu-id="2cba1-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cba1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cba1-112">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2cba1-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2cba1-113">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2cba1-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2cba1-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cba1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cba1-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2cba1-115">See Also</span></span>  
 [<span data-ttu-id="2cba1-116">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="2cba1-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="2cba1-117">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="2cba1-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
