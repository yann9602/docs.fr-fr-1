---
title: "ICorProfilerInfo::GetTokenAndMetadataFromFunction, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetTokenAndMetadataFromFunction
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetTokenAndMetadataFromFunction
helpviewer_keywords:
- ICorProfilerInfo::GetTokenAndMetadataFromFunction method [.NET Framework profiling]
- GetTokenAndMetadataFromFunction method [.NET Framework profiling]
ms.assetid: e525aa16-c923-4b16-833b-36f1f0dd70fc
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 33522d55383b1137d8591c74c988903655eba5f6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a><span data-ttu-id="2bd8b-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction, méthode</span><span class="sxs-lookup"><span data-stu-id="2bd8b-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Method</span></span>
<span data-ttu-id="2bd8b-103">Obtient le jeton de métadonnées et une instance d’interface de métadonnées qui peut être utilisée avec le jeton pour la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2bd8b-103">Gets the metadata token and a metadata interface instance that can be used against the token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bd8b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2bd8b-104">Syntax</span></span>  
  
```  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2bd8b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2bd8b-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="2bd8b-106">[in] L’ID de la fonction pour laquelle obtenir le jeton de métadonnées et l’interface de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="2bd8b-106">[in] The ID of the function for which to get the metadata token and metadata interface.</span></span>  
  
 `riid`  
 <span data-ttu-id="2bd8b-107">[in] L’ID de référence de l’interface de métadonnées pour obtenir l’instance de.</span><span class="sxs-lookup"><span data-stu-id="2bd8b-107">[in] The reference ID of the metadata interface to get the instance of.</span></span>  
  
 `ppImport`  
 <span data-ttu-id="2bd8b-108">[out] Pointeur vers l’adresse de l’instance d’interface de métadonnées qui peut être utilisé avec le jeton pour la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2bd8b-108">[out] A pointer to the address of the metadata interface instance that can be used against the token for the specified function.</span></span>  
  
 `pToken`  
 <span data-ttu-id="2bd8b-109">[out] Pointeur vers le jeton de métadonnées pour la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2bd8b-109">[out] A pointer to the metadata token for the specified function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bd8b-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2bd8b-110">Requirements</span></span>  
 <span data-ttu-id="2bd8b-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bd8b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bd8b-112">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2bd8b-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2bd8b-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2bd8b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2bd8b-114">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bd8b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bd8b-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2bd8b-115">See Also</span></span>  
 [<span data-ttu-id="2bd8b-116">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="2bd8b-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
