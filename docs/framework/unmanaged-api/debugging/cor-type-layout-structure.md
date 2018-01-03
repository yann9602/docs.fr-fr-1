---
title: COR_TYPE_LAYOUT, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_TYPE_LAYOUT
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_TYPE_LAYOUT
helpviewer_keywords: COR_TYPE_LAYOUT structure [.NET Framework debugging]
ms.assetid: 43a7addd-f25a-4049-9907-abec3eb17af2
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 250d78dd9983b75fa7e1b3cfd99215160fbc2b1d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="cortypelayout-structure"></a><span data-ttu-id="d4614-102">COR_TYPE_LAYOUT, structure</span><span class="sxs-lookup"><span data-stu-id="d4614-102">COR_TYPE_LAYOUT Structure</span></span>
<span data-ttu-id="d4614-103">Fournit des informations sur la disposition d'un objet en mémoire.</span><span class="sxs-lookup"><span data-stu-id="d4614-103">Provides information about the layout of an object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4614-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4614-104">Syntax</span></span>  
  
```  
typedef struct COR_TYPE_LAYOUT {  
    COR_TYPEID parentID;  
    ULONG32 objectSize;  
    ULONG32 numFields;  
    ULONG32 boxOffset;  
    CorElementType type;  
} COR_TYPE_LAYOUT;  
```  
  
## <a name="members"></a><span data-ttu-id="d4614-105">Membres</span><span class="sxs-lookup"><span data-stu-id="d4614-105">Members</span></span>  
  
|<span data-ttu-id="d4614-106">Membre</span><span class="sxs-lookup"><span data-stu-id="d4614-106">Member</span></span>|<span data-ttu-id="d4614-107">Description</span><span class="sxs-lookup"><span data-stu-id="d4614-107">Description</span></span>|  
|------------|-----------------|  
|`parentID`|<span data-ttu-id="d4614-108">L’identificateur du type de parent pour ce type.</span><span class="sxs-lookup"><span data-stu-id="d4614-108">The identifier of the parent type to this type.</span></span> <span data-ttu-id="d4614-109">Il s’agit de l’id de type NULL (token1 = 0, token2 = 0) si l’id de type correspond à <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d4614-109">This will be the NULL type id (token1= 0, token2 = 0) if the type id corresponds to <xref:System.Object?displayProperty=nameWithType>.</span></span>|  
|`objectSize`|<span data-ttu-id="d4614-110">La taille de base d’un objet de ce type.</span><span class="sxs-lookup"><span data-stu-id="d4614-110">The base size of an object of this type.</span></span> <span data-ttu-id="d4614-111">Il s’agit de la taille totale des objets de tailles non variable.</span><span class="sxs-lookup"><span data-stu-id="d4614-111">This is the total size for non-variable sized objects.</span></span>|  
|`numFields`|<span data-ttu-id="d4614-112">Le nombre de champs inclus dans les objets de ce type.</span><span class="sxs-lookup"><span data-stu-id="d4614-112">The number of fields included in objects of this type.</span></span>|  
|`boxOffset`|<span data-ttu-id="d4614-113">Si ce type est convertie (boxed), le début du décalage de champs d’un objet.</span><span class="sxs-lookup"><span data-stu-id="d4614-113">If this type is boxed, the beginning offset of an object's fields.</span></span> <span data-ttu-id="d4614-114">Ce champ est valide uniquement pour les types valeur tels que des primitives et les structures.</span><span class="sxs-lookup"><span data-stu-id="d4614-114">This field is valid only for value types such as primitives and structures.</span></span>|  
|`type`|<span data-ttu-id="d4614-115">CorElementType d’à laquelle appartient ce type.</span><span class="sxs-lookup"><span data-stu-id="d4614-115">The CorElementType to which this type belongs.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4614-116">Notes</span><span class="sxs-lookup"><span data-stu-id="d4614-116">Remarks</span></span>  
 <span data-ttu-id="d4614-117">Si `numFields` est supérieure à zéro, vous pouvez appeler la [ICorDebugProcess5::GetTypeFields](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md) méthode pour obtenir des informations sur les champs de ce type.</span><span class="sxs-lookup"><span data-stu-id="d4614-117">If `numFields` is greater than zero, you can call the [ICorDebugProcess5::GetTypeFields](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md) method to obtain information about the fields in this type.</span></span> <span data-ttu-id="d4614-118">Si `type` est `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, ou `ELEMENT_TYPE_SZARRAY`, la taille des objets de ce type est variable, et vous pouvez passer le [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) structure le [ICorDebugProcess5::GetArrayLayout ](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="d4614-118">If `type` is `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, or `ELEMENT_TYPE_SZARRAY`, the size of objects of this type is variable, and you can pass the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) structure to the [ICorDebugProcess5::GetArrayLayout](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4614-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d4614-119">Requirements</span></span>  
 <span data-ttu-id="d4614-120">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4614-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4614-121">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4614-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4614-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4614-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4614-123">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4614-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4614-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4614-124">See Also</span></span>  
 [<span data-ttu-id="d4614-125">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="d4614-125">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="d4614-126">Débogage</span><span class="sxs-lookup"><span data-stu-id="d4614-126">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
