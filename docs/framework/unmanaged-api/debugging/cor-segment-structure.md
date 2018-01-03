---
title: COR_SEGMENT, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_SEGMENT
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_SEGMENT
helpviewer_keywords: COR_SEGMENT structure [.NET Framework debugging]
ms.assetid: 93aeecb9-7fef-4545-8daf-f566dfc47084
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9414aa1c36ba059d9ee1101f6183dc8a669f9e6f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corsegment-structure"></a><span data-ttu-id="9641d-102">COR_SEGMENT, structure</span><span class="sxs-lookup"><span data-stu-id="9641d-102">COR_SEGMENT Structure</span></span>
<span data-ttu-id="9641d-103">Contient des informations sur une région de la mémoire dans le tas managé.</span><span class="sxs-lookup"><span data-stu-id="9641d-103">Contains information about a region of memory in the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9641d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9641d-104">Syntax</span></span>  
  
```  
typedef struct _COR_SEGMENT {  
    CORDB_ADDRESS start;            
    CORDB_ADDRESS end;              
    CorDebugGenerationTypes gen;    
    ULONG heap;                     
} COR_SEGMENT;  
```  
  
## <a name="members"></a><span data-ttu-id="9641d-105">Membres</span><span class="sxs-lookup"><span data-stu-id="9641d-105">Members</span></span>  
  
|<span data-ttu-id="9641d-106">Membre</span><span class="sxs-lookup"><span data-stu-id="9641d-106">Member</span></span>|<span data-ttu-id="9641d-107">Description</span><span class="sxs-lookup"><span data-stu-id="9641d-107">Description</span></span>|  
|------------|-----------------|  
|`start`|<span data-ttu-id="9641d-108">Adresse de départ de la région de mémoire.</span><span class="sxs-lookup"><span data-stu-id="9641d-108">The starting address of the memory region.</span></span>|  
|`end`|<span data-ttu-id="9641d-109">L’adresse de fin de la région de mémoire.</span><span class="sxs-lookup"><span data-stu-id="9641d-109">The ending address of the memory region.</span></span>|  
|`gen`|<span data-ttu-id="9641d-110">A [CorDebugGenerationTypes](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md) membre d’énumération qui indique la génération de la région de mémoire.</span><span class="sxs-lookup"><span data-stu-id="9641d-110">A [CorDebugGenerationTypes](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md) enumeration member that indicates the generation of the memory region.</span></span>|  
|`heap`|<span data-ttu-id="9641d-111">Le numéro de segment de mémoire dans lequel réside la région de mémoire.</span><span class="sxs-lookup"><span data-stu-id="9641d-111">The heap number in which the memory region resides.</span></span> <span data-ttu-id="9641d-112">Pour plus d'informations, consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="9641d-112">See the Remarks section for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9641d-113">Notes</span><span class="sxs-lookup"><span data-stu-id="9641d-113">Remarks</span></span>  
 <span data-ttu-id="9641d-114">Le `COR_SEGMENTS` structure représente une région de mémoire dans le tas managé.</span><span class="sxs-lookup"><span data-stu-id="9641d-114">The `COR_SEGMENTS` structure represents a region of memory in the managed heap.</span></span>  <span data-ttu-id="9641d-115">`COR_SEGMENTS`les objets sont membres de la [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) objet de collection, qui est remplie en appelant le[ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="9641d-115">`COR_SEGMENTS` objects are members of the [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) collection object, which is populated by calling the[ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) method.</span></span>  
  
 <span data-ttu-id="9641d-116">Le `heap` champ est le nombre de processeur, ce qui correspond au segment de mémoire signalée.</span><span class="sxs-lookup"><span data-stu-id="9641d-116">The `heap` field is the processor number, which corresponds to the heap being reported.</span></span> <span data-ttu-id="9641d-117">Pour la station de travail des garbage collectors, sa valeur est toujours égal à zéro, car les stations de travail ont uniquement un tas de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="9641d-117">For workstation garbage collectors, its value is always zero, because workstations have only one garbage collection heap.</span></span> <span data-ttu-id="9641d-118">Pour le serveur des garbage collectors, sa valeur correspond au processeur d’à que tas est attaché.</span><span class="sxs-lookup"><span data-stu-id="9641d-118">For server garbage collectors, its value corresponds to the processor the heap is attached to.</span></span> <span data-ttu-id="9641d-119">Notez qu’il existe peut-être plus ou moins le garbage collection segments de mémoire qu’il ne sont processeurs réelles en raison des détails d’implémentation du garbage collector.</span><span class="sxs-lookup"><span data-stu-id="9641d-119">Note that there may be more or fewer garbage collection heaps than there are actual processors due to the implementation details of the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9641d-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9641d-120">Requirements</span></span>  
 <span data-ttu-id="9641d-121">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9641d-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9641d-122">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9641d-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9641d-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9641d-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9641d-124">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9641d-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9641d-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9641d-125">See Also</span></span>  
 [<span data-ttu-id="9641d-126">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="9641d-126">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="9641d-127">Débogage</span><span class="sxs-lookup"><span data-stu-id="9641d-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
