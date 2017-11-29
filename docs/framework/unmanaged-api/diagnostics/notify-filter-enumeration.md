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
ms.openlocfilehash: 9db03458aab60d28efe52edfd9830da7862fcb8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="notifyfilter-enumeration"></a><span data-ttu-id="e3dfc-102">NOTIFY_FILTER, énumération</span><span class="sxs-lookup"><span data-stu-id="e3dfc-102">NOTIFY_FILTER Enumeration</span></span>
<span data-ttu-id="e3dfc-103">Identifie des rappels pour les fonctions de débogueur.</span><span class="sxs-lookup"><span data-stu-id="e3dfc-103">Identifies callbacks for debugger functions.</span></span> <span data-ttu-id="e3dfc-104">Pour plus d’informations, consultez la [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="e3dfc-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3dfc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3dfc-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="e3dfc-106">Membres</span><span class="sxs-lookup"><span data-stu-id="e3dfc-106">Members</span></span>  
  
|<span data-ttu-id="e3dfc-107">Membre</span><span class="sxs-lookup"><span data-stu-id="e3dfc-107">Member</span></span>|<span data-ttu-id="e3dfc-108">Description</span><span class="sxs-lookup"><span data-stu-id="e3dfc-108">Description</span></span>|  
|------------|-----------------|  
|`NOTIFY_FILTER_ONSYNCCALLOUT`|<span data-ttu-id="e3dfc-109">Indique que le [INotifySink2::OnSyncCallOut](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md) méthode doit être appelée.</span><span class="sxs-lookup"><span data-stu-id="e3dfc-109">Indicates that the [INotifySink2::OnSyncCallOut](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLENTER`|<span data-ttu-id="e3dfc-110">Indique que le [INotifySink2::OnSyncCallEnter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md) méthode doit être appelée.</span><span class="sxs-lookup"><span data-stu-id="e3dfc-110">Indicates that the [INotifySink2::OnSyncCallEnter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLEXIT`|<span data-ttu-id="e3dfc-111">Indique que le [INotifySink2::OnSyncCallExit](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md) méthode doit être appelée.</span><span class="sxs-lookup"><span data-stu-id="e3dfc-111">Indicates that the [INotifySink2::OnSyncCallExit](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLRETURN`|<span data-ttu-id="e3dfc-112">Indique que le [INotifySink2::OnSyncCallReturn](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md) méthode doit être appelée.</span><span class="sxs-lookup"><span data-stu-id="e3dfc-112">Indicates that the [INotifySink2::OnSyncCallReturn](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALLSYNC`|<span data-ttu-id="e3dfc-113">Indique que tous les [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) méthode doit être appelée.</span><span class="sxs-lookup"><span data-stu-id="e3dfc-113">Indicates that all of the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) methods should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALL`|<span data-ttu-id="e3dfc-114">Active toutes les notifications existantes et futures.</span><span class="sxs-lookup"><span data-stu-id="e3dfc-114">Activates all existing and future notifications.</span></span>|  
|`NOTIFY_FILTER_NONE`|<span data-ttu-id="e3dfc-115">Indique qu’aucune méthode de notification doit être appelée.</span><span class="sxs-lookup"><span data-stu-id="e3dfc-115">Indicates that no notification methods should be invoked.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e3dfc-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e3dfc-116">Requirements</span></span>  
 <span data-ttu-id="e3dfc-117">**En-tête :** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="e3dfc-117">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3dfc-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3dfc-118">See Also</span></span>  
 [<span data-ttu-id="e3dfc-119">Énumérations du magasin de symboles de Diagnostics</span><span class="sxs-lookup"><span data-stu-id="e3dfc-119">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
