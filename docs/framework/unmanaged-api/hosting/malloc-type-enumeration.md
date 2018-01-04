---
title: "MALLOC_TYPE (énumération)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: MALLOC_TYPE
api_location: mscoree.dll
api_type: COM
f1_keywords: MALLOC_TYPE
helpviewer_keywords: MALLOC_TYPE Enumeration
ms.assetid: c02476f9-23a2-4af7-9282-aa9c42c7429b
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b3f41f381266c76b267d5d3e366047fe5267c30b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="malloctype-enumeration"></a><span data-ttu-id="9ac64-102">MALLOC_TYPE (énumération)</span><span class="sxs-lookup"><span data-stu-id="9ac64-102">MALLOC_TYPE Enumeration</span></span>
<span data-ttu-id="9ac64-103">Contient des valeurs qui spécifient les caractéristiques de la mémoire est allouée.</span><span class="sxs-lookup"><span data-stu-id="9ac64-103">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ac64-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ac64-104">Syntax</span></span>  
  
```  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="9ac64-105">Membres</span><span class="sxs-lookup"><span data-stu-id="9ac64-105">Members</span></span>  
  
|<span data-ttu-id="9ac64-106">Membre</span><span class="sxs-lookup"><span data-stu-id="9ac64-106">Member</span></span>|<span data-ttu-id="9ac64-107">Description</span><span class="sxs-lookup"><span data-stu-id="9ac64-107">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="9ac64-108">La mémoire allouée peut contenir un fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="9ac64-108">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="9ac64-109">La mémoire allouée est thread-safe.</span><span class="sxs-lookup"><span data-stu-id="9ac64-109">The allocated memory is thread-safe.</span></span> <span data-ttu-id="9ac64-110">Autrement dit, la mémoire est accessible par plusieurs threads sans synchronisation.</span><span class="sxs-lookup"><span data-stu-id="9ac64-110">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="9ac64-111">Si cet indicateur n’est pas défini, les appels sur l’objet doivent être sérialisés.</span><span class="sxs-lookup"><span data-stu-id="9ac64-111">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9ac64-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9ac64-112">Requirements</span></span>  
 <span data-ttu-id="9ac64-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ac64-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ac64-114">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9ac64-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9ac64-115">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9ac64-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ac64-116">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ac64-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ac64-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ac64-117">See Also</span></span>  
 [<span data-ttu-id="9ac64-118">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="9ac64-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
