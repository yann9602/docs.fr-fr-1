---
title: "ICorDebugProcess6::MarkDebuggerAttached, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f6d219e298e04157ea0670681c7550bd920bd284
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess6markdebuggerattached-method"></a><span data-ttu-id="595d4-102">ICorDebugProcess6::MarkDebuggerAttached, méthode</span><span class="sxs-lookup"><span data-stu-id="595d4-102">ICorDebugProcess6::MarkDebuggerAttached Method</span></span>
<span data-ttu-id="595d4-103">Change l'état interne du programme débogué pour que la méthode <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> de la bibliothèque de classes du .NET Framework retourne `true`.</span><span class="sxs-lookup"><span data-stu-id="595d4-103">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="595d4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="595d4-104">Syntax</span></span>  
  
```  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="595d4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="595d4-105">Parameters</span></span>  
 `fIsAttached`  
 <span data-ttu-id="595d4-106">`true` si la méthode <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> doit indiquer qu'un débogueur est attaché ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="595d4-106">`true` if the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method should indicate that a debugger is attached; `false` otherwise.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="595d4-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="595d4-107">Return Value</span></span>  
 <span data-ttu-id="595d4-108">La méthode peut retourner les valeurs répertoriées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="595d4-108">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="595d4-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="595d4-109">Return value</span></span>|<span data-ttu-id="595d4-110">Description</span><span class="sxs-lookup"><span data-stu-id="595d4-110">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="595d4-111">Le programme débogué a été mis à jour.</span><span class="sxs-lookup"><span data-stu-id="595d4-111">The debuggee was successfully updated.</span></span>|  
|`CORDBG_E_MODULE_NOT_LOADED`|<span data-ttu-id="595d4-112">L'assembly contenant la méthode <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> n'est pas chargé ou il n'a pas pu être reconnu à cause d'une autre erreur (par exemple, métadonnées manquantes).</span><span class="sxs-lookup"><span data-stu-id="595d4-112">The assembly that contains the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method is not loaded, or some other error, such as missing metadata, is preventing it from being recognized.</span></span><br /><br /> <span data-ttu-id="595d4-113">Cette erreur courante est sans gravité.</span><span class="sxs-lookup"><span data-stu-id="595d4-113">This error is common and benign.</span></span> <span data-ttu-id="595d4-114">Rappelez la méthode lors du chargement des assemblys supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="595d4-114">You should call the method again when additional assemblies load.</span></span>|  
|<span data-ttu-id="595d4-115">Autres valeurs `HRESULT` indiquant un échec.</span><span class="sxs-lookup"><span data-stu-id="595d4-115">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="595d4-116">Autres valeurs susceptibles d'indiquer un dysfonctionnement des composants du débogueur ou du compilateur.</span><span class="sxs-lookup"><span data-stu-id="595d4-116">Other values likely indicate misbehaving debugger or compiler components.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="595d4-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="595d4-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="595d4-118">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="595d4-118">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="595d4-119">Spécifications</span><span class="sxs-lookup"><span data-stu-id="595d4-119">Requirements</span></span>  
 <span data-ttu-id="595d4-120">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="595d4-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="595d4-121">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="595d4-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="595d4-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="595d4-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="595d4-123">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="595d4-123">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="595d4-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="595d4-124">See Also</span></span>  
 [<span data-ttu-id="595d4-125">Icordebugprocess6, Interface</span><span class="sxs-lookup"><span data-stu-id="595d4-125">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="595d4-126">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="595d4-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
