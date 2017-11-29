---
title: "ICorDebugSymbolProvider::GetMergedAssemblyRecords, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1f7515479ae5fbe490496bac79f102b02700dcee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="9ec0b-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords, méthode</span><span class="sxs-lookup"><span data-stu-id="9ec0b-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>
<span data-ttu-id="9ec0b-103">Obtient les enregistrements de symbole de tous les assemblys fusionnés.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-103">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ec0b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ec0b-104">Syntax</span></span>  
  
```  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9ec0b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9ec0b-105">Parameters</span></span>  
 `cRequestedRecords`  
 <span data-ttu-id="9ec0b-106">[in] Nombre d'enregistrements de symbole demandé.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-106">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="9ec0b-107">[out] Pointeur vers le nombre d'enregistrements de symbole récupéré par la méthode.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-107">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="9ec0b-108">Un pointeur vers un tableau de [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objets.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-108">A pointer to an array of [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ec0b-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="9ec0b-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ec0b-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ec0b-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9ec0b-111">Requirements</span></span>  
 <span data-ttu-id="9ec0b-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ec0b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ec0b-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ec0b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ec0b-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ec0b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ec0b-115">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ec0b-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ec0b-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ec0b-116">See Also</span></span>  
 [<span data-ttu-id="9ec0b-117">Icordebugsymbolprovider, Interface</span><span class="sxs-lookup"><span data-stu-id="9ec0b-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="9ec0b-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="9ec0b-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
