---
title: ICorDebugModule2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule2
helpviewer_keywords: ICorDebugModule2 interface [.NET Framework debugging]
ms.assetid: 0847e64f-fdbe-4c96-8168-da20fdc84d80
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 97259783d34babe3f0f229f5d62b3e945c0ac624
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodule2-interface1"></a><span data-ttu-id="ce196-102">ICorDebugModule2 Interface1</span><span class="sxs-lookup"><span data-stu-id="ce196-102">ICorDebugModule2 Interface1</span></span>
<span data-ttu-id="ce196-103">Sert d’extension logique à l’interface ICorDebugModule.</span><span class="sxs-lookup"><span data-stu-id="ce196-103">Serves as a logical extension to the ICorDebugModule interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ce196-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ce196-104">Methods</span></span>  
  
|<span data-ttu-id="ce196-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="ce196-105">Method</span></span>|<span data-ttu-id="ce196-106">Description</span><span class="sxs-lookup"><span data-stu-id="ce196-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ce196-107">ApplyChanges (méthode)</span><span class="sxs-lookup"><span data-stu-id="ce196-107">ApplyChanges Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)|<span data-ttu-id="ce196-108">Applique les modifications dans les métadonnées et les modifications dans le code MSIL (intermediate language) de Microsoft pour le processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="ce196-108">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>|  
|[<span data-ttu-id="ce196-109">GetJITCompilerFlags (méthode)</span><span class="sxs-lookup"><span data-stu-id="ce196-109">GetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-getjitcompilerflags-method.md)|<span data-ttu-id="ce196-110">Obtient les indicateurs qui contrôlent la compilation juste-à-temps (JIT) pour ce `ICorDebugModule2`.</span><span class="sxs-lookup"><span data-stu-id="ce196-110">Gets the flags that control the just-in-time (JIT) compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="ce196-111">ResolveAssembly (méthode)</span><span class="sxs-lookup"><span data-stu-id="ce196-111">ResolveAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-resolveassembly-method.md)|<span data-ttu-id="ce196-112">Résout l’assembly référencé par le jeton de métadonnées spécifié.</span><span class="sxs-lookup"><span data-stu-id="ce196-112">Resolves the assembly referenced by the specified metadata token.</span></span>|  
|[<span data-ttu-id="ce196-113">SetJITCompilerFlags (méthode)</span><span class="sxs-lookup"><span data-stu-id="ce196-113">SetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)|<span data-ttu-id="ce196-114">Définit les indicateurs qui contrôlent la compilation JIT pour cet `ICorDebugModule2`.</span><span class="sxs-lookup"><span data-stu-id="ce196-114">Sets the flags that control the JIT compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="ce196-115">SetJMCStatus, méthode</span><span class="sxs-lookup"><span data-stu-id="ce196-115">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjmcstatus-method.md)|<span data-ttu-id="ce196-116">Définit l’état uniquement mon Code (JMC) de toutes les méthodes de toutes les classes dans ce `ICorDebugModule2` à la valeur spécifiée, à l’exception de celles figurant dans le `pTokens` tableau, il définit la valeur opposée.</span><span class="sxs-lookup"><span data-stu-id="ce196-116">Sets the Just My Code (JMC) status of all methods of all the classes in this `ICorDebugModule2` to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce196-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="ce196-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce196-118">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="ce196-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce196-119">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ce196-119">Requirements</span></span>  
 <span data-ttu-id="ce196-120">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce196-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce196-121">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ce196-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce196-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce196-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce196-123">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce196-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce196-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce196-124">See Also</span></span>  
 [<span data-ttu-id="ce196-125">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="ce196-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
