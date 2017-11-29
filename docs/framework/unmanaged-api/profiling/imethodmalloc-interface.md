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
ms.openlocfilehash: d246f329f80a76d2c93190fd663c7362418385f7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="d1b9d-102">IMethodMalloc, interface</span><span class="sxs-lookup"><span data-stu-id="d1b9d-102">IMethodMalloc Interface</span></span>
<span data-ttu-id="d1b9d-103">Fournit une méthode pour allouer de la mémoire pour un nouveau corps de fonction MSIL (intermediate language).</span><span class="sxs-lookup"><span data-stu-id="d1b9d-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1b9d-104">Le `IMethodMalloc` interface est un allocateur de mémoire simple.</span><span class="sxs-lookup"><span data-stu-id="d1b9d-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="d1b9d-105">Elle permet à allouer de la mémoire, mais ne pas pour le libérer.</span><span class="sxs-lookup"><span data-stu-id="d1b9d-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d1b9d-106">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d1b9d-106">Methods</span></span>  
  
|<span data-ttu-id="d1b9d-107">Méthode</span><span class="sxs-lookup"><span data-stu-id="d1b9d-107">Method</span></span>|<span data-ttu-id="d1b9d-108">Description</span><span class="sxs-lookup"><span data-stu-id="d1b9d-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d1b9d-109">Alloc (méthode)</span><span class="sxs-lookup"><span data-stu-id="d1b9d-109">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|<span data-ttu-id="d1b9d-110">Tente d’allouer une quantité de mémoire spécifiée pour un nouveau corps de fonction MSIL.</span><span class="sxs-lookup"><span data-stu-id="d1b9d-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1b9d-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="d1b9d-111">Remarks</span></span>  
 <span data-ttu-id="d1b9d-112">Chaque allocateur est spécifique au module et garantit que le corps de fonction sera à un offset positif à partir de la base du module.</span><span class="sxs-lookup"><span data-stu-id="d1b9d-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="d1b9d-113">Mémoire au-dessus de la base d’un module peut être précieuse, donc l’allocateur doit être utilisé pour allouer de la mémoire uniquement pour un corps de fonction.</span><span class="sxs-lookup"><span data-stu-id="d1b9d-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1b9d-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d1b9d-114">Requirements</span></span>  
 <span data-ttu-id="d1b9d-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1b9d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1b9d-116">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d1b9d-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d1b9d-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1b9d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1b9d-118">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1b9d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1b9d-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1b9d-119">See Also</span></span>  
 [<span data-ttu-id="d1b9d-120">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="d1b9d-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
