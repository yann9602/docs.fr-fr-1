---
title: "ResetSecurity (fonction) (référence des API non managées)"
description: "La fonction ResetSecurity assigne un jeton d’emprunt d’identité pour le thread actuel."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: ResetSecurity
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: ResetSecurity
helpviewer_keywords: ResetSecurity function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2790012a429c6a0551d8321a80570f3f8be2142b
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="resetsecurity-function"></a><span data-ttu-id="ab17c-103">ResetSecurity (fonction)</span><span class="sxs-lookup"><span data-stu-id="ab17c-103">ResetSecurity function</span></span>
<span data-ttu-id="ab17c-104">Assigne le jeton d’emprunt d’identité fournie pour le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="ab17c-104">Assigns the supplied impersonation token to the current thread.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="ab17c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab17c-105">Syntax</span></span>  
  
```  
HRESULT ResetSecurity (
   [in] HANDLE token
); 
```  

## <a name="parameters"></a><span data-ttu-id="ab17c-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ab17c-106">Parameters</span></span>

`token`  
<span data-ttu-id="ab17c-107">[in] Le jeton d’emprunt d’identité à associer au thread en cours.</span><span class="sxs-lookup"><span data-stu-id="ab17c-107">[in] The impersonation token to associate with the current thread.</span></span> <span data-ttu-id="ab17c-108">Sa valeur peut être `null`.</span><span class="sxs-lookup"><span data-stu-id="ab17c-108">Its value can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="ab17c-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ab17c-109">Return value</span></span>

<span data-ttu-id="ab17c-110">Si la fonction réussit, la valeur de retour est `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="ab17c-110">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="ab17c-111">Si la fonction échoue, la valeur de retour est un code d’erreur différent de zéro.</span><span class="sxs-lookup"><span data-stu-id="ab17c-111">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="ab17c-112">Pour obtenir des informations d’erreur plus complètes, appelez le [GetErrorInfo](geterrorinfo.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="ab17c-112">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="ab17c-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ab17c-113">Requirements</span></span>  
 <span data-ttu-id="ab17c-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab17c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab17c-115">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="ab17c-115">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="ab17c-116">**Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ab17c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab17c-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab17c-117">See also</span></span>  
[<span data-ttu-id="ab17c-118">WMI et les compteurs de Performance (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="ab17c-118">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
