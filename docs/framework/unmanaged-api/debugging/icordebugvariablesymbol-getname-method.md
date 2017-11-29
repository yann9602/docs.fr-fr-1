---
title: "Méthode ICorDebugVariableSymbol::GetName"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: aff18efb6781aee5b6a148fcd59863a2ce657023
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="8d4b2-102">Méthode ICorDebugVariableSymbol::GetName</span><span class="sxs-lookup"><span data-stu-id="8d4b2-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="8d4b2-103">Obtient le nom d'une variable.</span><span class="sxs-lookup"><span data-stu-id="8d4b2-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d4b2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d4b2-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8d4b2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8d4b2-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="8d4b2-106">[in] Nombre de caractères dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="8d4b2-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="8d4b2-107">[out] Pointeur vers le nombre de caractères réellement écrits dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="8d4b2-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="8d4b2-108">Pointeur vers un tableau de caractères qui contient le nom de la variable.</span><span class="sxs-lookup"><span data-stu-id="8d4b2-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d4b2-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="8d4b2-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d4b2-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8d4b2-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d4b2-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8d4b2-111">Requirements</span></span>  
 <span data-ttu-id="8d4b2-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d4b2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d4b2-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8d4b2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d4b2-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d4b2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d4b2-115">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d4b2-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d4b2-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d4b2-116">See Also</span></span>  
 [<span data-ttu-id="8d4b2-117">Icordebugvariablesymbol, Interface</span><span class="sxs-lookup"><span data-stu-id="8d4b2-117">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="8d4b2-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="8d4b2-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
