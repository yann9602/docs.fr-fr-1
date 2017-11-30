---
title: "ICorDebugILFrame::EnumerateArguments, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.EnumerateArguments
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::EnumerateArguments
helpviewer_keywords:
- ICorDebugILFrame::EnumerateArguments method [.NET Framework debugging]
- EnumerateArguments method [.NET Framework debugging]
ms.assetid: 00ac81e2-a774-422a-bd88-54a4b3c99f73
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bf345f3fa684b57a33e3452916535b1cd7db3c8b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugilframeenumeratearguments-method"></a><span data-ttu-id="508e3-102">ICorDebugILFrame::EnumerateArguments, méthode</span><span class="sxs-lookup"><span data-stu-id="508e3-102">ICorDebugILFrame::EnumerateArguments Method</span></span>
<span data-ttu-id="508e3-103">Obtient un énumérateur pour les arguments dans ce frame.</span><span class="sxs-lookup"><span data-stu-id="508e3-103">Gets an enumerator for the arguments in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="508e3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="508e3-104">Syntax</span></span>  
  
```  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="508e3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="508e3-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="508e3-106">[out] Pointeur vers l’adresse d’un objet ICorDebugValueEnum qui est l’énumérateur pour les arguments dans ce frame.</span><span class="sxs-lookup"><span data-stu-id="508e3-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the arguments in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="508e3-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="508e3-107">Remarks</span></span>  
 <span data-ttu-id="508e3-108">`EnumerateArguments`Obtient un énumérateur qui peut répertorier les arguments disponibles dans le frame d’appel représenté par cet objet ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="508e3-108">`EnumerateArguments` gets an enumerator that can list the arguments available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="508e3-109">La liste inclut les arguments qui sont [vararg](/cpp/windows/vararg) (autrement dit, un nombre variable d’arguments) ainsi que les arguments qui ne sont pas `vararg`.</span><span class="sxs-lookup"><span data-stu-id="508e3-109">The list will include arguments that are [vararg](/cpp/windows/vararg) (that is, a variable number of arguments) as well as arguments that are not `vararg`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="508e3-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="508e3-110">Requirements</span></span>  
 <span data-ttu-id="508e3-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="508e3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="508e3-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="508e3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="508e3-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="508e3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="508e3-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="508e3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
