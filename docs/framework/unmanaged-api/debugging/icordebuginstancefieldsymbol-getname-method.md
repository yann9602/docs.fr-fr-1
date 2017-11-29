---
title: "ICorDebugInstanceFieldSymbol::GetName, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cfd56230d391c44343bdb3f575247b07af1e98ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="ffdae-102">ICorDebugInstanceFieldSymbol::GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="ffdae-102">ICorDebugInstanceFieldSymbol::GetName Method</span></span>
<span data-ttu-id="ffdae-103">Obtient le nom du champ d'instance.</span><span class="sxs-lookup"><span data-stu-id="ffdae-103">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffdae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ffdae-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ffdae-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ffdae-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="ffdae-106">[in] Nombre de caractères dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="ffdae-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ffdae-107">[out] Pointeur vers le nombre de caractères réellement écrits dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="ffdae-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="ffdae-108">[out] Tableau de caractères qui stocke le nom retourné.</span><span class="sxs-lookup"><span data-stu-id="ffdae-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ffdae-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="ffdae-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ffdae-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ffdae-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffdae-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ffdae-111">Requirements</span></span>  
 <span data-ttu-id="ffdae-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffdae-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffdae-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ffdae-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ffdae-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ffdae-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ffdae-115">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffdae-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffdae-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ffdae-116">See Also</span></span>  
 [<span data-ttu-id="ffdae-117">Icordebuginstancefieldsymbol, Interface</span><span class="sxs-lookup"><span data-stu-id="ffdae-117">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="ffdae-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="ffdae-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
