---
title: "GetErrorInfo (fonction) (référence des API non managées)"
description: "La fonction GetErrorInfo récupère les informations d’erreur à partir de l’appel de fonction précédente."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetErrorInfo
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetErrorInfo
helpviewer_keywords: GetErrorInfo function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a1bdaa72723855c6688a7c8c7704b958f6196dfd
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="913da-103">GetErrorInfo (fonction)</span><span class="sxs-lookup"><span data-stu-id="913da-103">GetErrorInfo function</span></span>
<span data-ttu-id="913da-104">Récupère les informations d’erreur à partir de l’appel de fonction précédente.</span><span class="sxs-lookup"><span data-stu-id="913da-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="913da-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="913da-105">Syntax</span></span>  
  
```  
IErrorInfo* GetErrorInfo(); 
```  

## <a name="return-value"></a><span data-ttu-id="913da-106">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="913da-106">Return value</span></span>

<span data-ttu-id="913da-107">Un pointeur vers un [IErrorInfo](https://msdn.microsoft.com/library/windows/desktop/ms221233(v=vs.85).aspx) objet si l’appel de fonction aboutit, ou `null` en cas d’échec.</span><span class="sxs-lookup"><span data-stu-id="913da-107">An pointer to an [IErrorInfo](https://msdn.microsoft.com/library/windows/desktop/ms221233(v=vs.85).aspx) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="913da-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="913da-108">Remarks</span></span>

<span data-ttu-id="913da-109">Cette fonction encapsule un appel à la [IComThreadingInfo::GetErrorInfo](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) (méthode).</span><span class="sxs-lookup"><span data-stu-id="913da-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="913da-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="913da-110">Requirements</span></span>  
 <span data-ttu-id="913da-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="913da-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="913da-112">**En-tête :** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="913da-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="913da-113">**Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="913da-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="913da-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="913da-114">See also</span></span>  
[<span data-ttu-id="913da-115">WMI et les compteurs de Performance (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="913da-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
