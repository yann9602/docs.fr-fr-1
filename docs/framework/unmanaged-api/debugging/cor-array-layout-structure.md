---
title: COR_ARRAY_LAYOUT, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_ARRAY_LAYOUT
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_ARRAY_LAYOUT
helpviewer_keywords: COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: aa20ac3d-6f60-4aa2-91c5-f3a86f82eba8
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b936b1b2187ec68db7f5fdecb0344e6cac211ab1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corarraylayout-structure"></a><span data-ttu-id="f6c48-102">COR_ARRAY_LAYOUT, structure</span><span class="sxs-lookup"><span data-stu-id="f6c48-102">COR_ARRAY_LAYOUT Structure</span></span>
<span data-ttu-id="f6c48-103">Fournit des informations sur la disposition d'un objet Array en mémoire.</span><span class="sxs-lookup"><span data-stu-id="f6c48-103">Provides information about the layout of an array object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6c48-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6c48-104">Syntax</span></span>  
  
```  
typedef struct COR_ARRAY_LAYOUT {  
    COR_TYPEID componentID;  
    CorElementType componentType;  
    ULONG32 firstElementOffset;  
    ULONG32 elementSize;  
    ULONG32 countOffset;   
    ULONG32 rankSize;   
    ULONG32 numRanks;   
    ULONG32 rankOffset;   
} COR_ARRAY_LAYOUT;  
```  
  
## <a name="members"></a><span data-ttu-id="f6c48-105">Membres</span><span class="sxs-lookup"><span data-stu-id="f6c48-105">Members</span></span>  
  
|<span data-ttu-id="f6c48-106">Membre</span><span class="sxs-lookup"><span data-stu-id="f6c48-106">Member</span></span>|<span data-ttu-id="f6c48-107">Description</span><span class="sxs-lookup"><span data-stu-id="f6c48-107">Description</span></span>|  
|------------|-----------------|  
|`componentID`|<span data-ttu-id="f6c48-108">L’identificateur du type d’objets contenus dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="f6c48-108">The identifier of the type of objects that the array contains.</span></span>|  
|`componentType`|<span data-ttu-id="f6c48-109">Une valeur d’énumération CorElementType qui indique si le composant est une référence de garbage collection, une classe value ou un type primitif.</span><span class="sxs-lookup"><span data-stu-id="f6c48-109">A CorElementType enumeration value that indicates whether the component is a garbage collection reference, a value class, or a primitive.</span></span>|  
|`firstElementOffset`|<span data-ttu-id="f6c48-110">Offset au premier élément du tableau.</span><span class="sxs-lookup"><span data-stu-id="f6c48-110">The offset to the first element in the array.</span></span>|  
|`elementSize`|<span data-ttu-id="f6c48-111">La taille de chaque élément.</span><span class="sxs-lookup"><span data-stu-id="f6c48-111">The size of each element.</span></span>|  
|`countOffset`|<span data-ttu-id="f6c48-112">Offset au nombre d’éléments dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="f6c48-112">The offset to the number of elements in the array.</span></span>|  
|`rankSize`|<span data-ttu-id="f6c48-113">La taille du rang, en octets.</span><span class="sxs-lookup"><span data-stu-id="f6c48-113">The size of the rank, in bytes.</span></span>|  
|`numRanks`|<span data-ttu-id="f6c48-114">Le nombre de rangées dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="f6c48-114">The number of ranks in the array.</span></span>|  
|`rankOffset`|<span data-ttu-id="f6c48-115">Le décalage de départ de rangs.</span><span class="sxs-lookup"><span data-stu-id="f6c48-115">The offset at which the ranks start.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6c48-116">Notes</span><span class="sxs-lookup"><span data-stu-id="f6c48-116">Remarks</span></span>  
 <span data-ttu-id="f6c48-117">Le `rankSize` champ spécifie la taille d’un rang dans un tableau multidimensionnel.</span><span class="sxs-lookup"><span data-stu-id="f6c48-117">The `rankSize` field specifies the size of a rank in a multi-dimensional array.</span></span> <span data-ttu-id="f6c48-118">Elle est correcte pour les tableaux unidimensionnels ainsi.</span><span class="sxs-lookup"><span data-stu-id="f6c48-118">It is accurate for single-dimensional arrays as well.</span></span>  
  
 <span data-ttu-id="f6c48-119">La valeur de `numRanks` est 1 pour un tableau unidimensionnel et `N` pour un tableau multidimensionnel de `N` dimensions.</span><span class="sxs-lookup"><span data-stu-id="f6c48-119">The value of `numRanks` is 1 for a single-dimensional array and `N` for a multi-dimensional array of `N` dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6c48-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f6c48-120">Requirements</span></span>  
 <span data-ttu-id="f6c48-121">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6c48-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6c48-122">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f6c48-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6c48-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6c48-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6c48-124">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6c48-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6c48-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6c48-125">See Also</span></span>  
 [<span data-ttu-id="f6c48-126">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="f6c48-126">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="f6c48-127">Débogage</span><span class="sxs-lookup"><span data-stu-id="f6c48-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
