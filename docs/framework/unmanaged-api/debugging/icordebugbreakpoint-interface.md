---
title: ICorDebugBreakpoint Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugBreakpoint
helpviewer_keywords: ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: aa5ad3d7-e1bb-42af-99bc-471224e3bcaa
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b78b61b99fb8f236e787f3acbf993d0a1c57e797
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugbreakpoint-interface1"></a><span data-ttu-id="69120-102">ICorDebugBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="69120-102">ICorDebugBreakpoint Interface1</span></span>
<span data-ttu-id="69120-103">Représente un point d’arrêt dans une fonction ou un point de contrôle sur une valeur.</span><span class="sxs-lookup"><span data-stu-id="69120-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="69120-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="69120-104">Methods</span></span>  
  
|<span data-ttu-id="69120-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="69120-105">Method</span></span>|<span data-ttu-id="69120-106">Description</span><span class="sxs-lookup"><span data-stu-id="69120-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="69120-107">Activate (méthode)</span><span class="sxs-lookup"><span data-stu-id="69120-107">Activate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|<span data-ttu-id="69120-108">Définit l’état actif de ce `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="69120-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="69120-109">IsActive (méthode)</span><span class="sxs-lookup"><span data-stu-id="69120-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="69120-110">Obtient une valeur qui indique si cette `ICorDebugBreakpoint` est actif.</span><span class="sxs-lookup"><span data-stu-id="69120-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69120-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="69120-111">Remarks</span></span>  
 <span data-ttu-id="69120-112">Points d’arrêt ne prennent pas directement en charge les expressions conditionnelles.</span><span class="sxs-lookup"><span data-stu-id="69120-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="69120-113">Si cette fonctionnalité est souhaitée, un débogueur doit implémenter sur `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="69120-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="69120-114">L’interface ICorDebugFunctionBreakpoint étend `ICorDebugBreakpoint` pour prendre en charge les points d’arrêt dans les fonctions.</span><span class="sxs-lookup"><span data-stu-id="69120-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69120-115">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="69120-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69120-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="69120-116">Requirements</span></span>  
 <span data-ttu-id="69120-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69120-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69120-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69120-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69120-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69120-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69120-120">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69120-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69120-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69120-121">See Also</span></span>  
 [<span data-ttu-id="69120-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="69120-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
