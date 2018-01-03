---
title: ICLRHostProtectionManager, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRHostProtectionManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRHostProtectionManager
helpviewer_keywords: ICLRHostProtectionManager interface [.NET Framework hosting]
ms.assetid: ce2770ae-23d0-45d9-8bcf-46504ac5020e
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 37b1aaeef1d4c375f36ad043124287fc3b41e3fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrhostprotectionmanager-interface"></a><span data-ttu-id="e7f44-102">ICLRHostProtectionManager, interface</span><span class="sxs-lookup"><span data-stu-id="e7f44-102">ICLRHostProtectionManager Interface</span></span>
<span data-ttu-id="e7f44-103">Permet à l’hôte bloquer les classes managées spécifiques, les méthodes, les propriétés et les champs de l’exécution dans du code partiellement fiable.</span><span class="sxs-lookup"><span data-stu-id="e7f44-103">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e7f44-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="e7f44-104">Methods</span></span>  
  
|<span data-ttu-id="e7f44-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="e7f44-105">Method</span></span>|<span data-ttu-id="e7f44-106">Description</span><span class="sxs-lookup"><span data-stu-id="e7f44-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e7f44-107">SetEagerSerializeGrantSets</span><span class="sxs-lookup"><span data-stu-id="e7f44-107">SetEagerSerializeGrantSets</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|<span data-ttu-id="e7f44-108">Fournit une garantie que certaines conditions de concurrence peuvent erreurs irrécupérable langage common runtime (CLR) ne seront jamais se produire.</span><span class="sxs-lookup"><span data-stu-id="e7f44-108">Provides a guarantee that certain rare race conditions that can cause fatal common language runtime (CLR) errors will never arise.</span></span>|  
|[<span data-ttu-id="e7f44-109">SetProtectedCategories, méthode</span><span class="sxs-lookup"><span data-stu-id="e7f44-109">SetProtectedCategories Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)|<span data-ttu-id="e7f44-110">Spécifie les catégories de types managés et les membres qui ne doivent pas recevoir de s’exécuter dans du code partiellement fiable.</span><span class="sxs-lookup"><span data-stu-id="e7f44-110">Specifies the categories of managed types and members that should be blocked from running in partially trusted code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e7f44-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e7f44-111">Requirements</span></span>  
 <span data-ttu-id="e7f44-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7f44-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7f44-113">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e7f44-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e7f44-114">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e7f44-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e7f44-115">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7f44-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7f44-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7f44-116">See Also</span></span>  
 [<span data-ttu-id="e7f44-117">EApiCategories, énumération</span><span class="sxs-lookup"><span data-stu-id="e7f44-117">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)  
 [<span data-ttu-id="e7f44-118">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="e7f44-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
