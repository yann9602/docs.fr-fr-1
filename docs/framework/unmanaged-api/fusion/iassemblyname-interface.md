---
title: IAssemblyName, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyName
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyName
helpviewer_keywords: IAssemblyName interface [.NET Framework fusion]
ms.assetid: f7f8e605-6b67-4151-936f-f04ecd671d90
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1d11889ab9db408b6e703bbaec17fd0487f142a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iassemblyname-interface"></a><span data-ttu-id="45d06-102">IAssemblyName, interface</span><span class="sxs-lookup"><span data-stu-id="45d06-102">IAssemblyName Interface</span></span>
<span data-ttu-id="45d06-103">Fournit des méthodes pour décrire et travailler avec l’identité unique d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="45d06-103">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="45d06-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="45d06-104">Methods</span></span>  
  
|<span data-ttu-id="45d06-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="45d06-105">Method</span></span>|<span data-ttu-id="45d06-106">Description</span><span class="sxs-lookup"><span data-stu-id="45d06-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="45d06-107">Clone (méthode)</span><span class="sxs-lookup"><span data-stu-id="45d06-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-clone-method.md)|<span data-ttu-id="45d06-108">Crée une copie superficielle de cet `IAssemblyName` objet.</span><span class="sxs-lookup"><span data-stu-id="45d06-108">Creates a shallow copy of this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="45d06-109">Finalize (méthode)</span><span class="sxs-lookup"><span data-stu-id="45d06-109">Finalize Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-finalize-method.md)|<span data-ttu-id="45d06-110">Cela permet de `IAssemblyName` objet pour libérer des ressources et effectuer d’autres opérations de nettoyage avant que son destructeur est appelé.</span><span class="sxs-lookup"><span data-stu-id="45d06-110">Allows this `IAssemblyName` object to release resources and perform other cleanup operations before its destructor is called.</span></span>|  
|[<span data-ttu-id="45d06-111">GetDisplayName (méthode)</span><span class="sxs-lookup"><span data-stu-id="45d06-111">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md)|<span data-ttu-id="45d06-112">Obtient le nom explicite de l’assembly référencé par ce `IAssemblyName` objet.</span><span class="sxs-lookup"><span data-stu-id="45d06-112">Gets the human-readable name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="45d06-113">GetName (méthode)</span><span class="sxs-lookup"><span data-stu-id="45d06-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getname-method.md)|<span data-ttu-id="45d06-114">Obtient le nom simple, non chiffré de l’assembly référencé par ce `IAssemblyName` objet.</span><span class="sxs-lookup"><span data-stu-id="45d06-114">Gets the simple, unencrypted name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="45d06-115">GetProperty (méthode)</span><span class="sxs-lookup"><span data-stu-id="45d06-115">GetProperty Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getproperty-method.md)|<span data-ttu-id="45d06-116">Obtient un pointeur vers la propriété référencée par le `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="45d06-116">Gets a pointer to the property referenced by the specified `PropertyId`.</span></span>|  
|[<span data-ttu-id="45d06-117">GetVersion (méthode)</span><span class="sxs-lookup"><span data-stu-id="45d06-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getversion-method.md)|<span data-ttu-id="45d06-118">Obtient les informations de version pour l’assembly référencé par ce `IAssemblyName` objet.</span><span class="sxs-lookup"><span data-stu-id="45d06-118">Gets the version information for the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="45d06-119">IsEqual (méthode)</span><span class="sxs-lookup"><span data-stu-id="45d06-119">IsEqual Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-isequal-method.md)|<span data-ttu-id="45d06-120">Détermine si un `IAssemblyName` objet est égal à cette `IAssemblyName`, basé sur les indicateurs de comparaison spécifié.</span><span class="sxs-lookup"><span data-stu-id="45d06-120">Determines whether a specified `IAssemblyName` object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>|  
|[<span data-ttu-id="45d06-121">SetProperty (méthode)</span><span class="sxs-lookup"><span data-stu-id="45d06-121">SetProperty Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-setproperty-method.md)|<span data-ttu-id="45d06-122">Définit la valeur de la propriété référencée par le `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="45d06-122">Sets the value of the property referenced by the specified `PropertyId`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="45d06-123">Spécifications</span><span class="sxs-lookup"><span data-stu-id="45d06-123">Requirements</span></span>  
 <span data-ttu-id="45d06-124">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45d06-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45d06-125">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="45d06-125">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="45d06-126">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45d06-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45d06-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45d06-127">See Also</span></span>  
 [<span data-ttu-id="45d06-128">Interfaces de fusion</span><span class="sxs-lookup"><span data-stu-id="45d06-128">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="45d06-129">IAssemblyEnum (Interface)</span><span class="sxs-lookup"><span data-stu-id="45d06-129">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
