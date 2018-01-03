---
title: "ICorDebugILFrame3::GetReturnValueForILOffset, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- csharp
- vb
api_name: ICorDebugILFrame3.GetReturnValueForILOffset
api_location: mscordbi.dll
api_type: COM
ms.assetid: 06522727-5f64-4391-9331-11386883c352
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c58319de99bdd8d7cce0ea55ccb3140a31a39bd0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a><span data-ttu-id="633e1-102">ICorDebugILFrame3::GetReturnValueForILOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="633e1-102">ICorDebugILFrame3::GetReturnValueForILOffset Method</span></span>
<span data-ttu-id="633e1-103">Obtient un objet « ICorDebugValue » qui encapsule la valeur de retour d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="633e1-103">Gets an "ICorDebugValue" object that encapsulates the return value of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="633e1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="633e1-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,   
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="633e1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="633e1-105">Parameters</span></span>  
 `ILOffset`  
 <span data-ttu-id="633e1-106">Offset IL.</span><span class="sxs-lookup"><span data-stu-id="633e1-106">The IL offset.</span></span> <span data-ttu-id="633e1-107">Consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="633e1-107">See the Remarks section.</span></span>  
  
 `ppReturnValue`  
 <span data-ttu-id="633e1-108">Pointeur vers l’adresse d’un objet d’interface « ICorDebugValue » qui fournit des informations sur la valeur de retour d’un appel de fonction.</span><span class="sxs-lookup"><span data-stu-id="633e1-108">A pointer to the address of an "ICorDebugValue" interface object that provides information about the return value of a function call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="633e1-109">Notes</span><span class="sxs-lookup"><span data-stu-id="633e1-109">Remarks</span></span>  
 <span data-ttu-id="633e1-110">Cette méthode est utilisée avec la [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) méthode pour obtenir la valeur de retour d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="633e1-110">This method is used along with the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method to get the return value of a method.</span></span> <span data-ttu-id="633e1-111">Il est particulièrement utile dans le cas des méthodes dont les valeurs de retournés sont ignorées, comme dans les exemples de deux fichiers de code suivant.</span><span class="sxs-lookup"><span data-stu-id="633e1-111">It is particularly useful in the case of methods whose return values are ignored, as in the following two code examples.</span></span> <span data-ttu-id="633e1-112">Le premier exemple appelle la <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> (méthode), mais ignore la valeur de retour de la méthode.</span><span class="sxs-lookup"><span data-stu-id="633e1-112">The first example calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method, but ignores the method's return value.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 <span data-ttu-id="633e1-113">Le deuxième exemple illustre un problème beaucoup plus courant dans le débogage.</span><span class="sxs-lookup"><span data-stu-id="633e1-113">The second example illustrates a much more common problem in debugging.</span></span> <span data-ttu-id="633e1-114">Car une méthode est utilisée en tant qu’argument dans un appel de méthode, sa valeur de retour est accessible uniquement lorsque le débogueur parcourt la méthode appelée.</span><span class="sxs-lookup"><span data-stu-id="633e1-114">Because a method is used as an argument in a method call, its return value is accessible only when the debugger steps through the called method.</span></span> <span data-ttu-id="633e1-115">Dans de nombreux cas, en particulier lorsque la méthode appelée est définie dans une bibliothèque externe, qui n’est pas possible.</span><span class="sxs-lookup"><span data-stu-id="633e1-115">In many cases, particularly when the called method is defined in an external library, that is not possible.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 <span data-ttu-id="633e1-116">Si vous passez le [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) méthode un offset à un site d’appel de fonction IL, elle retourne un ou plusieurs des offsets natifs.</span><span class="sxs-lookup"><span data-stu-id="633e1-116">If you pass the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method an IL offset to a function call site, it returns one or more native offsets.</span></span> <span data-ttu-id="633e1-117">Le débogueur peut ensuite définir des points d’arrêt sur ces offsets natifs dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="633e1-117">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="633e1-118">Lorsque le débogueur atteint un des points d’arrêt, vous pouvez ensuite passer le même offset IL que vous avez passé à cette méthode pour obtenir la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="633e1-118">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to get the return value.</span></span> <span data-ttu-id="633e1-119">Le débogueur doit puis désactivez tous les points d’arrêt qu’il.</span><span class="sxs-lookup"><span data-stu-id="633e1-119">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="633e1-120">Le [icordebugcode3::getreturnvalueliveoffset, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) et `ICorDebugILFrame3::GetReturnValueForILOffset` méthodes permettent d’obtenir des informations de valeur de retour pour les types de référence uniquement.</span><span class="sxs-lookup"><span data-stu-id="633e1-120">The [ICorDebugCode3::GetReturnValueLiveOffset Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) and `ICorDebugILFrame3::GetReturnValueForILOffset` methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="633e1-121">Récupération des informations de valeur de retour dans les types valeur (autrement dit, tous les types qui dérivent de <xref:System.ValueType>) n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="633e1-121">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="633e1-122">Offset IL spécifié par le `ILOffset` le paramètre doit être sur un site d’appel de fonction, et le programme débogué doit être arrêté à un point d’arrêt défini à l’offset natif retourné par le [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) (méthode) pour le même offset IL.</span><span class="sxs-lookup"><span data-stu-id="633e1-122">The IL offset specified by the `ILOffset` parameter should be at a function call site, and the debuggee should be stopped at a breakpoint set at the native offset returned by the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method for the same IL offset.</span></span> <span data-ttu-id="633e1-123">Si le programme débogué n’est pas arrêté à l’emplacement correct pour l’offset IL spécifié, l’API échoue.</span><span class="sxs-lookup"><span data-stu-id="633e1-123">If the debuggee is not stopped at the correct location for the specified IL offset, the API will fail.</span></span>  
  
 <span data-ttu-id="633e1-124">Si l’appel de fonction ne retourne aucune valeur, l’API échoue.</span><span class="sxs-lookup"><span data-stu-id="633e1-124">If the function call doesn't return a value, the API will fail.</span></span>  
  
 <span data-ttu-id="633e1-125">Le `ICorDebugILFrame3::GetReturnValueForILOffset` méthode est disponible uniquement sur x86 et les systèmes AMD64.</span><span class="sxs-lookup"><span data-stu-id="633e1-125">The `ICorDebugILFrame3::GetReturnValueForILOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="633e1-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="633e1-126">Requirements</span></span>  
 <span data-ttu-id="633e1-127">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="633e1-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="633e1-128">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="633e1-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="633e1-129">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="633e1-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="633e1-130">**Versions du .NET framework :**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="633e1-130">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="633e1-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="633e1-131">See Also</span></span>  
 [<span data-ttu-id="633e1-132">GetReturnValueLiveOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="633e1-132">GetReturnValueLiveOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)  
 [<span data-ttu-id="633e1-133">ICorDebugILFrame3, interface</span><span class="sxs-lookup"><span data-stu-id="633e1-133">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
