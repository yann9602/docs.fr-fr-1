---
title: "SetSecurity (fonction) (référence des API non managées)"
description: "La fonction SetSecurity récupère le jeton d’emprunt d’identité du thread actuel."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: SetSecurity
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: SetSecurity
helpviewer_keywords: SetSecurity function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: abb716d64bde9b298203e54d862ff4f1b2bcd170
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="setsecurity-function"></a><span data-ttu-id="1757b-103">SetSecurity (fonction)</span><span class="sxs-lookup"><span data-stu-id="1757b-103">SetSecurity function</span></span>
<span data-ttu-id="1757b-104">Récupère le jeton d’emprunt d’identité associé au thread actuel.</span><span class="sxs-lookup"><span data-stu-id="1757b-104">Retrieves the impersonation token associated with the current thread.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="1757b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1757b-105">Syntax</span></span>  
  
```  
HRESULT SetSecurity (
   [out] boolean* pNeedToReset, 
   [out] HANDLE* pCurrentThreadToken
); 
```  

## <a name="parameters"></a><span data-ttu-id="1757b-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1757b-106">Parameters</span></span>

<span data-ttu-id="1757b-107">`pNeedToReset`[out] Lorsque la fonction est retournée, contient un pointeur vers un `boolean` qui indique si le jeton doit être réinitialisé en appelant le [ResetSecurity](resetsecurity.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="1757b-107">`pNeedToReset` [out] When the function returns, contains a pointer to a `boolean` that indicates whether the token should be reset by calling the [ResetSecurity](resetsecurity.md) function.</span></span>  

`token`  
<span data-ttu-id="1757b-108">[out] Lorsque la fonction est retournée, contient un pointeur vers le handle du jeton d’emprunt d’identité associé au thread actuel.</span><span class="sxs-lookup"><span data-stu-id="1757b-108">[out] When the function returns, contains a pointer to the handle of the impersonation token associated with the current thread.</span></span> <span data-ttu-id="1757b-109">Sa valeur peut être `null` s’il n’existe aucun jeton associé au thread actuel.</span><span class="sxs-lookup"><span data-stu-id="1757b-109">Its value can be `null` if there is no token associated with the current thread.</span></span> 

## <a name="return-value"></a><span data-ttu-id="1757b-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1757b-110">Return value</span></span>

<span data-ttu-id="1757b-111">Si la fonction réussit, la valeur de retour est `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="1757b-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="1757b-112">Si la fonction échoue, la valeur de retour est un code d’erreur différent de zéro.</span><span class="sxs-lookup"><span data-stu-id="1757b-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="1757b-113">Pour obtenir des informations d’erreur plus complètes, appelez le [GetErrorInfo](geterrorinfo.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="1757b-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="1757b-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1757b-114">Requirements</span></span>  
 <span data-ttu-id="1757b-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1757b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1757b-116">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="1757b-116">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="1757b-117">**Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1757b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1757b-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1757b-118">See also</span></span>  
[<span data-ttu-id="1757b-119">WMI et les compteurs de Performance (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="1757b-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
