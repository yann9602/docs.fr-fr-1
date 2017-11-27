---
title: ClrCreateManagedInstance, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ClrCreateManagedInstance
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: ClrCreateManagedInstance
helpviewer_keywords: ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2d27a881f84121f0d096eae7c693dec5b674caec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="clrcreatemanagedinstance-function"></a><span data-ttu-id="dbb8a-102">ClrCreateManagedInstance, fonction</span><span class="sxs-lookup"><span data-stu-id="dbb8a-102">ClrCreateManagedInstance Function</span></span>
<span data-ttu-id="dbb8a-103">Crée une instance du type managé spécifié.</span><span class="sxs-lookup"><span data-stu-id="dbb8a-103">Creates an instance of the specified managed type.</span></span>  
  
 <span data-ttu-id="dbb8a-104">Cette fonction est déconseillée dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dbb8a-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="dbb8a-105">Utilisez l’activation COM pour créer une instance du type managé ou utilisez l’hébergement (consultez [CLR Interfaces d’hébergement ajoutées dans le .NET Framework 4 et 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span><span class="sxs-lookup"><span data-stu-id="dbb8a-105">Use COM activation to create an instance of the managed type, or use hosting (see [CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbb8a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dbb8a-106">Syntax</span></span>  
  
```  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,   
    [in]  REFIID   riid,   
    [out] void     **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dbb8a-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dbb8a-107">Parameters</span></span>  
 `pTypeName`  
 <span data-ttu-id="dbb8a-108">[in] Pointeur vers le nom de type de l’instance demandé.</span><span class="sxs-lookup"><span data-stu-id="dbb8a-108">[in] A pointer to the name of the instance type being requested.</span></span>  
  
 `riid`  
 <span data-ttu-id="dbb8a-109">[in] Le `IID` type de l’instance demandé.</span><span class="sxs-lookup"><span data-stu-id="dbb8a-109">[in] The `IID` of the instance type being requested.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="dbb8a-110">[out] Pointeur vers un pointeur vers une instance du type managé qui a été demandée par l’appelant.</span><span class="sxs-lookup"><span data-stu-id="dbb8a-110">[out] A pointer to a pointer to an instance of the managed type that was requested by the caller.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dbb8a-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="dbb8a-111">Remarks</span></span>  
 <span data-ttu-id="dbb8a-112">Le common language runtime doit déjà être chargé dans un processus.</span><span class="sxs-lookup"><span data-stu-id="dbb8a-112">The common language runtime should already be loaded into a process.</span></span> <span data-ttu-id="dbb8a-113">Par exemple, il peut être chargé à l’aide d’un appel à la [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) fonctionner avant du `ClrCreateManagedInstance` est appelée.</span><span class="sxs-lookup"><span data-stu-id="dbb8a-113">For example, it can be loaded by using a call to the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function before the `ClrCreateManagedInstance` function is called.</span></span> <span data-ttu-id="dbb8a-114">Si le runtime n’est pas chargé, `ClrCreateManagedInstance` tente d’abord charger la version v1.0.3705 du runtime.</span><span class="sxs-lookup"><span data-stu-id="dbb8a-114">If the runtime is not loaded, `ClrCreateManagedInstance` first tries to load v1.0.3705 of the runtime.</span></span> <span data-ttu-id="dbb8a-115">En cas d’échec, il tente de charger la dernière version du runtime.</span><span class="sxs-lookup"><span data-stu-id="dbb8a-115">If that fails, it attempts to load the latest version of the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbb8a-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="dbb8a-116">Requirements</span></span>  
 <span data-ttu-id="dbb8a-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbb8a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbb8a-118">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dbb8a-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dbb8a-119">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dbb8a-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dbb8a-120">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbb8a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbb8a-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dbb8a-121">See Also</span></span>  
 [<span data-ttu-id="dbb8a-122">Fonctions d’hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="dbb8a-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
 [<span data-ttu-id="dbb8a-123">Hébergement d’applications WPF</span><span class="sxs-lookup"><span data-stu-id="dbb8a-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
