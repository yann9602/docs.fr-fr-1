---
title: ICorDebugReferenceValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugReferenceValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugReferenceValue
helpviewer_keywords: ICorDebugReferenceValue interface [.NET Framework debugging]
ms.assetid: 2040e2be-119a-4cfb-ae52-b0b6f052665c
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d11cb4cbd6baa1e0d381c9fb11d5a3343287cf55
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugreferencevalue-interface1"></a><span data-ttu-id="c7b97-102">ICorDebugReferenceValue Interface1</span><span class="sxs-lookup"><span data-stu-id="c7b97-102">ICorDebugReferenceValue Interface1</span></span>
<span data-ttu-id="c7b97-103">Fournit des méthodes qui gèrent une valeur qui est une référence à un objet.</span><span class="sxs-lookup"><span data-stu-id="c7b97-103">Provides methods that manage a value that is a reference to an object.</span></span> <span data-ttu-id="c7b97-104">(Autrement dit, cette interface fournit des méthodes qui gèrent un pointeur.) Cette interface implémente « ICorDebugValue ».</span><span class="sxs-lookup"><span data-stu-id="c7b97-104">(That is, this interface provides methods that manage a pointer.) This interface implements "ICorDebugValue".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c7b97-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="c7b97-105">Methods</span></span>  
  
|<span data-ttu-id="c7b97-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="c7b97-106">Method</span></span>|<span data-ttu-id="c7b97-107">Description</span><span class="sxs-lookup"><span data-stu-id="c7b97-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c7b97-108">Dereference, méthode</span><span class="sxs-lookup"><span data-stu-id="c7b97-108">Dereference Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|<span data-ttu-id="c7b97-109">Obtient l’objet qui est référencé.</span><span class="sxs-lookup"><span data-stu-id="c7b97-109">Gets the object that is referenced.</span></span>|  
|[<span data-ttu-id="c7b97-110">DereferenceStrong (méthode)</span><span class="sxs-lookup"><span data-stu-id="c7b97-110">DereferenceStrong Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|<span data-ttu-id="c7b97-111">Non implémenté.</span><span class="sxs-lookup"><span data-stu-id="c7b97-111">Not implemented.</span></span> <span data-ttu-id="c7b97-112">N’appelez pas cette méthode.</span><span class="sxs-lookup"><span data-stu-id="c7b97-112">Do not call this method.</span></span>|  
|[<span data-ttu-id="c7b97-113">GetValue (méthode)</span><span class="sxs-lookup"><span data-stu-id="c7b97-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|<span data-ttu-id="c7b97-114">Obtient l’adresse mémoire actuelle de l’objet référencé.</span><span class="sxs-lookup"><span data-stu-id="c7b97-114">Gets the current memory address of the referenced object.</span></span>|  
|[<span data-ttu-id="c7b97-115">IsNull (méthode)</span><span class="sxs-lookup"><span data-stu-id="c7b97-115">IsNull Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|<span data-ttu-id="c7b97-116">Obtient une valeur qui indique si cette `ICorDebugReferenceValue` est une valeur null, auquel cas le `ICorDebugReferenceValue` ne pointe pas vers un objet.</span><span class="sxs-lookup"><span data-stu-id="c7b97-116">Gets a value that indicates whether this `ICorDebugReferenceValue` is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>|  
|[<span data-ttu-id="c7b97-117">SetValue (méthode)</span><span class="sxs-lookup"><span data-stu-id="c7b97-117">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|<span data-ttu-id="c7b97-118">Définit l’adresse mémoire actuelle.</span><span class="sxs-lookup"><span data-stu-id="c7b97-118">Sets the current memory address.</span></span> <span data-ttu-id="c7b97-119">Autrement dit, cette méthode définit `ICorDebugReferenceValue` pour pointer vers un objet.</span><span class="sxs-lookup"><span data-stu-id="c7b97-119">That is, this method sets this `ICorDebugReferenceValue` to point to an object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7b97-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="c7b97-120">Remarks</span></span>  
 <span data-ttu-id="c7b97-121">Le common language runtime (CLR) peut effectuer un garbage collection sur les objets lors de la poursuite du processus débogué.</span><span class="sxs-lookup"><span data-stu-id="c7b97-121">The common language runtime (CLR) may do a garbage collection on objects when the debugged process is continued.</span></span> <span data-ttu-id="c7b97-122">Le garbage collection peut déplacer les objets en mémoire.</span><span class="sxs-lookup"><span data-stu-id="c7b97-122">The garbage collection may move objects around in memory.</span></span> <span data-ttu-id="c7b97-123">Un `ICorDebugReferenceValue` sera soit coopérer avec le garbage collection afin que ses informations sont mis à jour après le garbage collection, ou sera invalidé implicitement avant le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="c7b97-123">An `ICorDebugReferenceValue` will either cooperate with the garbage collection so that its information is updated after the garbage collection, or it will be invalidated implicitly before the garbage collection.</span></span>  
  
 <span data-ttu-id="c7b97-124">Le `ICorDebugReferenceValue` objet peut être invalidé implicitement après la poursuite du processus débogué.</span><span class="sxs-lookup"><span data-stu-id="c7b97-124">The `ICorDebugReferenceValue` object may be implicitly invalidated after the debugged process has been continued.</span></span> <span data-ttu-id="c7b97-125">Le « ICorDebugHandleValue « dérivé n’est pas invalidé jusqu'à ce qu’elle est explicitement libéré ou exposé.</span><span class="sxs-lookup"><span data-stu-id="c7b97-125">The derived "ICorDebugHandleValue" is not invalidated until it is explicitly released or exposed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7b97-126">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="c7b97-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7b97-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c7b97-127">Requirements</span></span>  
 <span data-ttu-id="c7b97-128">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7b97-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7b97-129">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c7b97-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7b97-130">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7b97-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7b97-131">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7b97-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7b97-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7b97-132">See Also</span></span>  
    
    
 [<span data-ttu-id="c7b97-133">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="c7b97-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
