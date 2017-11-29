---
title: "ICorDebug::Initialize, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.Initialize
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::Initialize
helpviewer_keywords:
- Initialize method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Initialize method [.NET Framework debugging]
ms.assetid: 6fae3b23-5c9f-47c0-85d8-6bb75e050786
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 12665472b201e6d89be9c5cc6c78b82de067d6a6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="4e5b2-102">ICorDebug::Initialize, méthode</span><span class="sxs-lookup"><span data-stu-id="4e5b2-102">ICorDebug::Initialize Method</span></span>
<span data-ttu-id="4e5b2-103">Initialise le `ICorDebug` objet.</span><span class="sxs-lookup"><span data-stu-id="4e5b2-103">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e5b2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e5b2-104">Syntax</span></span>  
  
```  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="4e5b2-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="4e5b2-105">Remarks</span></span>  
 <span data-ttu-id="4e5b2-106">Le débogueur doit appeler `Initialize` lors de la création de services moment pour initialiser le débogage.</span><span class="sxs-lookup"><span data-stu-id="4e5b2-106">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="4e5b2-107">Cette méthode doit être appelée avant toute autre méthode sur `ICorDebug` est appelée.</span><span class="sxs-lookup"><span data-stu-id="4e5b2-107">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e5b2-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4e5b2-108">Requirements</span></span>  
 <span data-ttu-id="4e5b2-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e5b2-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e5b2-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4e5b2-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e5b2-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e5b2-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e5b2-112">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e5b2-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e5b2-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e5b2-113">See Also</span></span>  
 [<span data-ttu-id="4e5b2-114">ICorDebug (Interface)</span><span class="sxs-lookup"><span data-stu-id="4e5b2-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
