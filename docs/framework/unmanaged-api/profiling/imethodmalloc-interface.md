---
title: IMethodMalloc, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMethodMalloc
api_location: mscorwks.dll
api_type: COM
f1_keywords: IMethodMalloc
helpviewer_keywords: IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1941a46a60219d9dd56d162f89baf268f220c102
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="7bcd1-102">IMethodMalloc, interface</span><span class="sxs-lookup"><span data-stu-id="7bcd1-102">IMethodMalloc Interface</span></span>
<span data-ttu-id="7bcd1-103">Fournit une méthode pour allouer de la mémoire pour un nouveau corps de fonction MSIL (intermediate language).</span><span class="sxs-lookup"><span data-stu-id="7bcd1-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7bcd1-104">Le `IMethodMalloc` interface est un allocateur de mémoire simple.</span><span class="sxs-lookup"><span data-stu-id="7bcd1-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="7bcd1-105">Elle permet à allouer de la mémoire, mais ne pas pour le libérer.</span><span class="sxs-lookup"><span data-stu-id="7bcd1-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7bcd1-106">Méthodes</span><span class="sxs-lookup"><span data-stu-id="7bcd1-106">Methods</span></span>  
  
|<span data-ttu-id="7bcd1-107">Méthode</span><span class="sxs-lookup"><span data-stu-id="7bcd1-107">Method</span></span>|<span data-ttu-id="7bcd1-108">Description</span><span class="sxs-lookup"><span data-stu-id="7bcd1-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7bcd1-109">Alloc, méthode</span><span class="sxs-lookup"><span data-stu-id="7bcd1-109">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|<span data-ttu-id="7bcd1-110">Tente d’allouer une quantité de mémoire spécifiée pour un nouveau corps de fonction MSIL.</span><span class="sxs-lookup"><span data-stu-id="7bcd1-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bcd1-111">Notes</span><span class="sxs-lookup"><span data-stu-id="7bcd1-111">Remarks</span></span>  
 <span data-ttu-id="7bcd1-112">Chaque allocateur est spécifique au module et garantit que le corps de fonction sera à un offset positif à partir de la base du module.</span><span class="sxs-lookup"><span data-stu-id="7bcd1-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="7bcd1-113">Mémoire au-dessus de la base d’un module peut être précieuse, donc l’allocateur doit être utilisé pour allouer de la mémoire uniquement pour un corps de fonction.</span><span class="sxs-lookup"><span data-stu-id="7bcd1-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bcd1-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7bcd1-114">Requirements</span></span>  
 <span data-ttu-id="7bcd1-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bcd1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bcd1-116">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7bcd1-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7bcd1-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7bcd1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7bcd1-118">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bcd1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bcd1-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7bcd1-119">See Also</span></span>  
 [<span data-ttu-id="7bcd1-120">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="7bcd1-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
