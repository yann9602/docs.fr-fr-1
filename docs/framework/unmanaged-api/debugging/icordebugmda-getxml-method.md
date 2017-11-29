---
title: "ICorDebugMDA::GetXML, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugMDA.GetXML
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugMDA::GetXML
helpviewer_keywords:
- ICorDebugMDA::GetXML method [.NET Framework debugging]
- GetXML method [.NET Framework debugging]
ms.assetid: 29746b24-3766-4255-8813-0426c45e73e5
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c9f1ad3ac70f001feebb0b28eec13cb45ca2c866
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmdagetxml-method"></a><span data-ttu-id="62c63-102">ICorDebugMDA::GetXML, méthode</span><span class="sxs-lookup"><span data-stu-id="62c63-102">ICorDebugMDA::GetXML Method</span></span>
<span data-ttu-id="62c63-103">Obtient le flux XML complet associé à l’assistant débogage managé (MDA) représenté par [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="62c63-103">Gets the full XML stream associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62c63-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62c63-104">Syntax</span></span>  
  
```  
HRESULT GetXML (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62c63-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="62c63-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="62c63-106">[in] Taille du tableau `szName`.</span><span class="sxs-lookup"><span data-stu-id="62c63-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="62c63-107">[out] Pointeur vers la longueur du flux XML.</span><span class="sxs-lookup"><span data-stu-id="62c63-107">[out] A pointer to the length of the XML stream.</span></span>  
  
 `szName`  
 <span data-ttu-id="62c63-108">[out] Tableau dans lequel stocker le flux XML.</span><span class="sxs-lookup"><span data-stu-id="62c63-108">[out] An array in which to store the XML stream.</span></span> <span data-ttu-id="62c63-109">Le tableau peut être vide.</span><span class="sxs-lookup"><span data-stu-id="62c63-109">The array may be empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62c63-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="62c63-110">Remarks</span></span>  
 <span data-ttu-id="62c63-111">Le `GetXML` méthode peut éventuellement affecter les performances, selon la taille du flux XML associé.</span><span class="sxs-lookup"><span data-stu-id="62c63-111">The `GetXML` method can potentially affect performance, depending on the size of the associated XML stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62c63-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="62c63-112">Requirements</span></span>  
 <span data-ttu-id="62c63-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62c63-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62c63-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="62c63-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62c63-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62c63-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62c63-116">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62c63-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62c63-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62c63-117">See Also</span></span>  
 [<span data-ttu-id="62c63-118">ICorDebugMDA (Interface)</span><span class="sxs-lookup"><span data-stu-id="62c63-118">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 [<span data-ttu-id="62c63-119">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="62c63-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
