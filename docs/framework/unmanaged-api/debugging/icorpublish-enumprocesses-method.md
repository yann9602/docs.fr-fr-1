---
title: "ICorPublish::EnumProcesses, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublish.EnumProcesses
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublish::EnumProcesses
helpviewer_keywords:
- ICorPublish::EnumProcesses method [.NET Framework debugging]
- EnumProcesses method [.NET Framework debugging]
ms.assetid: 4ae765f0-93b2-4b6f-aea1-7b0cf44e04a7
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d7e0af492cbec401d7470502de807033f21e39f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishenumprocesses-method"></a><span data-ttu-id="44468-102">ICorPublish::EnumProcesses, méthode</span><span class="sxs-lookup"><span data-stu-id="44468-102">ICorPublish::EnumProcesses Method</span></span>
<span data-ttu-id="44468-103">Obtient un énumérateur pour les processus managés en cours d’exécution sur cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="44468-103">Gets an enumerator for the managed processes running on this computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44468-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44468-104">Syntax</span></span>  
  
```  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="44468-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="44468-105">Parameters</span></span>  
 `Type`  
 <span data-ttu-id="44468-106">Une valeur de la [COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) énumération qui spécifie le type de processus à récupérer.</span><span class="sxs-lookup"><span data-stu-id="44468-106">A value of the [COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) enumeration that specifies the type of process to be retrieved.</span></span> <span data-ttu-id="44468-107">Dans la version actuelle, seul COR_PUB_MANAGEDONLY est valide.</span><span class="sxs-lookup"><span data-stu-id="44468-107">In the current version, only COR_PUB_MANAGEDONLY is valid.</span></span>  
  
 `ppIEnum`  
 <span data-ttu-id="44468-108">Un pointeur vers l’adresse d’un [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance qui est l’énumérateur des processus.</span><span class="sxs-lookup"><span data-stu-id="44468-108">A pointer to the address of an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that is the enumerator of the processes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44468-109">Notes</span><span class="sxs-lookup"><span data-stu-id="44468-109">Remarks</span></span>  
 <span data-ttu-id="44468-110">Collection de l’énumérateur de processus est basée sur un instantané des processus qui s’exécutent lorsque le `EnumProcesses` méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="44468-110">The enumerator's collection of processes is based on a snapshot of the processes that are running when the `EnumProcesses` method is called.</span></span> <span data-ttu-id="44468-111">L’énumérateur n’inclut pas tous les processus qui se terminer avant ou démarrer après `EnumProcesses` est appelée.</span><span class="sxs-lookup"><span data-stu-id="44468-111">The enumerator will not include any processes that terminate before or start after `EnumProcesses` is called.</span></span>  
  
 <span data-ttu-id="44468-112">Le `EnumProcesses` méthode peut être appelée plusieurs fois sur ce [ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) instance pour créer une nouvelle collection à jour de processus.</span><span class="sxs-lookup"><span data-stu-id="44468-112">The `EnumProcesses` method may be called more than once on this [ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) instance to create a new up-to-date collection of processes.</span></span> <span data-ttu-id="44468-113">Les collections existantes ne seront pas affectées par les appels suivants de la `EnumProcesses` (méthode).</span><span class="sxs-lookup"><span data-stu-id="44468-113">Existing collections will not be affected by subsequent calls of the `EnumProcesses` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44468-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="44468-114">Requirements</span></span>  
 <span data-ttu-id="44468-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44468-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44468-116">**En-tête :** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="44468-116">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="44468-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44468-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44468-118">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44468-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44468-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44468-119">See Also</span></span>  
 [<span data-ttu-id="44468-120">ICorPublish, interface</span><span class="sxs-lookup"><span data-stu-id="44468-120">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
