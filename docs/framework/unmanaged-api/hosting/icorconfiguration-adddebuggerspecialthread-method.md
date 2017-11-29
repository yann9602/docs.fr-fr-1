---
title: "ICorConfiguration::AddDebuggerSpecialThread, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorConfiguration.AddDebuggerSpecialThread
api_location: mscoree.dll
api_type: COM
f1_keywords: AddDebuggerSpecialThread
helpviewer_keywords:
- AddDebuggerSpecialThread method [.NET Framework hosting]
- ICorConfiguration::AddDebuggerSpecialThread method [.NET Framework hosting]
ms.assetid: 1f1e3239-438e-4be9-a3bb-7d0722d3a76d
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2501461267ff7369cd9c48f4cef6cda42063a48b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a><span data-ttu-id="0b759-102">ICorConfiguration::AddDebuggerSpecialThread, méthode</span><span class="sxs-lookup"><span data-stu-id="0b759-102">ICorConfiguration::AddDebuggerSpecialThread Method</span></span>
<span data-ttu-id="0b759-103">Indique aux services de débogage qu’un thread particulier doit être autorisé à continuer de s’exécuter pendant que le débogueur arrête les scénarios de débogage managés ou une application.</span><span class="sxs-lookup"><span data-stu-id="0b759-103">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b759-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b759-104">Syntax</span></span>  
  
```  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0b759-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0b759-105">Parameters</span></span>  
 `dwSpecialThreadId`  
 <span data-ttu-id="0b759-106">[in] L’ID du thread qui doit être autorisé à continuer de s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="0b759-106">[in] The ID of the thread that should be allowed to continue executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b759-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="0b759-107">Remarks</span></span>  
 <span data-ttu-id="0b759-108">Le thread spécifié pas pourront s’exécuter du code managé ou entrez l’exécution de toute façon.</span><span class="sxs-lookup"><span data-stu-id="0b759-108">The specified thread will not be allowed to run managed code or enter the runtime in any way.</span></span> <span data-ttu-id="0b759-109">Un exemple de ce type de thread serait un thread in-process pour prendre en charge les débogueurs de scripts hérités.</span><span class="sxs-lookup"><span data-stu-id="0b759-109">An example of such a thread would be an in-process thread to support legacy script debuggers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b759-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0b759-110">Requirements</span></span>  
 <span data-ttu-id="0b759-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b759-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b759-112">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0b759-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0b759-113">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0b759-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0b759-114">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b759-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b759-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b759-115">See Also</span></span>  
 [<span data-ttu-id="0b759-116">ICorConfiguration (Interface)</span><span class="sxs-lookup"><span data-stu-id="0b759-116">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
