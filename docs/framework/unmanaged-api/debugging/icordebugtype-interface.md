---
title: ICorDebugType Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType
helpviewer_keywords: ICorDebugType interface [.NET Framework debugging]
ms.assetid: 94e02e31-67ea-4b00-8148-a46740a4571d
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9a25e72766e6647f820c9871e989d4b24db0bf26
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugtype-interface1"></a><span data-ttu-id="0ade2-102">ICorDebugType Interface1</span><span class="sxs-lookup"><span data-stu-id="0ade2-102">ICorDebugType Interface1</span></span>
<span data-ttu-id="0ade2-103">Représente un type, base ou complex (c'est-à-dire défini par l’utilisateur).</span><span class="sxs-lookup"><span data-stu-id="0ade2-103">Represents a type, either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="0ade2-104">Si le type est générique, `ICorDebugType` représente le type générique instancié.</span><span class="sxs-lookup"><span data-stu-id="0ade2-104">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0ade2-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="0ade2-105">Methods</span></span>  
  
|<span data-ttu-id="0ade2-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="0ade2-106">Method</span></span>|<span data-ttu-id="0ade2-107">Description</span><span class="sxs-lookup"><span data-stu-id="0ade2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0ade2-108">EnumerateTypeParameters, méthode</span><span class="sxs-lookup"><span data-stu-id="0ade2-108">EnumerateTypeParameters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-enumeratetypeparameters-method.md)|<span data-ttu-id="0ade2-109">Obtient un pointeur d’interface ICorDebugTypeEnum qui référence l’objet générique <xref:System.Type> les paramètres de la classe référencée par ce `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="0ade2-109">Gets an interface pointer to an ICorDebugTypeEnum that references the generic <xref:System.Type> parameters of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="0ade2-110">GetBase (méthode)</span><span class="sxs-lookup"><span data-stu-id="0ade2-110">GetBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getbase-method.md)|<span data-ttu-id="0ade2-111">Obtient un pointeur d’interface vers un `ICorDebugType` qui fait référence à la classe de base de la classe référencée par ce `ICorDebugType`, s’il en existe.</span><span class="sxs-lookup"><span data-stu-id="0ade2-111">Gets an interface pointer to an `ICorDebugType` that references the base class of the class referenced by this `ICorDebugType`, if one exists.</span></span>|  
|[<span data-ttu-id="0ade2-112">GetClass, méthode</span><span class="sxs-lookup"><span data-stu-id="0ade2-112">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)|<span data-ttu-id="0ade2-113">Obtient un pointeur d’interface vers ICorDebugClass qui référence le constructeur typé de ce `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="0ade2-113">Gets an interface pointer to an ICorDebugClass that references the typed constructor of this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="0ade2-114">GetFirstTypeParameter (méthode)</span><span class="sxs-lookup"><span data-stu-id="0ade2-114">GetFirstTypeParameter Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getfirsttypeparameter-method.md)|<span data-ttu-id="0ade2-115">Obtient un pointeur d’interface vers un `ICorDebugType` qui fait référence à la première générique <xref:System.Type> paramètre du constructeur de la classe référencée par ce `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="0ade2-115">Gets an interface pointer to an `ICorDebugType` that references the first generic <xref:System.Type> parameter for the constructor of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="0ade2-116">GetRank (méthode)</span><span class="sxs-lookup"><span data-stu-id="0ade2-116">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getrank-method.md)|<span data-ttu-id="0ade2-117">Obtient le nombre de dimensions dans un type tableau.</span><span class="sxs-lookup"><span data-stu-id="0ade2-117">Gets the number of dimensions in an array type.</span></span>|  
|[<span data-ttu-id="0ade2-118">GetStaticFieldValue, méthode</span><span class="sxs-lookup"><span data-stu-id="0ade2-118">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)|<span data-ttu-id="0ade2-119">Obtient un pointeur d’interface vers ICorDebugValue qui contient la valeur du champ statique référencé par le champ spécifié de jeton dans le frame de pile spécifié.</span><span class="sxs-lookup"><span data-stu-id="0ade2-119">Gets an interface pointer to an ICorDebugValue that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>|  
|[<span data-ttu-id="0ade2-120">GetType (méthode)</span><span class="sxs-lookup"><span data-stu-id="0ade2-120">GetType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)|<span data-ttu-id="0ade2-121">Obtient une valeur CorElementType qui décrit le type natif du common language runtime <xref:System.Type> référencé par ce `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="0ade2-121">Gets a CorElementType value that describes the native type of the common language runtime <xref:System.Type> referenced by this `ICorDebugType`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ade2-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="0ade2-122">Remarks</span></span>  
 <span data-ttu-id="0ade2-123">Si le type est générique, `ICorDebugClass` représente le type non instancié.</span><span class="sxs-lookup"><span data-stu-id="0ade2-123">If the type is generic, `ICorDebugClass` represents the uninstantiated type.</span></span> <span data-ttu-id="0ade2-124">Le `ICorDebugType` interface représente un type générique instancié.</span><span class="sxs-lookup"><span data-stu-id="0ade2-124">The `ICorDebugType` interface represents an instantiated generic type.</span></span> <span data-ttu-id="0ade2-125">Par exemple, table de hachage\<K, V > serait représenté par `ICorDebugClass`, alors que Hashtable\<Int32, String > serait représenté par `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="0ade2-125">For example, Hashtable\<K, V> would be represented by `ICorDebugClass`, whereas Hashtable\<Int32, String> would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="0ade2-126">Les types non génériques sont représentés par les deux `ICorDebugClass` et `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="0ade2-126">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="0ade2-127">Cette dernière interface a été introduite dans le .NET Framework version 2.0 pour gérer l’instanciation de type.</span><span class="sxs-lookup"><span data-stu-id="0ade2-127">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0ade2-128">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="0ade2-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ade2-129">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0ade2-129">Requirements</span></span>  
 <span data-ttu-id="0ade2-130">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ade2-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ade2-131">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0ade2-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ade2-132">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ade2-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ade2-133">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ade2-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ade2-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ade2-134">See Also</span></span>  
 [<span data-ttu-id="0ade2-135">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="0ade2-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
