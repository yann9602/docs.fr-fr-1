---
title: "ICorDebugAssembly3::EnumerateContainedAssemblies, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b927d065f26a13d496aec8cd6c8cbc69cf3a8bc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a><span data-ttu-id="fd094-102">ICorDebugAssembly3::EnumerateContainedAssemblies, méthode</span><span class="sxs-lookup"><span data-stu-id="fd094-102">ICorDebugAssembly3::EnumerateContainedAssemblies Method</span></span>
<span data-ttu-id="fd094-103">Obtient un énumérateur pour les assemblys contenus dans cet assembly.</span><span class="sxs-lookup"><span data-stu-id="fd094-103">Gets an enumerator for the assemblies contained in this assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd094-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd094-104">Syntax</span></span>  
  
```  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fd094-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fd094-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="fd094-106">[out] Pointeur vers l’adresse d’un objet d’interface ICorDebugAssemblyEnum qui est l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="fd094-106">[out] A pointer to the address of an ICorDebugAssemblyEnum interface object that is the enumerator.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fd094-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="fd094-107">Return Value</span></span>  
 <span data-ttu-id="fd094-108">`S_OK` si cet objet `ICorDebugAssembly3` est un conteneur ; sinon, `S_FALSE`, et l'énumération est vide.</span><span class="sxs-lookup"><span data-stu-id="fd094-108">`S_OK` if this `ICorDebugAssembly3` object is a container; otherwise, `S_FALSE`, and the enumeration is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd094-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="fd094-109">Remarks</span></span>  
 <span data-ttu-id="fd094-110">Des symboles doivent être utilisés pour énumérer les assemblys contenus dans l'assembly.</span><span class="sxs-lookup"><span data-stu-id="fd094-110">Symbols are needed to enumerate the contained assemblies.</span></span> <span data-ttu-id="fd094-111">S'ils ne sont pas présents, la méthode retourne `S_FALSE`, et aucun énumérateur valide n'est fourni.</span><span class="sxs-lookup"><span data-stu-id="fd094-111">If they aren't present, the method returns `S_FALSE`, and no valid enumerator is provided.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fd094-112">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="fd094-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd094-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="fd094-113">Requirements</span></span>  
 <span data-ttu-id="fd094-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd094-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd094-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fd094-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fd094-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd094-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd094-117">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd094-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd094-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd094-118">See Also</span></span>  
 [<span data-ttu-id="fd094-119">Icordebugassembly3, Interface</span><span class="sxs-lookup"><span data-stu-id="fd094-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 [<span data-ttu-id="fd094-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="fd094-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
