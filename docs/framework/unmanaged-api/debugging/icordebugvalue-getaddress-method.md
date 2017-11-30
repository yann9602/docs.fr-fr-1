---
title: "ICorDebugValue::GetAddress, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValue.GetAddress
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValue::GetAddress
helpviewer_keywords:
- ICorDebugValue::GetAddress method [.NET Framework debugging]
- GetAddress method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: a247c792-45e1-4538-9e1f-b46acca4a463
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7018dcb41f46d5407549f5c3d3029716781014e3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvaluegetaddress-method"></a><span data-ttu-id="6a9be-102">ICorDebugValue::GetAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="6a9be-102">ICorDebugValue::GetAddress Method</span></span>
<span data-ttu-id="6a9be-103">Obtient l’adresse de cet objet « ICorDebugValue », qui est en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="6a9be-103">Gets the address of this "ICorDebugValue" object, which is in the process of being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a9be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a9be-104">Syntax</span></span>  
  
```  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6a9be-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6a9be-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="6a9be-106">[out] Pointeur vers un `CORDB_ADDRESS` objet qui spécifie l’adresse de cet objet de valeur.</span><span class="sxs-lookup"><span data-stu-id="6a9be-106">[out] Pointer to a `CORDB_ADDRESS` object that specifies the address of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a9be-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="6a9be-107">Remarks</span></span>  
 <span data-ttu-id="6a9be-108">Si la valeur n’est pas disponible, 0 (zéro) est retournée.</span><span class="sxs-lookup"><span data-stu-id="6a9be-108">If the value is unavailable, 0 (zero) is returned.</span></span> <span data-ttu-id="6a9be-109">Cela peut se produire si la valeur est au moins en partie dans les registres ou stockées dans un handle de garbage collector (`GCHandle`).</span><span class="sxs-lookup"><span data-stu-id="6a9be-109">This could happen if the value is at least partly in registers or stored in a garbage collector handle (`GCHandle`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a9be-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6a9be-110">Requirements</span></span>  
 <span data-ttu-id="6a9be-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a9be-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a9be-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6a9be-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a9be-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a9be-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a9be-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a9be-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a9be-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a9be-115">See Also</span></span>  
 
