---
title: "ICorDebugAppDomain::IsAttached, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.IsAttached
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::IsAttached
helpviewer_keywords:
- IsAttached method [.NET Framework debugging]
- ICorDebugAppDomain::IsAttached method [.NET Framework debugging]
ms.assetid: af0c67c7-f53e-47c9-b84b-be50bd04903e
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2a85b674ad705f77e00cf2a8a5286d6a74f7a646
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomainisattached-method"></a><span data-ttu-id="69d61-102">ICorDebugAppDomain::IsAttached, méthode</span><span class="sxs-lookup"><span data-stu-id="69d61-102">ICorDebugAppDomain::IsAttached Method</span></span>
<span data-ttu-id="69d61-103">Obtient une valeur qui indique si le débogueur est attaché au domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="69d61-103">Gets a value that indicates whether the debugger is attached to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69d61-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69d61-104">Syntax</span></span>  
  
```  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="69d61-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="69d61-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="69d61-106">[out] `true` si le débogueur est attaché au domaine d’application ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="69d61-106">[out] `true` if the debugger is attached to the application domain; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69d61-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="69d61-107">Remarks</span></span>  
 <span data-ttu-id="69d61-108">Les méthodes ICorDebugController ne peut pas être utilisés tant que le débogueur s’attache au domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="69d61-108">The ICorDebugController methods cannot be used until the debugger attaches to the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69d61-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="69d61-109">Requirements</span></span>  
 <span data-ttu-id="69d61-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69d61-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69d61-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69d61-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69d61-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69d61-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69d61-113">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69d61-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
