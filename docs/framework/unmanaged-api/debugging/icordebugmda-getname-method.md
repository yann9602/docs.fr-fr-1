---
title: "ICorDebugMDA::GetName, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugMDA.GetName
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugMDA::GetName
helpviewer_keywords:
- ICorDebugMDA::GetName method [.NET Framework debugging]
- GetName method, ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 885bf5e8-00b7-4cd7-9d8d-e720d47918c4
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c31125b1faf9f14262e8e4a4c6269671a35519f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmdagetname-method"></a><span data-ttu-id="af22b-102">ICorDebugMDA::GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="af22b-102">ICorDebugMDA::GetName Method</span></span>
<span data-ttu-id="af22b-103">Obtient une chaîne contenant le nom de l’assistant débogage managé (MDA) représenté par [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="af22b-103">Gets a string containing the name of the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af22b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af22b-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="af22b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="af22b-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="af22b-106">[in] Taille du tableau `szName`.</span><span class="sxs-lookup"><span data-stu-id="af22b-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="af22b-107">[out] Pointeur vers la longueur du nom.</span><span class="sxs-lookup"><span data-stu-id="af22b-107">[out] A pointer to the length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="af22b-108">[out] Tableau dans lequel stocker le nom.</span><span class="sxs-lookup"><span data-stu-id="af22b-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af22b-109">Notes</span><span class="sxs-lookup"><span data-stu-id="af22b-109">Remarks</span></span>  
 <span data-ttu-id="af22b-110">Les noms d’Assistant Débogage MANAGÉ sont des valeurs uniques.</span><span class="sxs-lookup"><span data-stu-id="af22b-110">MDA names are unique values.</span></span> <span data-ttu-id="af22b-111">Le `GetName` méthode constitue une alternative de performance appropriée pour obtenir le flux XML et extraire le nom du flux s’appuyant sur le schéma.</span><span class="sxs-lookup"><span data-stu-id="af22b-111">The `GetName` method is a convenient performance alternative to getting the XML stream and extracting the name from the stream based on the schema.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af22b-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="af22b-112">Requirements</span></span>  
 <span data-ttu-id="af22b-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af22b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af22b-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="af22b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af22b-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af22b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af22b-116">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af22b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af22b-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af22b-117">See Also</span></span>  
 [<span data-ttu-id="af22b-118">ICorDebugMDA, interface</span><span class="sxs-lookup"><span data-stu-id="af22b-118">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 [<span data-ttu-id="af22b-119">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="af22b-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
