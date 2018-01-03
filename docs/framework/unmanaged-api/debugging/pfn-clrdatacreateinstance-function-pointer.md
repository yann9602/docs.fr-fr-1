---
title: PFN_CLRDataCreateInstance (pointeur fonction)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: PFN_CLRDataCreateInstance
api_location: mscordbi.dll
api_type: COM
f1_keywords: PFN_CLRDataCreateInstance
helpviewer_keywords: PFN_CLRDataCreateInstance function pointer [.NET Framework debugging]
ms.assetid: 5c66ac57-d751-4de5-af9f-26ceb949af8b
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 98a966434332549d9ceb7f29de81e19fa1b2108f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="pfnclrdatacreateinstance-function-pointer"></a><span data-ttu-id="c1abe-102">PFN_CLRDataCreateInstance (pointeur fonction)</span><span class="sxs-lookup"><span data-stu-id="c1abe-102">PFN_CLRDataCreateInstance Function Pointer</span></span>
<span data-ttu-id="c1abe-103">Pointe vers une fonction qui crée un objet d’interface pour l’élément cible spécifié.</span><span class="sxs-lookup"><span data-stu-id="c1abe-103">Points to a function that creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1abe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1abe-104">Syntax</span></span>  
  
```  
typedef HRESULT (STDAPICALLTYPE* PFN_CLRDataCreateInstance) (  
    [in]  REFIID           iid,  
    [in]  ICLRDataTarget  *target,  
    [out] void           **iface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c1abe-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c1abe-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="c1abe-106">[in] Identificateur de l’interface pour être instancié.</span><span class="sxs-lookup"><span data-stu-id="c1abe-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="c1abe-107">[in] Un pointeur vers un implémenté par l’utilisateur [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) objet qui représente l’élément cible pour lequel créer l’objet d’interface.</span><span class="sxs-lookup"><span data-stu-id="c1abe-107">[in] A pointer to a user-implemented [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="c1abe-108">[out] Pointeur vers l’adresse de l’objet d’interface retourné.</span><span class="sxs-lookup"><span data-stu-id="c1abe-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1abe-109">Notes</span><span class="sxs-lookup"><span data-stu-id="c1abe-109">Remarks</span></span>  
 <span data-ttu-id="c1abe-110">Le `ICLRDataTarget` objet est implémenté par le writer de l’application de débogage.</span><span class="sxs-lookup"><span data-stu-id="c1abe-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="c1abe-111">L’implémentation varie selon le type de l’élément cible qui est représenté.</span><span class="sxs-lookup"><span data-stu-id="c1abe-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="c1abe-112">L’élément cible peut être un processus, vidage de la mémoire, ordinateur distant et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="c1abe-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1abe-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c1abe-113">Requirements</span></span>  
 <span data-ttu-id="c1abe-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1abe-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1abe-115">**En-tête :** ClrData.idl</span><span class="sxs-lookup"><span data-stu-id="c1abe-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="c1abe-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1abe-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1abe-117">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1abe-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1abe-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1abe-118">See Also</span></span>  
 [<span data-ttu-id="c1abe-119">Fonctions statiques globales de débogage</span><span class="sxs-lookup"><span data-stu-id="c1abe-119">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
