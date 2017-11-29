---
title: "IAssemblyName::GetProperty, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyName.GetProperty
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyName::GetProperty
helpviewer_keywords:
- IAssemblyName::GetProperty method [.NET Framework fusion]
- GetProperty method [.NET Framework fusion]
ms.assetid: e59fda62-77d5-4e37-89cb-ce7ae4627975
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6eae7cf2d6dabe9bad4912d6a97249f52464fe65
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="iassemblynamegetproperty-method"></a><span data-ttu-id="cb4b9-102">IAssemblyName::GetProperty, méthode</span><span class="sxs-lookup"><span data-stu-id="cb4b9-102">IAssemblyName::GetProperty Method</span></span>
<span data-ttu-id="cb4b9-103">Obtient un pointeur vers la propriété référencée par l’identificateur de propriété spécifié.</span><span class="sxs-lookup"><span data-stu-id="cb4b9-103">Gets a pointer to the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb4b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb4b9-104">Syntax</span></span>  
  
```  
HRESULT GetProperty (  
    [in]      DWORD    PropertyId,  
    [out]     LPVOID   pvProperty,  
    [in, out] LPDWORD  pcbProperty  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cb4b9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cb4b9-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="cb4b9-106">[in] Identificateur unique pour la propriété demandée.</span><span class="sxs-lookup"><span data-stu-id="cb4b9-106">[in] The unique identifier for the requested property.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="cb4b9-107">[out] Les données de la propriété renvoyée.</span><span class="sxs-lookup"><span data-stu-id="cb4b9-107">[out] The returned property data.</span></span>  
  
 `pcbProperty`  
 <span data-ttu-id="cb4b9-108">[dans, out] La taille, en octets, de `pvProperty`.</span><span class="sxs-lookup"><span data-stu-id="cb4b9-108">[in, out] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb4b9-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="cb4b9-109">Requirements</span></span>  
 <span data-ttu-id="cb4b9-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb4b9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb4b9-111">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="cb4b9-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="cb4b9-112">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb4b9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb4b9-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb4b9-113">See Also</span></span>  
 [<span data-ttu-id="cb4b9-114">IAssemblyName (Interface)</span><span class="sxs-lookup"><span data-stu-id="cb4b9-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
