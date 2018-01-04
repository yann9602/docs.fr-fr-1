---
title: "COR_PRF_CLAUSE_TYPE, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_CLAUSE_TYPE
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_CLAUSE_TYPE
helpviewer_keywords: COR_PRF_CLAUSE_TYPE enumeration [.NET Framework profiling]
ms.assetid: f64c325a-ed3a-4aaf-b847-a88edbc4fefc
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e03b3f2462b8876bfba3cf7d0df40311935722f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corprfclausetype-enumeration"></a><span data-ttu-id="6c25e-102">COR_PRF_CLAUSE_TYPE, énumération</span><span class="sxs-lookup"><span data-stu-id="6c25e-102">COR_PRF_CLAUSE_TYPE Enumeration</span></span>
<span data-ttu-id="6c25e-103">Indique le type de clause d'exception où le code vient d'entrer ou qu'il vient de quitter.</span><span class="sxs-lookup"><span data-stu-id="6c25e-103">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c25e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c25e-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_CLAUSE_NONE = 0,  
    COR_PRF_CLAUSE_FILTER = 1,  
    COR_PRF_CLAUSE_CATCH = 2,  
    COR_PRF_CLAUSE_FINALLY = 3,  
} COR_PRF_CLAUSE_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="6c25e-105">Membres</span><span class="sxs-lookup"><span data-stu-id="6c25e-105">Members</span></span>  
  
|<span data-ttu-id="6c25e-106">Membre</span><span class="sxs-lookup"><span data-stu-id="6c25e-106">Member</span></span>|<span data-ttu-id="6c25e-107">Description</span><span class="sxs-lookup"><span data-stu-id="6c25e-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CLAUSE_NONE`|<span data-ttu-id="6c25e-108">La clause d’exception n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="6c25e-108">The exception clause is not valid.</span></span>|  
|`COR_PRF_CLAUSE_FILTER`|<span data-ttu-id="6c25e-109">La clause d’exception est une expression de filtre.</span><span class="sxs-lookup"><span data-stu-id="6c25e-109">The exception clause is a filter expression.</span></span>|  
|`COR_PRF_CLAUSE_CATCH`|<span data-ttu-id="6c25e-110">La clause d’exception est un `catch` instruction.</span><span class="sxs-lookup"><span data-stu-id="6c25e-110">The exception clause is a `catch` statement.</span></span>|  
|`COR_PRF_CLAUSE_FINALLY`|<span data-ttu-id="6c25e-111">La clause d’exception est un `finally` instruction.</span><span class="sxs-lookup"><span data-stu-id="6c25e-111">The exception clause is a `finally` statement.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6c25e-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6c25e-112">Requirements</span></span>  
 <span data-ttu-id="6c25e-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c25e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c25e-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6c25e-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6c25e-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c25e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c25e-116">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c25e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c25e-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c25e-117">See Also</span></span>  
 [<span data-ttu-id="6c25e-118">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="6c25e-118">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
