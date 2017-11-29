---
title: "IMetaDataEmit::DefineUserString, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineUserString
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineUserString
helpviewer_keywords:
- DefineUserString method [.NET Framework metadata]
- IMetaDataEmit::DefineUserString method [.NET Framework metadata]
ms.assetid: 88fb7ef3-bbdf-429c-b678-c9c153456461
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: eb3e21e88da8fec08acf1ecbe451c5914b6cccaf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefineuserstring-method"></a><span data-ttu-id="c91d8-102">IMetaDataEmit::DefineUserString, méthode</span><span class="sxs-lookup"><span data-stu-id="c91d8-102">IMetaDataEmit::DefineUserString Method</span></span>
<span data-ttu-id="c91d8-103">Obtient les métadonnées jeton pour la chaîne littérale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c91d8-103">Gets a metadata token for the specified literal string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c91d8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c91d8-104">Syntax</span></span>  
  
```  
HRESULT DefineUserString (   
    [in]  LPCWSTR     szString,   
    [in]  ULONG       cchString,   
    [out] mdString    *pstk   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c91d8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c91d8-105">Parameters</span></span>  
 `szString`  
 <span data-ttu-id="c91d8-106">[in] La chaîne de l’utilisateur à enregistrer.</span><span class="sxs-lookup"><span data-stu-id="c91d8-106">[in] The user string to store.</span></span>  
  
 `cchString`  
 <span data-ttu-id="c91d8-107">[in] Le nombre de caractères larges dans `szString`.</span><span class="sxs-lookup"><span data-stu-id="c91d8-107">[in] The count of wide characters in `szString`.</span></span>  
  
 `pstk`  
 <span data-ttu-id="c91d8-108">[out] Le jeton de chaîne assigné.</span><span class="sxs-lookup"><span data-stu-id="c91d8-108">[out] The string token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c91d8-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c91d8-109">Requirements</span></span>  
 <span data-ttu-id="c91d8-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c91d8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c91d8-111">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c91d8-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c91d8-112">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c91d8-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c91d8-113">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c91d8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c91d8-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c91d8-114">See Also</span></span>  
 [<span data-ttu-id="c91d8-115">IMetaDataEmit (Interface)</span><span class="sxs-lookup"><span data-stu-id="c91d8-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="c91d8-116">IMetaDataEmit2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="c91d8-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
