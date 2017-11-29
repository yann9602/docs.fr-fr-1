---
title: "VerifyClientKey (fonction) (référence des API non managées)"
description: "La fonction VerifyClientKey garantit que la clé du client a la sécurité appropriée."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: VerifyClientKey
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: VerifyClientKey
helpviewer_keywords: VerifyClientKey function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cce10e3dd5536a85b4dee62cc7f6e9e8e73929cb
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="b92e9-103">VerifyClientKey (fonction)</span><span class="sxs-lookup"><span data-stu-id="b92e9-103">VerifyClientKey function</span></span>
<span data-ttu-id="b92e9-104">Garantit que la clé du client dispose de la sécurité appropriée.</span><span class="sxs-lookup"><span data-stu-id="b92e9-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="b92e9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b92e9-105">Syntax</span></span>  
  
```  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a><span data-ttu-id="b92e9-106">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b92e9-106">Return value</span></span>

<span data-ttu-id="b92e9-107">Si la fonction réussit, la valeur de retour est `ERROR_SUCCESS` (0).</span><span class="sxs-lookup"><span data-stu-id="b92e9-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="b92e9-108">Si la fonction échoue, la valeur de retour est un code d’erreur différent de zéro défini dans *WinError.h*.</span><span class="sxs-lookup"><span data-stu-id="b92e9-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="b92e9-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b92e9-109">Requirements</span></span>  
 <span data-ttu-id="b92e9-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b92e9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b92e9-111">**En-tête :** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="b92e9-111">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="b92e9-112">**Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b92e9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b92e9-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b92e9-113">See also</span></span>  
[<span data-ttu-id="b92e9-114">WMI et les compteurs de Performance (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="b92e9-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
