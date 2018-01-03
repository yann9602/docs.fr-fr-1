---
title: "IAssemblyName::SetProperty, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyName.SetProperty
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyName::SetProperty
helpviewer_keywords:
- IAssemblyName::SetProperty method [.NET Framework fusion]
- SetProperty method [.NET Framework fusion]
ms.assetid: 496c3add-f60b-4073-943f-d1bcf33330cb
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 60ef27021ec3431c90086e0dfbae56bb6e6ccc86
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblynamesetproperty-method"></a><span data-ttu-id="bf62e-102">IAssemblyName::SetProperty, méthode</span><span class="sxs-lookup"><span data-stu-id="bf62e-102">IAssemblyName::SetProperty Method</span></span>
<span data-ttu-id="bf62e-103">Définit la valeur de la propriété référencée par l’identificateur de la propriété spécifiée.</span><span class="sxs-lookup"><span data-stu-id="bf62e-103">Sets the value of the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf62e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf62e-104">Syntax</span></span>  
  
```  
HRESULT SetProperty (  
    [in] DWORD  PropertyId,  
    [in] LPVOID pvProperty,  
    [in] DWORD  cbProperty  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bf62e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bf62e-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="bf62e-106">[in] Identificateur unique de la propriété dont la valeur sera définie.</span><span class="sxs-lookup"><span data-stu-id="bf62e-106">[in] The unique identifier of the property whose value will be set.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="bf62e-107">[in] La valeur à laquelle définir la propriété référencée par `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="bf62e-107">[in] The value to which to set the property referenced by `PropertyId`.</span></span>  
  
 `cbProperty`  
 <span data-ttu-id="bf62e-108">[in] La taille, en octets, de `pvProperty`.</span><span class="sxs-lookup"><span data-stu-id="bf62e-108">[in] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf62e-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bf62e-109">Requirements</span></span>  
 <span data-ttu-id="bf62e-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf62e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf62e-111">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="bf62e-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="bf62e-112">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf62e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf62e-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf62e-113">See Also</span></span>  
 [<span data-ttu-id="bf62e-114">IAssemblyName, interface</span><span class="sxs-lookup"><span data-stu-id="bf62e-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
