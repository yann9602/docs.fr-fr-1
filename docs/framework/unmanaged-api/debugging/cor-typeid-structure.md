---
title: COR_TYPEID, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_TYPEID
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_TYPEID
helpviewer_keywords: COR_TYPEID structure [.NET Framework debugging]
ms.assetid: 1e172b14-ee22-4943-b3b8-3740e7bdcd2e
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ca6c9b3b02314843a3eaf01d8cd4a9eac5513efa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="cortypeid-structure"></a><span data-ttu-id="ec1c1-102">COR_TYPEID, structure</span><span class="sxs-lookup"><span data-stu-id="ec1c1-102">COR_TYPEID Structure</span></span>
<span data-ttu-id="ec1c1-103">Contient un identificateur de type.</span><span class="sxs-lookup"><span data-stu-id="ec1c1-103">Contains a type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec1c1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec1c1-104">Syntax</span></span>  
  
```  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a><span data-ttu-id="ec1c1-105">Membres</span><span class="sxs-lookup"><span data-stu-id="ec1c1-105">Members</span></span>  
  
|<span data-ttu-id="ec1c1-106">Membre</span><span class="sxs-lookup"><span data-stu-id="ec1c1-106">Member</span></span>|<span data-ttu-id="ec1c1-107">Description</span><span class="sxs-lookup"><span data-stu-id="ec1c1-107">Description</span></span>|  
|------------|-----------------|  
|`token1`|<span data-ttu-id="ec1c1-108">Le premier jeton.</span><span class="sxs-lookup"><span data-stu-id="ec1c1-108">The first token.</span></span>|  
|`token2`|<span data-ttu-id="ec1c1-109">Le deuxième jeton.</span><span class="sxs-lookup"><span data-stu-id="ec1c1-109">The second token.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec1c1-110">Notes</span><span class="sxs-lookup"><span data-stu-id="ec1c1-110">Remarks</span></span>  
 <span data-ttu-id="ec1c1-111">Le `COR_TYPEID` structure est retournée par un nombre de méthodes de débogage qui fournissent des informations sur les objets par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="ec1c1-111">The `COR_TYPEID` structure is returned by a number of debugging methods that provide information about objects to be garbage-collected.</span></span> <span data-ttu-id="ec1c1-112">Elle peut ensuite être passée en tant qu’argument à d’autres méthodes de débogage qui fournissent des informations supplémentaires sur cet élément.</span><span class="sxs-lookup"><span data-stu-id="ec1c1-112">It can then be passed as an argument to other debugging methods that provide additional information about that item.</span></span> <span data-ttu-id="ec1c1-113">Par exemple, en énumérant un [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) de l’objet, vous pouvez récupérer des [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objets qui représentent des objets sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="ec1c1-113">For example, by enumerating an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) object, you can retrieve individual [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects that represent individual objects on the managed heap.</span></span> <span data-ttu-id="ec1c1-114">Vous pouvez ensuite passer le `COR_TYPEID` valeur à partir de la `COR_HEAPOBJECT.type` au champ la [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) méthode pour récupérer un objet ICorDebugType qui fournit des informations de type sur l’objet.</span><span class="sxs-lookup"><span data-stu-id="ec1c1-114">You can then pass the `COR_TYPEID` value from the `COR_HEAPOBJECT.type` field to the [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) method to retrieve an ICorDebugType object that provides type information about the object.</span></span>  
  
 <span data-ttu-id="ec1c1-115">A `COR_TYPEID` objet est destiné à être opaque.</span><span class="sxs-lookup"><span data-stu-id="ec1c1-115">A `COR_TYPEID` object is intended to be opaque.</span></span> <span data-ttu-id="ec1c1-116">Des champs individuels ne doivent pas accessibles ou manipulées.</span><span class="sxs-lookup"><span data-stu-id="ec1c1-116">Its individual fields should not be accessed or manipulated.</span></span> <span data-ttu-id="ec1c1-117">Son utilisation exclusive est celui d’identificateur qui est fourni comme un `out` paramètre dans un appel de méthode et qui peut, à son tour, passer à d’autres méthodes pour fournir des informations supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="ec1c1-117">Its sole use is as an identifier that is provided as an `out` parameter in a method call and that can, in turn, be passed to other methods to provide additional information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec1c1-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ec1c1-118">Requirements</span></span>  
 <span data-ttu-id="ec1c1-119">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec1c1-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec1c1-120">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ec1c1-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ec1c1-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec1c1-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec1c1-122">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec1c1-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec1c1-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec1c1-123">See Also</span></span>  
 [<span data-ttu-id="ec1c1-124">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="ec1c1-124">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="ec1c1-125">Débogage</span><span class="sxs-lookup"><span data-stu-id="ec1c1-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
