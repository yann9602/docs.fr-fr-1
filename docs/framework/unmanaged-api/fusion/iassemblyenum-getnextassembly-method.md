---
title: "IAssemblyEnum::GetNextAssembly, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyEnum.GetNextAssembly
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyEnum::GetNextAssembly
helpviewer_keywords:
- GetNextAssembly method [.NET Framework fusion]
- IAssemblyEnum::GetNextAssembly method [.NET Framework fusion]
ms.assetid: 5d7a4ca2-5f46-4ef1-a9a2-257884e9dc11
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2666970e220334e9e8c2470622026442db0c2f95
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblyenumgetnextassembly-method"></a><span data-ttu-id="89251-102">IAssemblyEnum::GetNextAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="89251-102">IAssemblyEnum::GetNextAssembly Method</span></span>
<span data-ttu-id="89251-103">Obtient un pointeur vers la prochaine [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) contenus dans ce [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) objet.</span><span class="sxs-lookup"><span data-stu-id="89251-103">Gets a pointer to the next [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) contained in this [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89251-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89251-104">Syntax</span></span>  
  
```  
HRESULT GetNextAssembly (  
    [in]  LPVOID          pvReserved,  
    [out] IAssemblyName   **ppName,  
    [in]  DWORD           dwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="89251-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="89251-105">Parameters</span></span>  
 `pvReserved`  
 <span data-ttu-id="89251-106">[in] Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="89251-106">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="89251-107">`pvReserved`doit être une référence null.</span><span class="sxs-lookup"><span data-stu-id="89251-107">`pvReserved` must be a null reference.</span></span>  
  
 `ppName`  
 <span data-ttu-id="89251-108">[out] Retourné `IAssemblyName` pointeur.</span><span class="sxs-lookup"><span data-stu-id="89251-108">[out] The returned `IAssemblyName` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="89251-109">[in] Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="89251-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="89251-110">`dwFlags`doit être 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="89251-110">`dwFlags` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89251-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="89251-111">Requirements</span></span>  
 <span data-ttu-id="89251-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89251-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89251-113">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="89251-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="89251-114">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89251-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89251-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89251-115">See Also</span></span>  
 [<span data-ttu-id="89251-116">IAssemblyName, interface</span><span class="sxs-lookup"><span data-stu-id="89251-116">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="89251-117">IAssemblyEnum, interface</span><span class="sxs-lookup"><span data-stu-id="89251-117">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
