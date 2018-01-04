---
title: COR_PRF_FUNCTION, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_FUNCTION
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_FUNCTION
helpviewer_keywords: COR_PRF_FUNCTION structure [.NET Framework profiling]
ms.assetid: 8bb5acf5-cf4b-4ccb-93f1-46db1f3f8bf3
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 15ef81f07438a7cc18f7a131ee8cf9c50c47eb6d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corprffunction-structure"></a><span data-ttu-id="1e5bb-102">COR_PRF_FUNCTION, structure</span><span class="sxs-lookup"><span data-stu-id="1e5bb-102">COR_PRF_FUNCTION Structure</span></span>
<span data-ttu-id="1e5bb-103">Fournit une représentation unique d'une fonction en combinant son ID avec l'ID de sa version recompilée.</span><span class="sxs-lookup"><span data-stu-id="1e5bb-103">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e5bb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e5bb-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION {    FunctionID functionId;    ReJITID    reJitId;} COR_PRF_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="1e5bb-105">Membres</span><span class="sxs-lookup"><span data-stu-id="1e5bb-105">Members</span></span>  
  
|<span data-ttu-id="1e5bb-106">Membre</span><span class="sxs-lookup"><span data-stu-id="1e5bb-106">Member</span></span>|<span data-ttu-id="1e5bb-107">Description</span><span class="sxs-lookup"><span data-stu-id="1e5bb-107">Description</span></span>|  
|------------|-----------------|  
|`functionId`|<span data-ttu-id="1e5bb-108">L’ID de la fonction.</span><span class="sxs-lookup"><span data-stu-id="1e5bb-108">The ID of the function.</span></span>|  
|`reJitId`|<span data-ttu-id="1e5bb-109">L’ID de la fonction recompilée.</span><span class="sxs-lookup"><span data-stu-id="1e5bb-109">The ID of the recompiled function.</span></span> <span data-ttu-id="1e5bb-110">La valeur 0 (zéro) représente la version d’origine de la fonction.</span><span class="sxs-lookup"><span data-stu-id="1e5bb-110">A value of 0 (zero) represents the original version of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e5bb-111">Notes</span><span class="sxs-lookup"><span data-stu-id="1e5bb-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e5bb-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1e5bb-112">Requirements</span></span>  
 <span data-ttu-id="1e5bb-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e5bb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e5bb-114">**En-tête :** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="1e5bb-114">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="1e5bb-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1e5bb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e5bb-116">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e5bb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e5bb-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1e5bb-117">See Also</span></span>  
 [<span data-ttu-id="1e5bb-118">Structures de profilage</span><span class="sxs-lookup"><span data-stu-id="1e5bb-118">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
