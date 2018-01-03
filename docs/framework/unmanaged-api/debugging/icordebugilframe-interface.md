---
title: ICorDebugILFrame Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame
helpviewer_keywords: ICorDebugILFrame interface [.NET Framework debugging]
ms.assetid: d5cf5056-da4d-4629-914d-afe42a5393df
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1db53f50e942e70517fc06dfd90e75d04158ea9a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe-interface1"></a><span data-ttu-id="bd14e-102">ICorDebugILFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="bd14e-102">ICorDebugILFrame Interface1</span></span>
<span data-ttu-id="bd14e-103">Représente un frame de pile de code Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="bd14e-103">Represents a stack frame of Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="bd14e-104">Cette interface est une sous-classe de l’interface ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="bd14e-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bd14e-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="bd14e-105">Methods</span></span>  
  
|<span data-ttu-id="bd14e-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="bd14e-106">Method</span></span>|<span data-ttu-id="bd14e-107">Description</span><span class="sxs-lookup"><span data-stu-id="bd14e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bd14e-108">CanSetIP, méthode</span><span class="sxs-lookup"><span data-stu-id="bd14e-108">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|<span data-ttu-id="bd14e-109">Obtient une valeur qui indique s’il est possible de définir le pointeur d’instruction à l’emplacement de décalage spécifié.</span><span class="sxs-lookup"><span data-stu-id="bd14e-109">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location.</span></span>|  
|[<span data-ttu-id="bd14e-110">EnumerateArguments, méthode</span><span class="sxs-lookup"><span data-stu-id="bd14e-110">EnumerateArguments Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|<span data-ttu-id="bd14e-111">Obtient un énumérateur pour les arguments dans ce frame.</span><span class="sxs-lookup"><span data-stu-id="bd14e-111">Gets an enumerator for the arguments in this frame.</span></span>|  
|[<span data-ttu-id="bd14e-112">EnumerateLocalVariables, méthode</span><span class="sxs-lookup"><span data-stu-id="bd14e-112">EnumerateLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|<span data-ttu-id="bd14e-113">Obtient un énumérateur pour les variables locales dans ce frame.</span><span class="sxs-lookup"><span data-stu-id="bd14e-113">Gets an enumerator for the local variables in this frame.</span></span>|  
|[<span data-ttu-id="bd14e-114">GetArgument, méthode</span><span class="sxs-lookup"><span data-stu-id="bd14e-114">GetArgument Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|<span data-ttu-id="bd14e-115">Obtient la valeur de l’argument spécifié dans ce frame de pile MSIL.</span><span class="sxs-lookup"><span data-stu-id="bd14e-115">Gets the value of the specified argument in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="bd14e-116">GetIP, méthode</span><span class="sxs-lookup"><span data-stu-id="bd14e-116">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|<span data-ttu-id="bd14e-117">Obtient la valeur du pointeur d’instruction et une valeur de la combinaison de bits qui décrit la façon dont la valeur du pointeur d’instruction a été obtenue.</span><span class="sxs-lookup"><span data-stu-id="bd14e-117">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>|  
|[<span data-ttu-id="bd14e-118">GetLocalVariable, méthode</span><span class="sxs-lookup"><span data-stu-id="bd14e-118">GetLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|<span data-ttu-id="bd14e-119">Obtient la valeur de la variable locale spécifiée dans ce frame de pile MSIL.</span><span class="sxs-lookup"><span data-stu-id="bd14e-119">Gets the value of the specified local variable in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="bd14e-120">GetStackDepth, méthode</span><span class="sxs-lookup"><span data-stu-id="bd14e-120">GetStackDepth Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|<span data-ttu-id="bd14e-121">Non implémenté.</span><span class="sxs-lookup"><span data-stu-id="bd14e-121">Not implemented.</span></span>|  
|[<span data-ttu-id="bd14e-122">GetStackValue, méthode</span><span class="sxs-lookup"><span data-stu-id="bd14e-122">GetStackValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|<span data-ttu-id="bd14e-123">Non implémenté.</span><span class="sxs-lookup"><span data-stu-id="bd14e-123">Not implemented.</span></span>|  
|[<span data-ttu-id="bd14e-124">SetIP, méthode</span><span class="sxs-lookup"><span data-stu-id="bd14e-124">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|<span data-ttu-id="bd14e-125">Définit le pointeur d’instruction à l’emplacement de décalage spécifié dans le code MSIL.</span><span class="sxs-lookup"><span data-stu-id="bd14e-125">Sets the instruction pointer to the specified offset location in the MSIL code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd14e-126">Notes</span><span class="sxs-lookup"><span data-stu-id="bd14e-126">Remarks</span></span>  
 <span data-ttu-id="bd14e-127">Le `ICorDebugILFrame` interface est une interface ICorDebugFrame spécialisée.</span><span class="sxs-lookup"><span data-stu-id="bd14e-127">The `ICorDebugILFrame` interface is a specialized ICorDebugFrame interface.</span></span> <span data-ttu-id="bd14e-128">Il est utilisé pour les frames de code MSIL ou juste-à-temps (JIT) frames compilés.</span><span class="sxs-lookup"><span data-stu-id="bd14e-128">It is used either for MSIL code frames or for just-in-time (JIT) compiled frames.</span></span> <span data-ttu-id="bd14e-129">Les frames compilés JIT implémentent la `ICorDebugILFrame` interface et l’interface ICorDebugNativeFrame.</span><span class="sxs-lookup"><span data-stu-id="bd14e-129">The JIT-compiled frames implement both the `ICorDebugILFrame` interface and the ICorDebugNativeFrame interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd14e-130">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="bd14e-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd14e-131">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bd14e-131">Requirements</span></span>  
 <span data-ttu-id="bd14e-132">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd14e-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd14e-133">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bd14e-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd14e-134">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd14e-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd14e-135">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd14e-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd14e-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd14e-136">See Also</span></span>  
 [<span data-ttu-id="bd14e-137">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="bd14e-137">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
