---
title: "ICorDebugAppDomain::Attach, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.Attach
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::Attach
helpviewer_keywords:
- ICorDebugAppDomain::Attach method [.NET Framework debugging]
- Attach method [.NET Framework debugging]
ms.assetid: 0358b84a-4236-4c34-945b-4babff7df570
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 25f6d32cc1b06615c592739ffab8a87f0fe5d5b8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomainattach-method"></a><span data-ttu-id="b921a-102">ICorDebugAppDomain::Attach, méthode</span><span class="sxs-lookup"><span data-stu-id="b921a-102">ICorDebugAppDomain::Attach Method</span></span>
<span data-ttu-id="b921a-103">Attache le débogueur au domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="b921a-103">Attaches the debugger to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b921a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b921a-104">Syntax</span></span>  
  
```  
HRESULT Attach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="b921a-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="b921a-105">Remarks</span></span>  
 <span data-ttu-id="b921a-106">Le débogueur doit être attaché au domaine d’application pour recevoir des événements et activer le débogage du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="b921a-106">The debugger must be attached to the application domain to receive events and to enable debugging of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b921a-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b921a-107">Requirements</span></span>  
 <span data-ttu-id="b921a-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b921a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b921a-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b921a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b921a-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b921a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b921a-111">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b921a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
