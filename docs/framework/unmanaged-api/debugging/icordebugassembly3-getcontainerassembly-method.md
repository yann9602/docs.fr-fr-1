---
title: "ICorDebugAssembly3::GetContainerAssembly, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f9a32520c2a67c0bc51a3f88e9822db49e4a3974
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugassembly3getcontainerassembly-method"></a><span data-ttu-id="621c7-102">ICorDebugAssembly3::GetContainerAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="621c7-102">ICorDebugAssembly3::GetContainerAssembly Method</span></span>
<span data-ttu-id="621c7-103">Retourne l'assembly conteneur de cet objet `ICorDebugAssembly3`.</span><span class="sxs-lookup"><span data-stu-id="621c7-103">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="621c7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="621c7-104">Syntax</span></span>  
  
```  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="621c7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="621c7-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="621c7-106">Un pointeur vers l’adresse d’un objet ICorDebugAssembly qui représente l’assembly conteneur, ou **null** si l’appel de méthode échoue.</span><span class="sxs-lookup"><span data-stu-id="621c7-106">A pointer to the address of an ICorDebugAssembly object that represents the container assembly, or **null** if the method call fails.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="621c7-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="621c7-107">Return Value</span></span>  
 <span data-ttu-id="621c7-108">`S_OK`Si l’appel de méthode a réussi ; dans le cas contraire, `S_FALSE`, et `ppAssembly` est **null**.</span><span class="sxs-lookup"><span data-stu-id="621c7-108">`S_OK` if the method call succeeds; otherwise, `S_FALSE`, and `ppAssembly` is **null**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="621c7-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="621c7-109">Remarks</span></span>  
 <span data-ttu-id="621c7-110">Si cet assembly a été fusionné avec d’autres assemblys dans un seul assembly conteneur, cette méthode retourne l’assembly conteneur.</span><span class="sxs-lookup"><span data-stu-id="621c7-110">If this assembly has been merged with others inside a single container assembly, this method returns the container assembly.</span></span> <span data-ttu-id="621c7-111">Pour plus d’informations et la terminologie, consultez le [ICorDebugProcess6::EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) rubrique.</span><span class="sxs-lookup"><span data-stu-id="621c7-111">For more information and terminology, see the [ICorDebugProcess6::EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="621c7-112">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="621c7-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="621c7-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="621c7-113">Requirements</span></span>  
 <span data-ttu-id="621c7-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="621c7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="621c7-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="621c7-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="621c7-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="621c7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="621c7-117">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="621c7-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="621c7-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="621c7-118">See Also</span></span>  
 [<span data-ttu-id="621c7-119">Icordebugassembly3, Interface</span><span class="sxs-lookup"><span data-stu-id="621c7-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 [<span data-ttu-id="621c7-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="621c7-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
