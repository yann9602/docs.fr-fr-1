---
title: "ICorDebugStaticFieldSymbol::GetName, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: af3cea14e29c987d2d24d5adc803afd5b9084651
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="de565-102">ICorDebugStaticFieldSymbol::GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="de565-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="de565-103">Obtient le nom du champ static.</span><span class="sxs-lookup"><span data-stu-id="de565-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de565-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de565-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de565-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="de565-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="de565-106">[in] Nombre de caractères dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="de565-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="de565-107">[out] Pointeur vers le nombre de caractères réellement écrits dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="de565-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="de565-108">[out] Tableau de caractères qui stocke le nom retourné.</span><span class="sxs-lookup"><span data-stu-id="de565-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de565-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="de565-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="de565-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="de565-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de565-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="de565-111">Requirements</span></span>  
 <span data-ttu-id="de565-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de565-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de565-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="de565-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="de565-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de565-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de565-115">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de565-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de565-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de565-116">See Also</span></span>  
 [<span data-ttu-id="de565-117">Icordebugstaticfieldsymbol, Interface</span><span class="sxs-lookup"><span data-stu-id="de565-117">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="de565-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="de565-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
