---
title: FExecuteInAppDomainCallback (pointeur fonction)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FExecuteInAppDomainCallback
api_location: mscoree.dll
api_type: COM
f1_keywords: FExecuteInAppDomainCallback
helpviewer_keywords: FExecuteInAppDomainCallback function pointer [.NET Framework hosting]
ms.assetid: 2709f18f-3eee-497f-bc33-3ab7a485599b
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9852abbf2f69dda5c4c3b06f48adbd1bc33f5a1e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a><span data-ttu-id="afb74-102">FExecuteInAppDomainCallback (pointeur fonction)</span><span class="sxs-lookup"><span data-stu-id="afb74-102">FExecuteInAppDomainCallback Function Pointer</span></span>
<span data-ttu-id="afb74-103">Pointe vers une fonction qui est appelée par le common language runtime (CLR) pour exécuter le code managé.</span><span class="sxs-lookup"><span data-stu-id="afb74-103">Points to a function that is called by the common language runtime (CLR) to execute managed code.</span></span>  
  
 <span data-ttu-id="afb74-104">Ce pointeur de fonction a été déconseillé dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="afb74-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afb74-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="afb74-105">Syntax</span></span>  
  
```  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="afb74-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="afb74-106">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="afb74-107">[in] Pointeur vers la mémoire allouée par l’appelant opaque qui contient le code managé à exécuter.</span><span class="sxs-lookup"><span data-stu-id="afb74-107">[in] A pointer to opaque caller-allocated memory that contains the managed code to be executed.</span></span>  
  
 <span data-ttu-id="afb74-108">L’allocation et la durée de vie de cette mémoire sont contrôlées par l’appelant (autrement dit, le CLR).</span><span class="sxs-lookup"><span data-stu-id="afb74-108">The allocation and lifetime of this memory are controlled by the caller (that is, the CLR).</span></span> <span data-ttu-id="afb74-109">Ce n’est pas mémoire de tas managé CLR.</span><span class="sxs-lookup"><span data-stu-id="afb74-109">This is not CLR managed-heap memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afb74-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="afb74-110">Requirements</span></span>  
 <span data-ttu-id="afb74-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afb74-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afb74-112">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="afb74-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="afb74-113">**Bibliothèque :** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="afb74-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="afb74-114">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afb74-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afb74-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="afb74-115">See Also</span></span>  
 [<span data-ttu-id="afb74-116">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="afb74-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
