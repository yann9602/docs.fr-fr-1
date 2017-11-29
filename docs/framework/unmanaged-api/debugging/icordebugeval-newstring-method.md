---
title: "ICorDebugEval::NewString, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.NewString
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::NewString
helpviewer_keywords:
- NewString method [.NET Framework debugging]
- ICorDebugEval::NewString method [.NET Framework debugging]
ms.assetid: 29e7a14b-d50e-4852-bfda-011b76c0c9ee
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 48c1a36e32feb94e8399c46f88a98f75c81fdb6a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugevalnewstring-method"></a><span data-ttu-id="f7679-102">ICorDebugEval::NewString, méthode</span><span class="sxs-lookup"><span data-stu-id="f7679-102">ICorDebugEval::NewString Method</span></span>
<span data-ttu-id="f7679-103">Alloue une nouvelle instance de chaîne avec le contenu spécifié.</span><span class="sxs-lookup"><span data-stu-id="f7679-103">Allocates a new string instance with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7679-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7679-104">Syntax</span></span>  
  
```  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f7679-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f7679-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="f7679-106">[in] Pointeur vers le contenu de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="f7679-106">[in] Pointer to the contents for the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7679-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="f7679-107">Remarks</span></span>  
 <span data-ttu-id="f7679-108">La chaîne est toujours créée dans le domaine d’application dans lequel le thread est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="f7679-108">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7679-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f7679-109">Requirements</span></span>  
 <span data-ttu-id="f7679-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7679-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7679-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7679-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7679-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7679-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7679-113">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7679-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
