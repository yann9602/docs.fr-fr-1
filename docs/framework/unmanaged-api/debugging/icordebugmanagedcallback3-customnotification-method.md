---
title: "ICorDebugManagedCallback3::CustomNotification, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback3.CustomNotification Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback3::CustomNotification
helpviewer_keywords:
- ICorDebugManagedCallback3::CustomNotification method [.NET Framework debugging]
- CustomNotification method [.NET Framework debugging]
ms.assetid: 5e5422ac-afa1-403d-a894-2d7348673e38
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9c42443b0d1e355d4233909357c341763298160e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback3customnotification-method"></a><span data-ttu-id="5c341-102">ICorDebugManagedCallback3::CustomNotification, méthode</span><span class="sxs-lookup"><span data-stu-id="5c341-102">ICorDebugManagedCallback3::CustomNotification Method</span></span>
<span data-ttu-id="5c341-103">Indique qu’une notification de débogueur personnalisée a été déclenchée.</span><span class="sxs-lookup"><span data-stu-id="5c341-103">Indicates that a custom debugger notification has been raised.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c341-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c341-104">Syntax</span></span>  
  
```  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5c341-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5c341-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="5c341-106">[in] Pointeur vers le thread qui a déclenché la notification.</span><span class="sxs-lookup"><span data-stu-id="5c341-106">[in] A pointer to the thread that raised the notification.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="5c341-107">[in] Pointeur vers le domaine d’application qui contient le thread qui a déclenché la notification.</span><span class="sxs-lookup"><span data-stu-id="5c341-107">[in] A pointer to the application domain that contains the thread that raised the notification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c341-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="5c341-108">Return Value</span></span>  
 <span data-ttu-id="5c341-109">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="5c341-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="5c341-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5c341-110">HRESULT</span></span>|<span data-ttu-id="5c341-111">Description</span><span class="sxs-lookup"><span data-stu-id="5c341-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5c341-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="5c341-112">S_OK</span></span>|<span data-ttu-id="5c341-113">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="5c341-113">The method completed successfully.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="5c341-114">Exceptions</span><span class="sxs-lookup"><span data-stu-id="5c341-114">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c341-115">Notes</span><span class="sxs-lookup"><span data-stu-id="5c341-115">Remarks</span></span>  
 <span data-ttu-id="5c341-116">Un appel ultérieur à la [ICorDebugThread4::GetCurrentCustomDebuggerNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md) méthode extrait l’objet thread qui a été passé à la <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> (méthode).</span><span class="sxs-lookup"><span data-stu-id="5c341-116">A subsequent call to the [ICorDebugThread4::GetCurrentCustomDebuggerNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md) method retrieves the thread object that was passed to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5c341-117">Type de l’objet thread doit avoir été précédemment activé en appelant le [ICorDebugProcess3::SetEnableCustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="5c341-117">The thread object's type must have been previously enabled by calling the [ICorDebugProcess3::SetEnableCustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md) method.</span></span> <span data-ttu-id="5c341-118">Le débogueur peut lire des paramètres spécifiques au type à partir des champs de l’objet thread et peut stocker les réponses dans les champs.</span><span class="sxs-lookup"><span data-stu-id="5c341-118">The debugger can read type-specific parameters from the fields of the thread object, and can store responses into fields.</span></span>  
  
 <span data-ttu-id="5c341-119">Le [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface n’impose aucune stratégie sur les types de notifications ou leur contenu, et la sémantique des notifications est strictement un contrat entre les débogueurs, applications et le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5c341-119">The [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface imposes no policy on the types of notifications or their contents, and the semantics of the notifications are strictly a contract between debuggers, applications, and the .NET Framework.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c341-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5c341-120">Requirements</span></span>  
 <span data-ttu-id="5c341-121">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c341-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c341-122">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5c341-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c341-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c341-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c341-124">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c341-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c341-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c341-125">See Also</span></span>  
 [<span data-ttu-id="5c341-126">ICorDebugManagedCallback3, interface</span><span class="sxs-lookup"><span data-stu-id="5c341-126">ICorDebugManagedCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)  
 [<span data-ttu-id="5c341-127">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="5c341-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="5c341-128">Débogage</span><span class="sxs-lookup"><span data-stu-id="5c341-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
