---
title: COR_VERSION, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_VERSION
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_VERSION
helpviewer_keywords: COR_VERSION structure [.NET Framework debugging]
ms.assetid: 5efaee1c-a001-4c73-9525-4160f4c71567
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b527cb9175315af98a9ad4e9be06d459ad6e188e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corversion-structure"></a><span data-ttu-id="a2a6d-102">COR_VERSION, structure</span><span class="sxs-lookup"><span data-stu-id="a2a6d-102">COR_VERSION Structure</span></span>
<span data-ttu-id="a2a6d-103">Stocke le numéro de version en quatre parties du CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="a2a6d-103">Stores the standard four-part version number of the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2a6d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2a6d-104">Syntax</span></span>  
  
```  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="a2a6d-105">Membres</span><span class="sxs-lookup"><span data-stu-id="a2a6d-105">Members</span></span>  
  
|<span data-ttu-id="a2a6d-106">Membre</span><span class="sxs-lookup"><span data-stu-id="a2a6d-106">Member</span></span>|<span data-ttu-id="a2a6d-107">Description</span><span class="sxs-lookup"><span data-stu-id="a2a6d-107">Description</span></span>|  
|------------|-----------------|  
|`dwMajor`|<span data-ttu-id="a2a6d-108">Numéro de version principale.</span><span class="sxs-lookup"><span data-stu-id="a2a6d-108">The major version number.</span></span>|  
|`dwMinor`|<span data-ttu-id="a2a6d-109">Numéro de version secondaire.</span><span class="sxs-lookup"><span data-stu-id="a2a6d-109">The minor version number.</span></span>|  
|`dwBuild`|<span data-ttu-id="a2a6d-110">Le numéro de build.</span><span class="sxs-lookup"><span data-stu-id="a2a6d-110">The build number.</span></span>|  
|`dwSubBuild`|<span data-ttu-id="a2a6d-111">Numéro de version secondaire.</span><span class="sxs-lookup"><span data-stu-id="a2a6d-111">The sub-build number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2a6d-112">Notes</span><span class="sxs-lookup"><span data-stu-id="a2a6d-112">Remarks</span></span>  
 <span data-ttu-id="a2a6d-113">Si le numéro de version est 1.0.3705.288, 1 est le numéro de version majeure, 0 est le numéro de version secondaire, 3705 est le numéro de build et 288 est le numéro de version secondaire.</span><span class="sxs-lookup"><span data-stu-id="a2a6d-113">If the version number is 1.0.3705.288, 1 is the major version number, 0 is the minor version number, 3705 is the build number, and 288 is the sub-build number.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2a6d-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a2a6d-114">Requirements</span></span>  
 <span data-ttu-id="a2a6d-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2a6d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2a6d-116">**En-tête :** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="a2a6d-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="a2a6d-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2a6d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2a6d-118">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2a6d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2a6d-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2a6d-119">See Also</span></span>  
 [<span data-ttu-id="a2a6d-120">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="a2a6d-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="a2a6d-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="a2a6d-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
