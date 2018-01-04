---
title: "IMetaDataImport::GetUserString, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetUserString
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetUserString
helpviewer_keywords:
- IMetaDataImport::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 0fd3bb47-58b5-4083-b241-b9719df7a285
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 944d7e6413f35ad56af38dee90dc90f881c1d4cc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetuserstring-method"></a><span data-ttu-id="75cbe-102">IMetaDataImport::GetUserString, méthode</span><span class="sxs-lookup"><span data-stu-id="75cbe-102">IMetaDataImport::GetUserString Method</span></span>
<span data-ttu-id="75cbe-103">Obtient la chaîne littérale représentée par le jeton de métadonnées spécifié.</span><span class="sxs-lookup"><span data-stu-id="75cbe-103">Gets the literal string represented by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75cbe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75cbe-104">Syntax</span></span>  
  
```  
HRESULT GetUserString (  
   [in]   mdString    stk,  
   [out]  LPWSTR      szString,  
   [in]   ULONG       cchString,  
   [out]  ULONG       *pchString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="75cbe-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="75cbe-105">Parameters</span></span>  
 `stk`  
 <span data-ttu-id="75cbe-106">[in] Le jeton de chaîne pour retourner la chaîne associée.</span><span class="sxs-lookup"><span data-stu-id="75cbe-106">[in] The String token to return the associated string for.</span></span>  
  
 `szString`  
 <span data-ttu-id="75cbe-107">[out] Une copie de la chaîne demandée.</span><span class="sxs-lookup"><span data-stu-id="75cbe-107">[out] A copy of the requested string.</span></span>  
  
 `cchString`  
 <span data-ttu-id="75cbe-108">[in] La taille maximale en caractères larges de demandé `szString`.</span><span class="sxs-lookup"><span data-stu-id="75cbe-108">[in] The maximum size in wide characters of the requested `szString`.</span></span>  
  
 `pchString`  
 <span data-ttu-id="75cbe-109">[out] La taille en caractères larges de retourné `szString`.</span><span class="sxs-lookup"><span data-stu-id="75cbe-109">[out] The size in wide characters of the returned `szString`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75cbe-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="75cbe-110">Requirements</span></span>  
 <span data-ttu-id="75cbe-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75cbe-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75cbe-112">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="75cbe-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="75cbe-113">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="75cbe-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="75cbe-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75cbe-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75cbe-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75cbe-115">See Also</span></span>  
 [<span data-ttu-id="75cbe-116">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="75cbe-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="75cbe-117">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="75cbe-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
