---
title: CLRDataCreateInstance, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLRDataCreateInstance
api_location:
- mscordbi.dll
- mscordacwks.dll
api_type: COM
f1_keywords: CLRDataCreateInstance
helpviewer_keywords: CLRDataCreateInstance function [.NET Framework debugging]
ms.assetid: 440bad90-5a88-45e7-9157-4596801d8d19
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c611cc51417199aae7c595e4edd2e9a5360f0f9c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="clrdatacreateinstance-function"></a><span data-ttu-id="544dd-102">CLRDataCreateInstance, fonction</span><span class="sxs-lookup"><span data-stu-id="544dd-102">CLRDataCreateInstance Function</span></span>
<span data-ttu-id="544dd-103">Crée un objet d’interface pour l’élément cible spécifié.</span><span class="sxs-lookup"><span data-stu-id="544dd-103">Creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="544dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="544dd-104">Syntax</span></span>  
  
```  
HRESULT CLRDataCreateInstance (  
    [in]  REFIID           iid,   
    [in]  ICLRDataTarget  *target,   
    [out] void           **iface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="544dd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="544dd-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="544dd-106">[in] Identificateur de l’interface pour être instancié.</span><span class="sxs-lookup"><span data-stu-id="544dd-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="544dd-107">[in] Un pointeur vers un implémenté par l’utilisateur [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) objet qui représente l’élément cible pour lequel créer l’objet d’interface.</span><span class="sxs-lookup"><span data-stu-id="544dd-107">[in] A pointer to a user-implemented [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="544dd-108">[out] Pointeur vers l’adresse de l’objet d’interface retourné.</span><span class="sxs-lookup"><span data-stu-id="544dd-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="544dd-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="544dd-109">Remarks</span></span>  
 <span data-ttu-id="544dd-110">Le `ICLRDataTarget` objet est implémenté par le writer de l’application de débogage.</span><span class="sxs-lookup"><span data-stu-id="544dd-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="544dd-111">L’implémentation varie selon le type de l’élément cible qui est représenté.</span><span class="sxs-lookup"><span data-stu-id="544dd-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="544dd-112">L’élément cible peut être un processus, vidage de la mémoire, ordinateur distant et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="544dd-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="544dd-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="544dd-113">Requirements</span></span>  
 <span data-ttu-id="544dd-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="544dd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="544dd-115">**En-tête :** ClrData.idl</span><span class="sxs-lookup"><span data-stu-id="544dd-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="544dd-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="544dd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="544dd-117">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="544dd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="544dd-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="544dd-118">See Also</span></span>  
 [<span data-ttu-id="544dd-119">Fonctions statiques globales de débogage</span><span class="sxs-lookup"><span data-stu-id="544dd-119">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
