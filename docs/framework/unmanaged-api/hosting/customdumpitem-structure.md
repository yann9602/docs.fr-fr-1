---
title: CustomDumpItem, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CustomDumpItem
api_location: mscoree.dll
api_type: COM
f1_keywords: CustomDumpItem
helpviewer_keywords: CustomDumpItem structure [.NET Framework hosting]
ms.assetid: fd9085ff-7beb-4c38-97f0-037cd8ba4f65
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 547204385b20d5b7e64bda9ea0a9e790f2ba3471
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="ab0a5-102">CustomDumpItem, structure</span><span class="sxs-lookup"><span data-stu-id="ab0a5-102">CustomDumpItem Structure</span></span>
<span data-ttu-id="ab0a5-103">Décrit un élément à ajouter à un dump personnalisé dans le rapport d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="ab0a5-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab0a5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab0a5-104">Syntax</span></span>  
  
```  
struct {  
    ECustomDumpItemKind itemKind;   
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="ab0a5-105">Membres</span><span class="sxs-lookup"><span data-stu-id="ab0a5-105">Members</span></span>  
  
|<span data-ttu-id="ab0a5-106">Membre</span><span class="sxs-lookup"><span data-stu-id="ab0a5-106">Member</span></span>|<span data-ttu-id="ab0a5-107">Description</span><span class="sxs-lookup"><span data-stu-id="ab0a5-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="ab0a5-108">Un [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) valeur qui indique le type d’élément à ajouter.</span><span class="sxs-lookup"><span data-stu-id="ab0a5-108">An [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="ab0a5-109">Actuellement non utilisé.</span><span class="sxs-lookup"><span data-stu-id="ab0a5-109">Not currently used.</span></span> <span data-ttu-id="ab0a5-110">Les éléments ajoutés à l’union doivent être non supérieure à la taille du pointeur.</span><span class="sxs-lookup"><span data-stu-id="ab0a5-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="ab0a5-111">Si un `struct` est nécessaire, vous devez allouer séparément et pointer sur elle.</span><span class="sxs-lookup"><span data-stu-id="ab0a5-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab0a5-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="ab0a5-112">Remarks</span></span>  
 <span data-ttu-id="ab0a5-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) prend un paramètre de type `CustomDumpItem`.</span><span class="sxs-lookup"><span data-stu-id="ab0a5-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab0a5-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ab0a5-114">Requirements</span></span>  
 <span data-ttu-id="ab0a5-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab0a5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab0a5-116">**En-tête :** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="ab0a5-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="ab0a5-117">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ab0a5-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ab0a5-118">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab0a5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab0a5-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab0a5-119">See Also</span></span>  
 [<span data-ttu-id="ab0a5-120">Structures d’hébergement</span><span class="sxs-lookup"><span data-stu-id="ab0a5-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
