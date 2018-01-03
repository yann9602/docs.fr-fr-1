---
title: "NOTIFY_FILTER, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: NOTIFY_FILTER
api_location: diasymreader.dll
api_type: COM
f1_keywords: NOTIFY_FILTER
helpviewer_keywords: NOTIFY_FILTER enumeration [.NET Framework debugging]
ms.assetid: 4789d08f-8683-45d3-ac30-73d48c61e470
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ef72cb965bec8f424f5df35d4f66715fa11a5e46
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="notifyfilter-enumeration"></a><span data-ttu-id="d8056-102">NOTIFY_FILTER, énumération</span><span class="sxs-lookup"><span data-stu-id="d8056-102">NOTIFY_FILTER Enumeration</span></span>
<span data-ttu-id="d8056-103">Identifie des rappels pour les fonctions de débogueur.</span><span class="sxs-lookup"><span data-stu-id="d8056-103">Identifies callbacks for debugger functions.</span></span> <span data-ttu-id="d8056-104">Pour plus d’informations, consultez la [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="d8056-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8056-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8056-105">Syntax</span></span>  
  
```  
enum tagNOTIFY_FILTER  
{  
    NOTIFY_FILTER_ONSYNCCALLOUT    = 0x1,  
    NOTIFY_FILTER_ONSYNCCALLENTER  = 0x2,  
    NOTIFY_FILTER_ONSYNCCALLEXIT   = 0x4,  
    NOTIFY_FILTER_ONSYNCCALLRETURN = 0x8,  
    NOTIFY_FILTER_ALLSYNC = NOTIFY_FILTER_ONSYNCCALLOUT | NOTIFY_FILTER_ONSYNCCALLENTER | NOTIFY_FILTER_ONSYNCCALLEXIT | NOTIFY_FILTER_ONSYNCCALLRETURN,  
    NOTIFY_FILTER_ALL              = 0xffffffff,  
    NOTIFY_FILTER_NONE             = 0  
};  
```  
  
## <a name="members"></a><span data-ttu-id="d8056-106">Membres</span><span class="sxs-lookup"><span data-stu-id="d8056-106">Members</span></span>  
  
|<span data-ttu-id="d8056-107">Membre</span><span class="sxs-lookup"><span data-stu-id="d8056-107">Member</span></span>|<span data-ttu-id="d8056-108">Description</span><span class="sxs-lookup"><span data-stu-id="d8056-108">Description</span></span>|  
|------------|-----------------|  
|`NOTIFY_FILTER_ONSYNCCALLOUT`|<span data-ttu-id="d8056-109">Indique que le [INotifySink2::OnSyncCallOut](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md) méthode doit être appelée.</span><span class="sxs-lookup"><span data-stu-id="d8056-109">Indicates that the [INotifySink2::OnSyncCallOut](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLENTER`|<span data-ttu-id="d8056-110">Indique que le [INotifySink2::OnSyncCallEnter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md) méthode doit être appelée.</span><span class="sxs-lookup"><span data-stu-id="d8056-110">Indicates that the [INotifySink2::OnSyncCallEnter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLEXIT`|<span data-ttu-id="d8056-111">Indique que le [INotifySink2::OnSyncCallExit](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md) méthode doit être appelée.</span><span class="sxs-lookup"><span data-stu-id="d8056-111">Indicates that the [INotifySink2::OnSyncCallExit](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLRETURN`|<span data-ttu-id="d8056-112">Indique que le [INotifySink2::OnSyncCallReturn](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md) méthode doit être appelée.</span><span class="sxs-lookup"><span data-stu-id="d8056-112">Indicates that the [INotifySink2::OnSyncCallReturn](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALLSYNC`|<span data-ttu-id="d8056-113">Indique que tous les [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) méthode doit être appelée.</span><span class="sxs-lookup"><span data-stu-id="d8056-113">Indicates that all of the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) methods should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALL`|<span data-ttu-id="d8056-114">Active toutes les notifications existantes et futures.</span><span class="sxs-lookup"><span data-stu-id="d8056-114">Activates all existing and future notifications.</span></span>|  
|`NOTIFY_FILTER_NONE`|<span data-ttu-id="d8056-115">Indique qu’aucune méthode de notification doit être appelée.</span><span class="sxs-lookup"><span data-stu-id="d8056-115">Indicates that no notification methods should be invoked.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d8056-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d8056-116">Requirements</span></span>  
 <span data-ttu-id="d8056-117">**En-tête :** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="d8056-117">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8056-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8056-118">See Also</span></span>  
 [<span data-ttu-id="d8056-119">Énumérations du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="d8056-119">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
