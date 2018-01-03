---
title: CLR_DEBUGGING_VERSION, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLR_DEBUGGING_VERSION
api_location: mscordbi.dll
api_type: COM
f1_keywords: CLR_DEBUGGING_VERSION
helpviewer_keywords: CLR_DEBUGGING_VERSION structure [.NET Framework debugging]
ms.assetid: 4d821186-3ddf-405a-ac44-d79438a9f7f3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 092024f3f4e6fc1bc923ae2a299c5d9c21f1b1b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="clrdebuggingversion-structure"></a><span data-ttu-id="56c3a-102">CLR_DEBUGGING_VERSION, structure</span><span class="sxs-lookup"><span data-stu-id="56c3a-102">CLR_DEBUGGING_VERSION Structure</span></span>
<span data-ttu-id="56c3a-103">Définit la version du produit de CLR (Common Language Runtime) à des fins de débogage.</span><span class="sxs-lookup"><span data-stu-id="56c3a-103">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56c3a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56c3a-104">Syntax</span></span>  
  
```  
Typedef struct _CLR_DEBUGGING_VERSION  
{  
WORD wStructVersion;  
WORD wMajor;   
WORD wMinor;  
WORD wBuild;  
WORD wRevision;  
}  CLR_DEBUGGING_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="56c3a-105">Membres</span><span class="sxs-lookup"><span data-stu-id="56c3a-105">Members</span></span>  
  
|<span data-ttu-id="56c3a-106">Membre</span><span class="sxs-lookup"><span data-stu-id="56c3a-106">Member</span></span>|<span data-ttu-id="56c3a-107">Description</span><span class="sxs-lookup"><span data-stu-id="56c3a-107">Description</span></span>|  
|------------|-----------------|  
|`wStructVersion`|<span data-ttu-id="56c3a-108">Le numéro de version de structure</span><span class="sxs-lookup"><span data-stu-id="56c3a-108">The structure version number</span></span>|  
|`wMajor`|<span data-ttu-id="56c3a-109">Numéro de version principale.</span><span class="sxs-lookup"><span data-stu-id="56c3a-109">The major version number.</span></span>|  
|`wMinor`|<span data-ttu-id="56c3a-110">Numéro de version secondaire.</span><span class="sxs-lookup"><span data-stu-id="56c3a-110">The minor version number.</span></span>|  
|`wBuild`|<span data-ttu-id="56c3a-111">Le numéro de build.</span><span class="sxs-lookup"><span data-stu-id="56c3a-111">The build number.</span></span>|  
|`wRevision`|<span data-ttu-id="56c3a-112">Le numéro de révision.</span><span class="sxs-lookup"><span data-stu-id="56c3a-112">The revision number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56c3a-113">Notes</span><span class="sxs-lookup"><span data-stu-id="56c3a-113">Remarks</span></span>  
 <span data-ttu-id="56c3a-114">Le `CLR_DEBUGGING_VERSION` structure est la même que la structure COR_VERSION, toutefois, le `CLR_DEBUGGING_VERSION` structure fournit un champ de version de structure supplémentaire (`wStructVersion`).</span><span class="sxs-lookup"><span data-stu-id="56c3a-114">The `CLR_DEBUGGING_VERSION` structure is the same as the COR_VERSION structure, however, the `CLR_DEBUGGING_VERSION` structure provides an additional structure version field (`wStructVersion`).</span></span> <span data-ttu-id="56c3a-115">Actuellement, ce champ doit être défini à zéro.</span><span class="sxs-lookup"><span data-stu-id="56c3a-115">Currently, this field must be set to zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56c3a-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="56c3a-116">Requirements</span></span>  
 <span data-ttu-id="56c3a-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56c3a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56c3a-118">**En-tête :** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="56c3a-118">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="56c3a-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56c3a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56c3a-120">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56c3a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56c3a-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56c3a-121">See Also</span></span>  
 [<span data-ttu-id="56c3a-122">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="56c3a-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="56c3a-123">Débogage</span><span class="sxs-lookup"><span data-stu-id="56c3a-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
