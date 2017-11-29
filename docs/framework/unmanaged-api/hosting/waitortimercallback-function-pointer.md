---
title: WAITORTIMERCALLBACK (pointeur fonction)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: WAITORTIMERCALLBACK
api_location: mscoree.dll
api_type: COM
f1_keywords: WAITORTIMERCALLBACK
helpviewer_keywords: WAITORTIMERCALLBACK function pointer [.NET Framework hosting]
ms.assetid: 1fec4aef-0a06-4df0-bae7-d31a9ef9603d
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 873d2ff489085ec2a0c37be2feeb3e15f61c9227
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="waitortimercallback-function-pointer"></a><span data-ttu-id="6b004-102">WAITORTIMERCALLBACK (pointeur fonction)</span><span class="sxs-lookup"><span data-stu-id="6b004-102">WAITORTIMERCALLBACK Function Pointer</span></span>
<span data-ttu-id="6b004-103">Pointe vers une fonction qui avertit l’hôte qu’un handle d’attente (<xref:System.Threading.WaitHandle>) a été signalé ou a expiré.</span><span class="sxs-lookup"><span data-stu-id="6b004-103">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span></span>  
  
 <span data-ttu-id="6b004-104">Ce pointeur de fonction a été déconseillé dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6b004-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b004-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b004-105">Syntax</span></span>  
  
```  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6b004-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6b004-106">Parameters</span></span>  
 `lpParameter`  
 <span data-ttu-id="6b004-107">[in] Pointeur vers un objet qui contient des informations définies par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="6b004-107">[in] A pointer to an object that contains information defined by the host.</span></span>  
  
 `TimerOrWaitFired`  
 <span data-ttu-id="6b004-108">[in] `true` si le handle d’attente a expiré, ou `false` si elle a été signalée.</span><span class="sxs-lookup"><span data-stu-id="6b004-108">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b004-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="6b004-109">Remarks</span></span>  
 <span data-ttu-id="6b004-110">La fonction à laquelle `WAITORTIMERCALLBACK` points est une fonction de rappel et doit être implémentée par le writer de l’application d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="6b004-110">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b004-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6b004-111">Requirements</span></span>  
 <span data-ttu-id="6b004-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b004-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b004-113">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6b004-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6b004-114">**Bibliothèque :** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="6b004-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="6b004-115">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b004-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b004-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b004-116">See Also</span></span>  
 [<span data-ttu-id="6b004-117">Fonctions d’hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="6b004-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
