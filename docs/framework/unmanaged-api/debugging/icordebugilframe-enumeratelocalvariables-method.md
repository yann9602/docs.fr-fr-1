---
title: "ICorDebugILFrame::EnumerateLocalVariables, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.EnumerateLocalVariables
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::EnumerateLocalVariables
helpviewer_keywords:
- EnumerateLocalVariables method [.NET Framework debugging]
- ICorDebugILFrame::EnumerateLocalVariables method [.NET Framework debugging]
ms.assetid: 1a67fa1b-2419-4cd0-aad4-6f46a0719b4b
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3a1b53dbefefcea6003ec4a61c8169ed96bac701
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a><span data-ttu-id="497ae-102">ICorDebugILFrame::EnumerateLocalVariables, méthode</span><span class="sxs-lookup"><span data-stu-id="497ae-102">ICorDebugILFrame::EnumerateLocalVariables Method</span></span>
<span data-ttu-id="497ae-103">Obtient un énumérateur pour les variables locales dans ce frame.</span><span class="sxs-lookup"><span data-stu-id="497ae-103">Gets an enumerator for the local variables in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="497ae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="497ae-104">Syntax</span></span>  
  
```  
HRESULT EnumerateLocalVariables(   
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="497ae-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="497ae-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="497ae-106">[out] Pointeur vers l’adresse d’un objet ICorDebugValueEnum qui est l’énumérateur pour les variables locales de ce frame.</span><span class="sxs-lookup"><span data-stu-id="497ae-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="497ae-107">Notes</span><span class="sxs-lookup"><span data-stu-id="497ae-107">Remarks</span></span>  
 <span data-ttu-id="497ae-108">`EnumerateLocalVariables`Obtient un énumérateur qui peut répertorier les variables locales disponibles dans le frame d’appel représenté par cet objet ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="497ae-108">`EnumerateLocalVariables` gets an enumerator that can list the local variables available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="497ae-109">La liste ne peut-être pas inclure toutes les variables locales dans la fonction en cours d’exécution, car certains d'entre eux ne peuvent pas être actif.</span><span class="sxs-lookup"><span data-stu-id="497ae-109">The list may not include all of the local variables in the running function, because some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="497ae-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="497ae-110">Requirements</span></span>  
 <span data-ttu-id="497ae-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="497ae-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="497ae-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="497ae-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="497ae-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="497ae-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="497ae-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="497ae-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
