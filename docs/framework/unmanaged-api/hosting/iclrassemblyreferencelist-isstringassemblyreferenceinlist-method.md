---
title: "ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyReferenceList.IsStringAssemblyReferenceInList
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList method [.NET Framework hosting]
- IsStringAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: e6121cc3-2f11-42c7-bdae-47808581ff71
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ff0e51327e0e66c2a282ebf46e6036f81d3d568b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyreferencelistisstringassemblyreferenceinlist-method"></a><span data-ttu-id="b40d4-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList, méthode</span><span class="sxs-lookup"><span data-stu-id="b40d4-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Method</span></span>
<span data-ttu-id="b40d4-103">Obtient une valeur qui indique si le nom fourni correspond au nom d’un assembly dans la liste.</span><span class="sxs-lookup"><span data-stu-id="b40d4-103">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b40d4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b40d4-104">Syntax</span></span>  
  
```  
HRESULT IsStringAssemblyReferenceInList (  
    [in] LPCWSTR pwzAssemblyName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b40d4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b40d4-105">Parameters</span></span>  
 `pwzAssemblyName`  
 <span data-ttu-id="b40d4-106">[in] Le nom de l’assembly à rechercher.</span><span class="sxs-lookup"><span data-stu-id="b40d4-106">[in] The name of the assembly for which to search.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b40d4-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b40d4-107">Return Value</span></span>  
  
|<span data-ttu-id="b40d4-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b40d4-108">HRESULT</span></span>|<span data-ttu-id="b40d4-109">Description</span><span class="sxs-lookup"><span data-stu-id="b40d4-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b40d4-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b40d4-110">S_OK</span></span>|<span data-ttu-id="b40d4-111">La chaîne apparaît dans la liste.</span><span class="sxs-lookup"><span data-stu-id="b40d4-111">The string appears in the list.</span></span>|  
|<span data-ttu-id="b40d4-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b40d4-112">S_FALSE</span></span>|<span data-ttu-id="b40d4-113">La chaîne n’apparaît pas dans la liste.</span><span class="sxs-lookup"><span data-stu-id="b40d4-113">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="b40d4-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b40d4-114">E_FAIL</span></span>|<span data-ttu-id="b40d4-115">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="b40d4-115">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b40d4-116">Une fois une méthode retourne E_FAIL, le common language runtime n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="b40d4-116">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="b40d4-117">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b40d4-117">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b40d4-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b40d4-118">Requirements</span></span>  
 <span data-ttu-id="b40d4-119">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b40d4-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b40d4-120">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b40d4-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b40d4-121">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b40d4-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b40d4-122">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b40d4-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b40d4-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b40d4-123">See Also</span></span>  
 [<span data-ttu-id="b40d4-124">ICLRAssemblyIdentityManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="b40d4-124">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="b40d4-125">ICLRAssemblyReferenceList (Interface)</span><span class="sxs-lookup"><span data-stu-id="b40d4-125">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="b40d4-126">IHostAssemblyManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="b40d4-126">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="b40d4-127">IHostAssemblyStore (Interface)</span><span class="sxs-lookup"><span data-stu-id="b40d4-127">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
