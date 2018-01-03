---
title: "ICorDebugReferenceValue::Dereference, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugReferenceValue.Dereference
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugReferenceValue::Dereference
helpviewer_keywords:
- ICorDebugReferenceValue::Dereference method [.NET Framework debugging]
- Dereference method [.NET Framework debugging]
ms.assetid: 5ec8cf76-3deb-4ce6-9a49-77a4c35d80b9
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0dbf2775217a78c1cbb9a96093354f0fc0b278bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugreferencevaluedereference-method"></a><span data-ttu-id="2a942-102">ICorDebugReferenceValue::Dereference, méthode</span><span class="sxs-lookup"><span data-stu-id="2a942-102">ICorDebugReferenceValue::Dereference Method</span></span>
<span data-ttu-id="2a942-103">Obtient l’objet qui est référencé.</span><span class="sxs-lookup"><span data-stu-id="2a942-103">Gets the object that is referenced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a942-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2a942-104">Syntax</span></span>  
  
```  
HRESULT Dereference (  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2a942-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2a942-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="2a942-106">[out] Pointeur vers l’adresse d’un ICorDebugValue qui représente l’objet vers lequel pointe cet objet ICorDebugReferenceValue.</span><span class="sxs-lookup"><span data-stu-id="2a942-106">[out] A pointer to the address of an ICorDebugValue that represents the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a942-107">Notes</span><span class="sxs-lookup"><span data-stu-id="2a942-107">Remarks</span></span>  
 <span data-ttu-id="2a942-108">Le `ICorDebugValue` objet est valide uniquement lors de sa référence n’a pas été désactivé.</span><span class="sxs-lookup"><span data-stu-id="2a942-108">The `ICorDebugValue` object is valid only while its reference has not yet been disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a942-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2a942-109">Requirements</span></span>  
 <span data-ttu-id="2a942-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a942-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a942-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2a942-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a942-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a942-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a942-113">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a942-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
