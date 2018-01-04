---
title: "COR_PRF_STATIC_TYPE, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_STATIC_TYPE
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_STATIC_TYPE
helpviewer_keywords: COR_PRF_STATIC_TYPE enumeration [.NET Framework profiling]
ms.assetid: 441d7809-5b65-41a5-ba64-2910a8008315
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 76d43a620b64c771427cd30af770e70642dabe7a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corprfstatictype-enumeration"></a><span data-ttu-id="adca4-102">COR_PRF_STATIC_TYPE, énumération</span><span class="sxs-lookup"><span data-stu-id="adca4-102">COR_PRF_STATIC_TYPE Enumeration</span></span>
<span data-ttu-id="adca4-103">Indique si un champ est statique et si oui, la qualité statique qui s'y applique.</span><span class="sxs-lookup"><span data-stu-id="adca4-103">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span> <span data-ttu-id="adca4-104">Ces valeurs peuvent être combinées à l’aide de l’opération OR au niveau du bit pour indiquer que le champ a plusieurs qualités statiques différentes.</span><span class="sxs-lookup"><span data-stu-id="adca4-104">These values can be combined using the bitwise OR operation to indicate that the field has multiple, different static qualities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adca4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="adca4-105">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_FIELD_NOT_A_STATIC = 0x0,  
    COR_PRF_FIELD_APP_DOMAIN_STATIC = 0x1,  
    COR_PRF_FIELD_THREAD_STATIC = 0x2,  
    COR_PRF_FIELD_CONTEXT_STATIC = 0x4,  
    COR_PRF_FIELD_RVA_STATIC = 0x8  
} COR_PRF_STATIC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="adca4-106">Membres</span><span class="sxs-lookup"><span data-stu-id="adca4-106">Members</span></span>  
  
|<span data-ttu-id="adca4-107">Membre</span><span class="sxs-lookup"><span data-stu-id="adca4-107">Member</span></span>|<span data-ttu-id="adca4-108">Description</span><span class="sxs-lookup"><span data-stu-id="adca4-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_NOT_A_STATIC`|<span data-ttu-id="adca4-109">Le champ n’est pas statique.</span><span class="sxs-lookup"><span data-stu-id="adca4-109">The field is not static.</span></span>|  
|`COR_PRF_FIELD_APP_DOMAIN_STATIC`|<span data-ttu-id="adca4-110">Le champ est statique de domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="adca4-110">The field is application domain-static.</span></span>|  
|`COR_PRF_FIELD_THREAD_STATIC`|<span data-ttu-id="adca4-111">Le champ est statique de thread.</span><span class="sxs-lookup"><span data-stu-id="adca4-111">The field is thread-static.</span></span>|  
|`COR_PRF_FIELD_CONTEXT_STATIC`|<span data-ttu-id="adca4-112">Le champ est statique de contexte.</span><span class="sxs-lookup"><span data-stu-id="adca4-112">The field is context-static.</span></span>|  
|`COR_PRF_FIELD_RVA_STATIC`|<span data-ttu-id="adca4-113">Le champ est l’adresse virtuelle relative (RVA)-statique.</span><span class="sxs-lookup"><span data-stu-id="adca4-113">The field is relative virtual address (RVA)-static.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="adca4-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="adca4-114">Requirements</span></span>  
 <span data-ttu-id="adca4-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adca4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adca4-116">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="adca4-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="adca4-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="adca4-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="adca4-118">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adca4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adca4-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="adca4-119">See Also</span></span>  
 [<span data-ttu-id="adca4-120">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="adca4-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
