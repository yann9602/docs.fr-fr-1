---
title: "ICorDebugCode::CreateBreakpoint, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode.CreateBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode::CreateBreakpoint
helpviewer_keywords:
- ICorDebugCode::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 46842618-0fe4-480b-871c-82fba82d23d9
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 214d032129613230b8c55cdd286ea637227a626e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcodecreatebreakpoint-method"></a><span data-ttu-id="9b53a-102">ICorDebugCode::CreateBreakpoint, méthode</span><span class="sxs-lookup"><span data-stu-id="9b53a-102">ICorDebugCode::CreateBreakpoint Method</span></span>
<span data-ttu-id="9b53a-103">Crée un point d’arrêt dans ce segment de code à l’offset spécifié.</span><span class="sxs-lookup"><span data-stu-id="9b53a-103">Creates a breakpoint in this code segment at the specified offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b53a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b53a-104">Syntax</span></span>  
  
```  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9b53a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9b53a-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="9b53a-106">[in] Le décalage à partir duquel créer le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="9b53a-106">[in] The offset at which to create the breakpoint.</span></span>  
  
 `ppBreakpoint`  
 <span data-ttu-id="9b53a-107">[out] Pointeur vers l’adresse d’un objet « ICorDebugFunctionBreakpoint » qui représente le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="9b53a-107">[out] A pointer to the address of an "ICorDebugFunctionBreakpoint" object that represents the breakpoint.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b53a-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="9b53a-108">Remarks</span></span>  
 <span data-ttu-id="9b53a-109">Avant le point d’arrêt est actif, il doit être ajouté à l’objet de processus.</span><span class="sxs-lookup"><span data-stu-id="9b53a-109">Before the breakpoint is active, it must be added to the process object.</span></span>  
  
 <span data-ttu-id="9b53a-110">Si ce code est le code Microsoft intermediate language (MSIL), et il existe un juste-à-temps (JIT)-version native compilée du code, le point d’arrêt sera appliquée dans le code compilé par JIT.</span><span class="sxs-lookup"><span data-stu-id="9b53a-110">If this code is Microsoft intermediate language (MSIL) code, and there is a just-in-time (JIT)-compiled, native version of the code, the breakpoint will be applied in the JIT-compiled code as well.</span></span> <span data-ttu-id="9b53a-111">(Le même a la valeur true si le code est compilé par JIT ultérieurement.)</span><span class="sxs-lookup"><span data-stu-id="9b53a-111">(The same is true if the code is JIT-compiled later.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b53a-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9b53a-112">Requirements</span></span>  
 <span data-ttu-id="9b53a-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b53a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b53a-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b53a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b53a-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b53a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b53a-116">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b53a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b53a-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b53a-117">See Also</span></span>  
 
