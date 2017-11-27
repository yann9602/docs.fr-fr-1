---
title: ICLRDomainManager, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDomainManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDomainManager
helpviewer_keywords: ICLRDomainManager interface [.NET Framework hosting]
ms.assetid: f08b2390-d872-4521-a815-e9c237c4c45d
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 75a7e93d26a5c77484d78ad4632bedf8def6a44b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdomainmanager-interface"></a><span data-ttu-id="5e995-102">ICLRDomainManager, interface</span><span class="sxs-lookup"><span data-stu-id="5e995-102">ICLRDomainManager Interface</span></span>
<span data-ttu-id="5e995-103">Permet à l’hôte spécifier le Gestionnaire de domaine d’application qui sera utilisé pour initialiser le domaine d’application par défaut et pour spécifier les propriétés d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="5e995-103">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5e995-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="5e995-104">Methods</span></span>  
  
|<span data-ttu-id="5e995-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="5e995-105">Method</span></span>|<span data-ttu-id="5e995-106">Description</span><span class="sxs-lookup"><span data-stu-id="5e995-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5e995-107">SetAppDomainManagerType (méthode)</span><span class="sxs-lookup"><span data-stu-id="5e995-107">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)|<span data-ttu-id="5e995-108">Spécifie le type, dérivé de la <xref:System.AppDomainManager?displayProperty=nameWithType> classe, le Gestionnaire de domaine d’application qui servira à initialiser le domaine d’application par défaut.</span><span class="sxs-lookup"><span data-stu-id="5e995-108">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>|  
|[<span data-ttu-id="5e995-109">SetPropertiesForDefaultAppDomain (méthode)</span><span class="sxs-lookup"><span data-stu-id="5e995-109">SetPropertiesForDefaultAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|<span data-ttu-id="5e995-110">Définit les propriétés qui servira à initialiser le domaine d’application par défaut.</span><span class="sxs-lookup"><span data-stu-id="5e995-110">Sets properties that will be used to initialize the default application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e995-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="5e995-111">Remarks</span></span>  
 <span data-ttu-id="5e995-112">Pour obtenir une instance de cette interface, appelez le [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) méthode avec le type de gestionnaire IID `IID_ICLRDomainManager`.</span><span class="sxs-lookup"><span data-stu-id="5e995-112">To get an instance of this interface, call the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method with the manager type IID `IID_ICLRDomainManager`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e995-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5e995-113">Requirements</span></span>  
 <span data-ttu-id="5e995-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e995-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e995-115">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="5e995-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5e995-116">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5e995-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5e995-117">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e995-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e995-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e995-118">See Also</span></span>  
 [<span data-ttu-id="5e995-119">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="5e995-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="5e995-120">Hébergement d’applications WPF</span><span class="sxs-lookup"><span data-stu-id="5e995-120">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
